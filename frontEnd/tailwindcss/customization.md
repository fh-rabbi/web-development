## Customization:

```js
module.exports = {
  mode: 'jit',
  content: ["index.html"],
  theme: {
    extend: {
      // Customization
      colors:{
        fr: 'red',
        test:{
          400: 'seagreen',
          600: 'orange',
          800: 'lime'
        }
      },
      spacing: {
        large: '50px',
      }
      // Customization
    },
  },
  plugins: [],
};

```
