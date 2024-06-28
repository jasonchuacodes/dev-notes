in order to use the useContext hook in React, we have to create the context first.

```js
// > context/AuthProvider.tsx

import { ReactNode, createContext, useState } from 'react'

type Auth = {
    token: string | null
}

type AuthContextType = {
    auth: Auth | null
    setAuth: (newvalue: Auth) => void
}

const initialState = {
    auth: {
        token: null,
    },
    setAuth: () => {},
}

// Here, we are creating the context with createContext()
const AuthContext = createContext<AuthContextType>(initialState)

// Next, we are setting the AuthProvider - which is basically a wrapper for the entire application which needs access to the state
const AuthProvider = ({ children }: { children?: ReactNode }) => {

// We then set the auth state here
    const [auth, setAuth] = useState<Auth>({ token: null })

    return (
        <AuthContext.Provider value={{ auth, setAuth }}>
            {children}
        </AuthContext.Provider>
    )
}

export { AuthContext, AuthProvider }
```

Note: It is not really necessary to create the provider. It's just a wrapper for the child components which we will make use of the context values.

```js
// > index.tsx 
const root = ReactDOM.createRoot(document.getElementById('root') as HTMLElement)
root.render(
    <React.StrictMode>
	    // Here, we are wrapping the entire application with the AuthProvider since we need the auth state in the entirety of our application. For other contexts, wrap the provider only to the componetns that need it.
        <AuthProvider> 
            <App />
        </AuthProvider>
    </React.StrictMode>,
)
```

---
We can now use the context where we want it.
```js
// > dashboard
const authContext = useContext(AuthContext)

console.log(authContext.auth.token) // token value
```

Optionally, we can also create a useAuth hook so that we can access the values directly from our context.
```js
// > hooks/useAuth.ts
const useAuth = () => {
    return useContext(AuthContext)
}

export default useAuth
```


```js
const { auth } = useAuth()

console.log(auth.token) // token value
```