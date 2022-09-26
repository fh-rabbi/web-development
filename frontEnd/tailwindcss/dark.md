## Darkmode feature:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  darkMode: "class", // class or media
  theme: {
    extend: {},
  },
  plugins: [],
}
```

* **Media for device default mode**
* **Class for manually add dark mode**

* For class required add `dark` class in the `html` tag

