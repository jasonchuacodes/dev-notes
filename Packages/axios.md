
This creates a request/response interceptor in order to check if the response is successful. 
Else, if it receives an unauthorized error (403 or 401), then the user is redirected back to the login page.

Here, we set up an `AxiosInterceptor` component so that we are able to handle unauthorized requests (i.e. requests with expired JWT token). The user is redirected to `/login` page if an unauthorized error is received.

Page redirect to `/login` could also be accomplished by using `window.location.href = '/login'`. However, by doing this approach, we would lose the capability to save the location `from` state which is needed to redirect the user back to the page he previously visited once he is logged back in.


```js
// api/axiosInstance.ts
import axios from 'axios'
import Cookies from 'universal-cookie'
import { ReactNode, useEffect, useState } from 'react'
import { useLocation, useNavigate } from 'react-router-dom'
import toast from 'react-hot-toast'

const cookies = new Cookies()

const instance = axios.create({
    baseURL: process.env.REACT_APP_API_URL,
    headers: {
        'Content-Type': 'application/json',
        Accept: 'application/json',
    },
})

const AxiosInterceptor = ({ children }: { children: ReactNode }) => {
    const navigate = useNavigate()
    const { pathname } = useLocation()

    const [isSet, setIsSet] = useState(false)

    useEffect(() => {
        setIsSet(true)
        
        const responseInterceptor = (response: any) => {
            const accessToken = cookies.get('token')

            if (accessToken) {
                instance.defaults.headers.common['Authorization'] =
                    `Bearer ${accessToken}`
            }

            return response
        }

        const errorInterceptor = (error: any) => {
            if (
                (error.response.status === 401 ||
                    error.response.status === 403) &&
                pathname !== '/login'
            ) {
                cookies.remove('token')
                toast.error('Authentication failed. Please login.')
                navigate('/login', { state: { from: pathname }, replace: true })
            }

            return Promise.reject(error)
        }

        const interceptor = instance.interceptors.response.use(
            responseInterceptor,
            errorInterceptor,
        )

        return () => instance.interceptors.response.eject(interceptor)
    }, [pathname, navigate])

    return isSet && children // check if isSet is true and then return children
}

const setBearerToken = (token: string) => {
    instance.defaults.headers.common['Authorization'] = `Bearer ${token}`
}

export default instance
export { AxiosInterceptor, setBearerToken }
```

We need to wrap the entire app with the `AxiosInterceptor` component.
```js
// App.tsx
function App() {
    return (
        <BrowserRouter>
            <AxiosInterceptor>
                <Layout>
                    <AppRoutes />
                </Layout>
            </AxiosInterceptor>
        </BrowserRouter>
    )
}

export default App
```


###### Additional notes:
`useEffect` is asynchronous to children's effect, so request call might be at the same time with interceptor setup and even sooner, in that case the interceptor might not work as we expected.

So the solution is set a state as `false` initially, and set it to true after interceptor setup complete, then we return the `children`