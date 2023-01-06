# Getting Started
Tailwind CSS works by scanning all of your HTML files, JavaScript components, and any other templates for class names, generating the corresponding styles and then writing them to a static CSS file.

It's fast, flexible, and reliable -- with zero-runtime.

## Installation (TailwindCLI)
The simplest and fastest way to get up and running with Tailwind CSS from scratch is with the Tailwind CLI tool. The CLI is also available as a [standalone executable](https://tailwindcss.com/blog/standalone-cli) if you want ot use it without installing Node.js.

1. Install Tailwind CSS
Install `tailwindcss` via npm, and create your `tailwind.config.js` file.

```shell
yarn init -y
yarn add -D tailwindcss postcss-cli autoprefixer
yarn tailwindcss init
```

2. Configure your template paths
Add the paths to all of your template files in your `tailwind.config.js` file.

```javascript
/** @type {import('tailwindcss').Config} **/
module.exports = {
	content: ["./app/*"],
	theme: {
		extend: {},
	},
	plugins: [
		require("tailwindcss"),
		require("autoprefixer")
	],
}
```

3. Add the Tailwind directives to your CSS
Add the `@tailwind` directives for each of Tailwind's layers to your main CSS file which is to be created and name it to *tailwind.css*.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

4. Configure your package.json
We have completed the creation of our CSS file. It is now time to write a simple script to process this CSS through our PostCSS plugin lists.
- The first step, open *package.json* file
- The second step, add the build script with the commands below (above the repo):
```json
"scripts": {
	"build": "yarn tailwindcss -i tailwind.css -o ./styles/styles.css"
},
```
- A brief illustration of the script.
![](https://aviyel.com/cdn-cgi/image/format=auto/assets/uploads/files/1634119499823-image-resized.png)

Now, type the following command in the terminal to actually start the build script.
```sh
yarn run build
```

5. Start using Tailwind in your HTML
Add your compiled CSS file to the `<head>` and start using Tailwind's utility classes to style your content.

```html
<!doctype html>
<html>
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<link href="/dist/output.css" rel="stylesheet">
</head>
<body>
	<h1 class="text-3xl font-bold underline">
		Hello World
	</h1>
</body>
</html>
```

## Install Tailwind CSS with Next.js

The quickest way to start using Tailwind CSS in your Next.js project is to use the [Next.js + Tailwind CSS Example](https://github.com/vercel/next.js/tree/c3e5caf1109a2eb42801de23fc78e42a08e5da6e/examples/with-tailwindcss). This will automatically configure your Tailwind  setup based on the official Next.js exampl. If you'd like to configure Tailwind manually, continue with the rest of this guide.

1. Create your project
Start by creating a new Next.js project if you don't have one set up already. The most common approach is to use [Create Next App](https://nextjs.org/docs/api-reference/create-next-app).

```shell
npx create-next-app my-project
cd my-project
```

2. Install Tailwind CSS
Install `tailwindcss` and its peer dependencies via npm, and then run the init command to generate both `tailwind.config.js` and `postcss.config.js`.

```shell
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

3. Configure your template paths
Add the paths to all of your template files in your `tailwind.config.js` file.

```javascript
/** @type {import('tailwind').Config} **/
module.exports = {
	content: [
		"./pages/**/*.{js,ts,jsx,tsx}",
		"./components/**/*.{js,ts,jsx,tsx}",
	],
	theme: {
		extend: {},
	},
	plugins: [],
}
```

4. Add the Tailwind directives to your CSS
Add the `@tailwind` directives for each of Tailwind's layers to your `./styles/globals.css` file.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

5. Start your build process
Run your build process with `npm run dev`.

```shell
npm run dev
```

6. Start using Tailwind in your project
Start using Tailwind's utility classes to style your content.

```javascript
export default function Home() {
  return (
    <h1 className="text-3xl font-bold underline">
      Hello world!
    </h1>
  )
}
```