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




