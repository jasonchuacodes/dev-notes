#### Installation
series of steps. see documentation here [tailwind docs](https://tailwindcss.com/docs/installation)


#### Purpose
For easily adding styles to elements via the class attribute

#### Techniques
You can *override the default theme* and add styles in the tailwind.config file by overriding an option in the default theme.
```js
module.exports = {
	theme: {
		opacity: { 
		'0': '0', 
		'20': '0.2', 
		'40': '0.4', 
		'60': '0.6', 
		'80': '0.8', 
		'100': '1', 
		} 
	} 
}
```

If you'd like to keep the default theme and add more styles, you can *extend* it instead.
```js
module.exports = {
	theme: {
		opacity: { 
		'0': '0', 
		'20': '0.2', 
		'40': '0.4', 
		'60': '0.6', 
		'80': '0.8', 
		'100': '1', 
		},
		extend: {
			fontSize: {
				'usm': '8px', //ultra-small
			}
		}
	} 
}
```

You can *reference* a value in your theme. You can do so by providing a closure instead of a static value. For example, if we have a 'lineHeight' already defined in the theme, we can reference its value for another key like 'fontSize'. 
like this: 
```js
theme: {
    lineHeight: {
      none: '1',
      tight: '1.2',
      normal: '1.5',
      auto: 'auto',
    },
    fontSize: ({ theme }) => ({
      body: ['14px'],
      small: ['10.5px'],
      h1: [
        '35px',
        {
          lineHeight: theme('lineHeight.normal'),
        },
      ],
      h2: [
        '28px',
        {
          lineHeight: theme('lineHeight.normal'),
        },
      ],
```