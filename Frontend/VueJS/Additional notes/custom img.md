For Vue3 components with an image tag where we need the `src` attribute to be dynamic, we can assign a placeholder to it in case the link is invalid.

Here's how we can do that:
```html
<img :src="customUrl" @error="replaceByDefault" />
```

```js
import placeholderImage from 'path/to/placholder-image.png'

const replaceByDefault = (e: Event) => {
  (e.target as HTMLImageElement).src = placeholderImage;
};
```