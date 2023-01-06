# 👍 Tailwind CSS CDN

Adding the Tailwind CSS in an HTML project via the CDN is easier and very beginner friendly. This method allows you to use the Tailwind CSS framework without the need to worry about PostCSS configurations. It is a great way to jumpstart your project. However with these perks come some limitations, some of these limitations are:

- You cannot install third-party plugins
- You cannot customize Tailwind's default theme.
- You get access to all the files even the files you do not need.
- You cannot use any directives like _@apply_, or _@variants_.
- You cannot enable additional variants like _group-focus_.

To use the Tailwind CSS in an HTML project via the CDN add this to the _head_ section of your HTML project.

```html
<link
  href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.CSS"
  rel=" stylesheet"
/>
```

# 📦 Tailwind CSS using the Package Manager

Now, I would suggest if you are building a world application, it would be to install your tailwind CSS using the package manager. This is because most frameworks make use of PostCSS already, like the auto picker.

In this part of the Tailwind CSS tutorial, we are going to look at how to install Tailwind CSS in HTML using the package manger.

## Steps in installing tailwind CSS

- [[#Create your package.json file]]
- [[#Install Tailwind CSS]]
- [[#Adding tailwind CSS directives to a CSS file]]
- [[#Setting up the Tailwind configuration file]]

### Create your package.json file

A **package.json** file is a file that lives in the root directory of our project. It holds important information about your project like the project's name, the projects, description, dependencies required by the project.

Run the following command:

```sh
yarn init -y
```

### Install Tailwind CSS

Next, we install the Tailwind CSS in the HTML project along with the latest PostCSS and autoprefixer using the command below:

```sh
yarn add -D tailwindcss@latest postcss@latest autoprefixer@latest
```

### Adding tailwind CSS directives to a CSS file

The next step in adding tailwind CSS in an HTML project is to create a file called _globals.css_ in the root folder of your application and write the following code to give your application the tailwind CSS utilities.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Setting up the Tailwind configuration file

Setting up your Tailwind CSS configuration is an important step in adding Tailwind CSS to an HTML project.

The chances are that you would want to use your configuration when building your application. The configuration file makes it easy to customize the classes in Tailwind CSS by changing any fonts, color, spacing, etc.

To override the default classes when using Tailwind, run the following command in your terminal to create a _tailwind.config.js_ file.

```sh
yarn tailwindcss init
```

In the new config file, you can go ahead to configure them by writing the following code on them:

```js
module.exports = {
  purge: [],
  darkmode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {},
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};
```

Now, you can go ahead to run the following command on your terminal.

```sh
next tailwind CSS build style.css -o output.css
```

This will generate a new CSS file called _output.css_. We then include this _output.css_ file in our HTML file, the same way we include a normal CSS file by adding this line of code

```html
<link href="./output.CSS" ref="stylesheet" />
```

With that, you can now use Tailwind CSS in the HTML project. You can go ahead to build your application.
