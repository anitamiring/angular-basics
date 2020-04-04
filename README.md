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










