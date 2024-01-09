####  pushState()

using the `pushState` method, we are able to update the site URL while opting out of the navigation.

```
history.pushState(state, unused, url)
```

Note:
this change will not be detected by useRouter. Hence, if you'd like to listen for this change, you must dispatch an event and listen for it.
