# Default app
## Initial code
- Download started code
- npm i
## Run app
- ng serve
- npm start
## Project structure
```
/app_name/src:
    - index.html: is app's top level html template
    - styles.css: is app's top level style sheet
    - main.ts: is where app starts running
/app_name/src/app:
    -app.ts: contains app-root, the top level angular component in app. 
        - component: a component is made up of:
            - component's code
            - html template
            - styles
        - The above parts of a component can be on separate files.
    - app.css: is the stylesheet for the component
    - new components go in this directory
/app_name/src/assets:
    - contains imgs used by app
/app_name: 
    - .angular: required to build app
    - .e2e: used to test app
    - .node_modules: node.js packages used by app
    - angular.json: describes angular app to aooo building tools
    - package.json: used by npm to run app
    - tsconfig.*: describe app's config to ts compiler
```
## First component
- app_name/src/index.html: Update title
```
    <title> Homes </title>
```
- app_name/src/app/app.ts: Update template and class
```js
import {Component} from '@angular/core';
@Component({
  selector: 'app-root',
  imports: [],
  template: `
    <h1>Hello world!</h1>
  `,
  styleUrls: ['./app.css'],
})
export class App {
  title = 'homes';
}
``` 
## Create Home component
- Angular components are the building blocks of angular app. 
- Angular component is made up of: 
    - code
    - html layout
    - css style
- Angular components have metadata that define its properties:
    - selector: How Angular regers to the component in templates
    - standalone: Whether component requires NgModule
    - imports: Describes component's dependencies
    - template: Describe component's html and layout
    - styleUrls: List URLs of css files used by component
### Create the Home component
- Navigate to root dir of app_name
- ng generate component component_name
### Add component to app's root component/App
- app_name/src/app.ts: update app component to include home
- First import the Home component
- Then Home component can be used in template of App component
```javascript
import {Component} from '@angular/core';
import {Home} from './home/home';
@Component({
  selector: 'app-root',
  imports: [Home],
  template: `
    <main>
      <header class="brand-name">
        <img class="brand-logo" src="/assets/logo.svg" alt="logo" aria-hidden="true" />
      </header>
      <section class="content">
        <app-home></app-home>
      </section>
    </main>
  `,
  styleUrls: ['./app.css'],
})
export class App {
  title = 'homes';
}
```
- Now, the root component displays the newly created Home component
### Coding the Home component
- app_name/src/app/home/home.ts:
- Defines a Home component with a non-functional search button
```javascript
import {Component} from '@angular/core';
@Component({
  selector: 'app-home',
  template: `
    <section>
      <form>
        <input type="text" placeholder="Filter by city" />
        <button class="primary" type="button">Search</button>
      </form>
    </section>
  `,
  styleUrls: ['./home.css'],
})
export class Home {}
```
### Stying the Home component
- app_name/src/app/home/home.css
```javascript
.results {
  display: grid;
  column-gap: 14px;
  row-gap: 14px;
  grid-template-columns: repeat(auto-fill, minmax(400px, 400px));
  margin-top: 50px;
  justify-content: space-around;
}
input[type="text"] {
  border: solid 1px var(--primary-color);
  padding: 10px;
  border-radius: 8px;
  margin-right: 4px;
  display: inline-block;
  width: 30%;
}
button {
  padding: 10px;
  border: solid 1px var(--primary-color);
  background: var(--primary-color);
  color: white;
  border-radius: 8px;
}
@media (min-width: 500px) and (max-width: 768px) {
  .results {
      grid-template-columns: repeat(2, 1fr);
  }
  input[type="text"] {
      width: 70%;
  }   
}
@media (max-width: 499px) {
  .results {
      grid-template-columns: 1fr;
  }    
}
```
## Create house location component
- 
