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







