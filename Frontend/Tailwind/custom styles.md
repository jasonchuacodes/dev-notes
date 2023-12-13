It is possible to define a custom font weight and apply it to your custom font size in the Tailwind CSS configuration file (`tailwind.config.js`).
Here's how you can do it:

```js
module.exports = {
  theme: {
    extend: {
      fontWeight: {
        regular: '500', 
        semibold: '600',
      },
      fontSize: {
        'lg-r': ['40px', { fontWeight: regular }], 
	    'lg-sb': ['40px', { fontWeight: semibold }],
	  }
    },
  },
};

```