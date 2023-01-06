Run this command:
```sh
npx create-next-app@latest -e with-tailwindcss # folder name
```

Create `app` directory:
```sh
mkdir app
```

I recommend to read the [[upgrade-guide]] or check this [link](https://beta.nextjs.org/docs/upgrade-guide) for more tips and tricks.

Enable the new `app` directory in `next.config.js`:
```js
/** @type {import('next').NextConfig} **/
module.exports = {
	reactStrictMode: true,
	experimental: {
		appDir: true,
	},
};
```

If you are using **tailwindcss** follow this guide `tailwind.config.js` if not, you can skip this guide:
```js
/** @type {import('tailwindcss').Config} **/
module.exports = {
	content: [
		'./app/**/*.{js,ts,jsx,tsx}',
		'./components/**/*.{js,ts,jsx,tsx}',
		'./pages/**/*.{js,ts,jsx,tsx}',
	],
	theme: {
		extend: {},
	},
	plugins: [],
}
```

**File Conventions**
- Layout
- Page
- Loading
- Error
- Template
- Head
- Not Found

You can check this information on this [page](https://beta.nextjs.org/docs/api-reference/file-conventions/layout).

> Note: You can now use the `app` directory and do not forget to use `page.tsx` as your Home Page.

*/app/page.tsx*
```tsx
import React from 'react';

function Home() {
	return(
		<div>Hello World</div>
	)
}

export default Home;
```

> Note: If this do not work, please delete the index.tsx in `pages` directory. It should be deleted so it will render the `app` directory not the `pages` directory.

After deleting the `index.tsx` the *app* directory will create a `layout.tsx` file.

> To use the tailwindcss please remove the `import '../styles/globals.css'` located at `/pages/_app.tsx` and paste it in the `layout.tsx`.