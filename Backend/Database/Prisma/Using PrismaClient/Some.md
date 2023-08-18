`some` - is a filtering field used for filtering data based on the condition set
```js
  const users = await prisma.user.findMany({
    where: {
      email: {
        endsWith: "prisma.io"
      },
      posts: {
        some: {
          published: false
        }
      }
    },
  }
```

	the data returned here would be of users with email ending with prisma.io and has atleast one post (some) that is not published.