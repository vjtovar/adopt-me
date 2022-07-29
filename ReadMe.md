Setup
create directory src
create file index.html- html:5 html document, emmit built into vs code

Vanilla React Setup
unpkg - load from mpn via
reactdom - renders to dom
go to finder open folder, open html file, drag to browser


App component
React.createElement - creates a new instance of something
document.getElementById - where do you want to put it

Components
src = "./App.js" needs to be on the bottom of index.html
App is the parent component of Pet bc it renders pet. Data from the parent to the child via props

npm
node package manager
$ npm init -y - track dependencies and give latest version, gives package.json

Prettier
$ npx prettier src/App.js - will print indented code in terminal
$ npx prettier src/App.js --write - will indent code in vs code
create file .prettierrc, in file put empty object - tells ppl formatted by prettier
find prettier extension and do cmd , to open settings then do save on f to save formatting when vs code saves
require config prettier - prettier wont run unless there is a prettier rc in project
Package.json > scripts, add prettier string. If using open source, have to make it available fo ppl not using vs code prettier. adding prettier in npm scripts is referencing prettier in .bin. Now is portable on windows or mac.
$  npm install -D prettier - capital D bc want it to be devDependency not regular dependancy. devDependancies get installed when working on project and dependencies get installed when going out to production
$ npm run format - runs prettier

ESLint
Makes sure code correct
$ npm install -D eslint@8.8.0 eslint-config-prettier@8.3.0
^ gives latest path
create new file in root of directory .eslintrc.json
In the extends array prettier must come last - shuts off other configs
eslint:recommended - solid rules, ex: no variables without assignment
plugins: extends what ESLint can do and read
parserOptions: what versions
env: environment - es6 allows for things like @import
browser: allow things like fetch, doc, window
node: allow things like process
$ npx eslint src/App.js - 'React' not defined
download eslint extension
put lint into scripts in package.json, --quiet: keeps it to the bare minimum of whats broken
$ npx prettier --help: gives command options 
In package.json scripts --check: checks if someone ran prettier
$ npm run lint -- --fix: the extra -- passes it to eslint instead of npm, can do --debug for more info, or you can check

Git
$git init: history of where code went, tracks source code
$ls -lsah: can see have git directory 
Create a file .gitignore in root and place things we need to ingnore 
.DS_Store: saves icon position

Parcel - bundler
Saves you time, knows how to compile based on file type
$ npm i -D parcel
In package.json add script for parcel
$ npm run dev: adds a .parcel-cache and dist directory. If not working delete directories and run command again. Now server is working http://localhost:1234
$ npm install react@17.0.2 react-dom@17.0.2: This will pull React and ReactDOM down from npm and put it in your node_modules directory. Now instead of loading them from unpkg, we can tell Parcel to include them in your main bundle. 
In index.html: Delete the two unpkg script tags. Add type="module" to App.js script tag. This is how parcel know the latest version of JS.
Create a new file called Pet.js in src directory and place function for pets
In App.js add imports and remove Pet component

Browserslist
In package.json add browserslist. last 2 Chrome versions is only 15% of population

Component Module
Change Pet.js to have props 
Capital first letter for components

JSX
can remove import react from Pet.js, still there bc of tools
Refactor App.js and Pet.js to JSX
JSX imports react for you
.jsx naming file is pointless. Can name .js if want to

Configure ESLint w/ JSX
$npm install -D eslint-plugin-import@2.25.4 eslint-plugin-jsx-a11y@6.5.1 eslint-plugin-react@7.28.0
In .eslintrc.json update extends with plugins, the react one so it knows what react is doing, import allows logic around imports, and jsx-ally will chack if you are putting alt text on img or buttons on links.
Disable two rules: prop-types(does validations) and jsx-scope(don't have to import react in jsx files). 0 means off. Add settings and tell to look for version of react
To run do $npm run lint

Search Form Component
hooks add statefullness to UI
Create file SearchParams.js in src and add function. In App.js remove pet import and add import for SearchParams, add component call for SearchParams

useState Hook
Everytime you see the word use it is a hook
do destructuring for location and setlocation
Make onChange handler in input tag, when change event happens will call onChange function and will pull out target.value. target is input, value of input, then call setlocation which will update the state. Then render with new state.
useState depends on the order it is called, so if have 5 hooks, then need to call them in same order. Do not have conditional hooks bc have variable amount of hooks being called. No hooks in if statements or loops
A controlled form has onChange function in input, this is a bad idea. An uncontrolled form is when you put something like onSubmit in form tag the input tag is no longer controlled and will pull everything out of form and submit it.

Mapping Data to Component
$npm install -D eslint-plugin-react-hooks@4.3.0
In .eslintrc.json add a plugin for hooks: validates rule of hooks(don't put hooks in if statements)
ANIMALS is in screaming case bc it is a constant. Do onChange for select tag in animal. Do onBlur function so we make sure it always captures event. Same logic as onChange. Map over ANIMAL array to take the list of strings and transform it to a list of react component. Using implicit return bc can put on one line.
Do the same for breed









