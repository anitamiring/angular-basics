# angular-basics

Angular is ***JavaScript Framework*** which allowes to create reactive ***Single-Page-Applications*** (SPAs). Single page means it is all about one html page which is updated in the browser. If there is nead to use database it doesn't interrupt page flow.  

### Angular Versions 

 AngularJS (Angular 1) ==> Completely rewrite ==>
 **Angular 2** ==> realeased in 2016 ==> (Angular 3 is skipped) ==>
 Angular 4 ==> ... ==> New version every 6 month ==>
 **Angular 9** (now)

### Angular Installation 

* Require node.js preinstalled.
* Angular CLI - globally 
```
npm install -g @angular/cli@latest 
```
* Create and run new project 
```
ng new project-name
cd project-name
ng serve 
```

### TypeScript

Angular is meant to use with TypeScript. TS has more features then vanilla JS, like 
types, classes, interfaces and so on. TS is not compiled in the browser, so before that it is 
compiled to JS, and then JS is compiled in the browser.

### Bootstrap Setup

* Installation 
```
npm install --save bootstrap@3 
```
* Adding new styling to the project
```
angular.json 
...
"styles": [
"node_modules/bootstrap/dist/css/bootstrap.min.css",
"src/styles.css"
]
...
```
### How Angular App gets loaded and started 
* Angular create SPAs
* index.html is the file (single page) served by server, with root component in it
```
<body>
  <app-root></app-root>
</body>
```
* root component contains and binds all custom component in our app 
```
app.component.ts 
...
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
...
```
* ng serve process rebuild our project - Angular CLI adds js scripts bundles and automatically adds right imports into index.html
* main.ts is the first code which gets executed. Here we create platform - an entry point for Angular on web page. Each page has only one platform. There potentially can be many applications on one platform. Each application is created from the module using bootstrapModule method. So the statement shown below first creates a platform and then the application instance. 
```
main.ts
platformBrowserDynamic().bootstrapModule(AppModule)
```
When the application is being created Angular checks the bootstrap property of the module used to bootstrap the application (AppModule):
```
app.module.ts 
@NgModule({
  declarations: [
    AppComponent,
    ServerComponent
  ],
  imports: [
    BrowserModule,
    FormsModule
  ],
  providers: [],
  bootstrap: [AppComponent] <-- bootstrap property 
})
export class AppModule {
}
```
Then Angular looks for the selector of the bootstraped component. And this is how the circle close. 

### Create new component 
* All custom components are placed in the root component, which bootstrap whole application 
* Component is basically normal ts class 
```
server.component.ts
export class ServerComponent {

}
```
* Then we have to tell it is not just a normal ts class but something special. There we use decorators - *** Component *** decorator in this case. Decorator is a ts feature which allows us to enhance ts classes. 
```
server.component.ts 
import {Component} from '@angular/core';

@Component({
  selector: 'app-server',
  templateUrl: './server.component.html'
})
```
* To use new **Component** in our App, we need to declare it. This simple App is created from one  **Module**. 
* **Module** is another ts decorator which create bundle package from all components. As previously said bootstrap property says which component bundle whole application, and it is AppComponent. But we need to declare all other components as well. 
```
app.module.ts 
import {BrowserModule} from '@angular/platform-browser';
import {NgModule} from '@angular/core';
import {FormsModule} from '@angular/forms';
import {AppComponent} from './app.component';
import {ServerComponent} from './server/server.component'; <--- import custom component 

@NgModule({
  declarations: [
    AppComponent,
    ServerComponent <---- Custom component declaration 
  ],
  imports: [
    BrowserModule,
    FormsModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule {
}
```
### Create component from CLI
```
ng g c name 
```
### Component selectors 
Select by element: 
```
selector: 'app-server'
```
Use this component: 
```
<app-server></app-server>
```
Attribute selector:
```
selector: '[app-server]'
```
Use this component:
```
<div app-server></div>
```
Select by class:
```
selector: '.app-server'
```
Use this component:
```
<div class = "app-server"><div>
```
### Databinding 
**Databinding** stands for communication of the **Template (HTML)** with **TS Code (Business Logic)**
#### Types of communication 
Output data: TS Code --> Template(User)
* **String Interpolation** ( *{{ data }}* ) 
* **Property Binding** ( *[property] = "data"* )

React to (User) events:
* **Event Binding** ( *(event) = "expression"* )

Combination of Both:
* **Two-Way-Binding** ( *[(NgModel)] = "data"* )

### String Interpolation {{ data }}
String interpolation can be use with any ts code which can be resolve to the string int the end. We can't use multiline code here. We can write simple strings, use class properties or use functions which will be resolve to a string.
```
server.component.ts
export class ServerComponent {

  serverID = 10;
  serverStatus = 'offline';

  getServerStatus()
  {
    return this.serverStatus;
  }
}
```
```
server.component.html
<p> {{ 'Server' }} with ID {{ serverID }} is {{ getServerStatus() }} </p>
```

### Property Binding [property] = "data"
Property binding just take property of the HTML element and assign our TS property to that. Properties are updated **dynamically**. This is one of advantage using Angular, it makes really easy to interact with DOM to change properties during runtime. 
```
servers.component.ts
  allowNewServer: boolean = false;

  constructor() { 
    setTimeout(() => {
      this.allowNewServer = true;
    }, 2000);
  }
```
```
servers.component.html
<button 
    class = "btn btn-primary"
    [disabled] = "!allowNewServer">  <---- Property Binding
    Add new Server 
</button>
```








