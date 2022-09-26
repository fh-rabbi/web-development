<h2 align="">Tailwind CLI Install</h2>


### Install & Initialize: 

```
npm install -D tailwindcss
npx tailwindcss init
npm init -y
```
### Modify `tailwind.config.js`:

```js
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### Modify `package.json`:

```json
{
  "name": "test",
  "version": "1.0.0",
  "description": "",
  "main": "tailwind.config.js",
  "scripts": {
    "build": "npx tailwindcss -i ./src/input.css -o ./src/output.css --watch"
  },
  "author": "",
  "license": "ISC"
}
```

### Create Folder & Files:

1. ```mkdir src```

2. ```cd src ```

3. ```touch index.html input.css```

4. **in root dir** > ```npm run build```

---

<h2 align="">Tailwind PostCSS Install</h2>

`npm i postcss postcss-cli autoprefixer`

`npx tailwindcss init -p`

[+] **Modify** `package.json`:

```json
"scripts": {
    "build": "npx tailwindcss -i ./src/input.css -o ./src/output.css --watch",
    "build-p": "npx postcss ./src/input.css -o ./src/output.css --watch"
  },
```

> `npm run build-p` 
