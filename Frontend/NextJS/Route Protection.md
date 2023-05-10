`Route protection` is a way of guarding _private routes_ so that only authorized users (with access_tokens) are allowed to visit the route or page.

Setting up route protection in NextJS is convenient with `getServerSideProps`.

Here’s an example on how this is done.
```javascript
// create the `utils` folder and add the file `getServerSideProps`
// insude getServerSideProps add the code below to check for authUser credentials

export const UserSignInOutAuthCheck = async ({ req }: any) => {
	// get the request cookies directly upon logging in. 
	// This is different from js-cookies
	const token = req?.cookies["token"];

  // get the current url path 
	const path = req?.url;


	// define all the privateRoutes and publicRoutes
	const privateRoutes = [
		path.includes("welcome"),
		path.includes("pre-question"),
		path.includes("main-question"),
		path.includes("recommendations"),
		path.includes("checklist"),
	];
	
	const publicRoutes = [
		path.includes("login"), 
		path.includes("register")
	];


	// from here, define the route-protection by checking if authToken is available
  if (publicRoutes.includes(true) && !token) return { props: {} };

  if (!token) {
    return {
			redirect: {
        destination: "/",
        permanent: false,
      },
    };
  }

  if (privateRoutes.includes(true) && !token) {
    return {
      redirect: {
        destination: "/",
        permanent: false,
      },
    };
  }

  if (publicRoutes.includes(true) && token) {
    return {
      redirect: {
        destination: "/welcome",
        permanent: false,
      },
    };
  }

  return {
    props: {},
  };
};
```

After setting the getServerSideProps, add the following to the components or pages that need the routeProtection.
```javascript
// loginPage | dashboardPage | profilePage | etc
const LoginPage = () => {
...
...
...
}

// add this in to set the authChecker for route protection
export { UserSignInOutAuthCheck as getServerSideProps } from "~/utils/getServerSideProps";
export default LoginPage;
```