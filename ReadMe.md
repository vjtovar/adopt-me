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

Effects
useEffect: to call out to API or stateful things that live outside of component
useEffect function called outside of render. Wait for something to happen first. Finish render function first then call on Effect function to fetch API and then call setPets. requestPets will call whenever call on dependant variables. If put nothing into array will call it just once. If don't put empty array it will call everything each time it renders. Use function to fetch API. await just says wait until the promise resolves. Assign key bc react knows which is which can render one rather than everything. Key: set to pet id bc better indentifier in db.

useState Q&A
pets is like a bit of state and setPets is a state updater. Destructuring. useState empty string is the initial state 

Custom Hooks
local Cache: so that it doesn't go back to API and reload it, when go back to breed it just gets local.
async function want setBreedList empty array, so don't mix up breeds, ex: dog, with cat breed.
Set dependancy of animal, so when animal changes request it.

Custom Hooks Q&A
Allows you schedule something to run later. Everytime animal changes in the future it knows to run custom function over again.

Handling User Input
Want user to request data from api. In form in SearchParams add onSubmit, need to add e.preventDefault so it doesn't submit the form back to it self, if you click submit and it refreshes then that is what it is doing.

Component Composition
Added Results.js. ?: is a terniary, can do terinarys but can't do if statements. The : is the otherwise.

Styling the Pet Component
add hero image and destructure props

Building for Production
$npx parcel build src/index.html
$npx serve dist
Do this when ready for production

Strict Mode
Will add additional checks so that your app is future proof and is compatiable with updated versions of react. In App.js add import for strictmode and add strictmode tags. Made it a component so can check certain parts of app

React Dev Tools
react extension tools, add to chrome

React Router
create Details.js file
$npm i react-router-dom@6.2.1: installs router
BrowserRouter: says everything in it is handled by a router
path: what path in browser, :id is a variable
element: whatever you want to render when route is matched, put it in component call

React Router Link
In pet.js add link import and change a tags to Link tags. Will handle things better with router
Every time use link tag it has to be inside a browserRouter tag
useParams works with router, will pull id off of useParams

BrowserRouter vs HashRouter and Q&A
HashRouter allows you to have a router that never leaves one page.
BrowserRouter have to make sure all routes go to the same index.html page. This one is better! 

Class Components
Can use anything with the word use, so need a constructor:run this functions when a new instance of Details is created and super: give this to my parent class, which is the parent of Details, which is component. create initial state. this is how we manage state and props.  

Fetching Data in componentDidMount
It is a lifecycle method, it will run once and show loading...then later will run function.
setState so updates the state
Need to use useParams to get params out of react router. Need to wrap it in another component. This is how you use hooks with class component

Class Properties
$npm i -D @babel/plugin-proposal-class-properties@7.16.7: this adds babel plugin
create .babelrc file
babel does jsx transformation
Don't have to use constructor or super anymore, by setting a class property on details for loading true. 
defaultProps: is all carousels share one default prop

Managing State in Class Components
Add Carousel.js, add carousel for animal pics
Add import of carousel to details page
If have parcel issues delete parcel and dist files and run it again
$ rm -rf .parcel-cache dist
$npm run dev

Handle Events in Class Components
Datatype index is a number, but in DOM is a string. This is a problem bc in src have images looking for the active index, but it will try to grab a string. To fix put a + (a unary plus) in front of event, so will read as a number.

Error Boundaries
Wrap untrusted components with error boundary, so errors don't go past that.
These have to be class components, errot classes can't be function components. Where ever the error boundary is placed has to be outside of where you think the error might happen.
componentDidUpdate will render everytime state or props updated
Navigate is a redirect

Error Boundaries Q&A
componentDidUpdate is like useEffect except it doesn't run at start and only cares about it's own component state

Context
Context is like state, but instead of being confined to a component, it's global to your application. It's application-level state. 
It helps you keep state in whole app. If want to pass theme don't have to do it in each component. Just set it once in App.js and then components can read from it.
createContext is a function that returns an object with two React components in it: a Provider and a Consumer. A Provider is how you scope where a context goes. A context will only be available inside of the Provider. You only need to do this once. A Consumer is how you consume from the above provider. A Consumer accepts a function as a child and gives it the context which you can use. We won't be using the Consumer directly: a function called useContext will do that for us.

Context for Theming
Make ThemeContext.js file add function
import theme  and useState in app.js and make hook. Add theme context tags
Searchparams and Details import theme and update code

Context & State
Make it settiable in SearchParams add label with onchange and onblur

Portals & useRef for Modals
Add modal in index.html. useRef to make sure you get the same thing across all renders. el=element.
elRef only lets you modify current

Removing Modals Q&A
toggleModal: if false make it true and vice versa
In Details.js add showModal and if true display and if no then null

Wrapping Up
Try to use API from Petfinder
Try to deploy