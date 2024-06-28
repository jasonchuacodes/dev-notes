#### Authentication
- user logs in with credentials thru `auht/login` endpoint
	-> receives token
- save token to cookies
- set axios instance bearer token - `setBearerToken()`
- save the token in memory as auth state `{token: token}`
- redirect user to `/company` page


#### Issues:
- onPageRefresh state is lost

#### Solution:
- if cookies has token, `setBearerToken()`
- set the auth state token (?)

- alt solution: 
  - private pages require to fetch user/data, if responst status is unauthorized `401 | 403`, navigate to `/login` page