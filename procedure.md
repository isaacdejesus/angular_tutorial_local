# Set up and create new project
## Install angular cli
- npm i -g @angular/cli
## Create new project
- ng new app-name
## Run project
- npm start 
- ng serve

# Creating components
## Create component
- Navigate to root dir of app_name 
- ng generate component component_name
## Adding component to another component
- In this example, use Home component in root component App
- First, import the Home component
- Then Home component can be used in the template section of App component
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
## Styling a component
- Upon creation of a component a .css file belonging to component is created
- For ex, Home component contains:
    - Home.ts for component's code
    - Home.css for styling
- The Home.css is linked to the Home.ts file using the *styleUrls* property
