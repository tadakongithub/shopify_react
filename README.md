# shopify_react
How to add react to shopify theme

# how to make this template

1. Make a folder with an arbitrary name

   > mkdir react-shopify

2. create package.json

   > npm init -y

3. install react and react-dom

   > npm i react react-dom

4. install @babel/core, @babel/preset-env, @babel/preset-react, webpack, webpack-cli, babel-loader

   > npm i @babel/core @babel/preset-env @babel/preset-react webpack webpack-cli babel-loader --save-dev

   * webpack-cli is used to run webpack on the command line
   * babel-loader allows transpiling JavaScript files using Babel and webpack.

5. create webpack.config.js in the project root

- we can specify the entry point. An entry point is where all the bundling starts from.
- we can specify the path and file name of the bundled js file.
- The Path module provides a way of working with directories and file paths.
- path.resolve combines arguments to make an absolute path.
- \_\_dirname gives us the absolute path of the current directory.
- the name of the folder does not matter, but by convention 'dist' for 'distribution' is often used. Shopify uses 'assets' for the name of the folder that contains js files, css files and other static assets.
- we can define how to bundle modules in module property. We want to use babel loader for js files because babel transpile modern javascript syntax and jsx into es5.
- mode production. In production mode, our bundles are gonnabe minified

6. create .babelrc

- @babel/preset-env is used to transpile es6+ into es5
- @babel/preset-react is used to transpile jsx into es5

7. create react app

8. bundle modules to create static assets

   > webpack --mode production

9. upload bundle js into assets folder of your shopify theme.　 I used online code editor on my store.

- go to your store's admin page
- click 'Online Store'
- click 'Themes'
- click 'Actions' dropdown of your theme and click 'Edit code'
- go to Assets folder, click Add a new asset
- choose your bundle js you just created, and hit 'Upload assets'

10. Add script tag in theme.liquid file to include the bundle js you just uploaded

- go to Layout folder, click theme.liquid
- right before closing body tag, add this script.
  > \<script defer type="module" src="{{ "bundle.js" | asset_url }}"></script>
