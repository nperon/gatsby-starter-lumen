---
title: A Playground Stub for Practicing NgRx
date: "2019-04-20T22:40:32.169Z"
template: "post"
draft: false
slug: "/posts/ngrx-playground/"
category: "Training"
tags:
  - "Angular"
  - "NgRx"
  - "Redux"
  - "RxJS"
  - "JavaScript"
  - "Front End"
  - "Web Development"
description: "NgRx is a library designed to integrate a Redux store in any Angular application. In this tutorial, a stub application is used as a starting point for practicing NgRx Redux."
---

- [Redux and the NgRx library](#redux-and-the-ngrx-library)
- [Starting point](#starting-point)
- [Moving the disk](#moving-the-disk)
- [Changing a text label](#changing-a-text-label)
- [Ergonomic refinements with RxJS](#ergonomic-refinements-with-RxJS)
- [Coding an NgRX @Effect to dispatch asynchronous actions](#coding-an-NgRX-effect-to-dispatch-asynchronous-actions)
- [Discussion](#discussion)


## The NgRx library

Redux consists in a store with a single access point intended for holding the state of any JavaScript application. The 
Redux library integrates well in React applications thanks to libraries like react-redux or reselect which provide
the connection between the Redux store and the React components. 

NgRx consists in a Redux store and its connecting API which is specific to Angular, the two of them wrapped together 
in a single library. The state selectors of the store are provided in the shape of RxJS Observables. Although RxJS is 
not our focus here, it is a reactive programming library which is part of most significant enough Angular applications. 
The use of NgRX with Angular is covered in the official Angular documentation. 

## Starting point

The stub application which we intend to use as our playground is an Angular application with one single component. 
The template of that component includes an svg image with shapes, e.g. a disk or a rectangle. Every shape has
parameters stated as attributes in the respective svg tag. The values of these parameters can be 
bound to variables defined in the component using angular binding directives. We could stick to holding the values 
of the parameters in variables simply defined as fields of the component. Other options like coding some 
Angular Service or using an RxJS Subject would be valid too. Instead, the kind of place where we want to store 
the parameters of our svg image in this tutorial is an NgRx store. 

Our stub application is available on github. Directly clone the starting point branch with:
```bash
git clone -b 00-starting-point https://github.com/nperon/ngrx-dojo
```
A node version as recent as version 8.3 at least is required. It is also required to have 
[Angular CLI](https://cli.angular.io/) installed to deploy the app locally. 
Move to the cloned project directory with cd ngrx-dojo. Install then the dependencies with 
npm install. Finally, deploy the project locally with ng serve.

Application should now display in your web browser at http://localhost:4200/.

![ngrx-screenshot.jpg](/media/ngrx-screenshot.jpg)

The only Angular Component in the code is called editable-svg.component.ts. It is found in the 
src/app/editable-svg directory. The associated html template is in the same directory as it is by default
in a project generated with Angular CLI. Right in the same directory is found a folder called store 
which contains our store reducer, editable-svg.reducer.ts. These are the three only files where we need
to write code in this tutorial.

It is in the parent module src/app/app.module.ts of the app that our editable-svg reducer is 
configured to operate as the NgRx store. Configuration is done at line 19 with the statement

```javascript
StoreModule.forRoot({ editableSvg: editableSvgReducer })
```

This single line declares our editableSvgReducer as an NgRX singleton store available to all components in the app. 

The template editable-svg.component.html includes the code of the svg with two shapes 
&mdash; a red disk and a green rectangle &mdash; followed with the code of the dashboard 
with buttons displayed below the svg. The different parts are commented. 

In the code of the associated component editable-svg.component.ts, it is seen how the 
store singleton is injected in the constructor. It is also seen how the field editableSvgState
is initialized from the latter store. 

As it is now, our component is already connected with the store. It is in the reducer store/editable-svg.reducer.ts
that the position of the red disk (initialState) is initialized when application starts. This can be 
verified by changing the xCoordinate and yCoordinate in initialState while observing the position of the red disk.
The state returned by our editableSvgReducer, so far empty, is just that initialState.

We are now ready to add new features to the app. In each of the following sections, a new task is proposed.
It is going to mainly consist in defining Redux actions while adding code in the reducer to treat the latter actions. 
In case you fancy other tasks and features rather than the ones we suggest at any stage in the tutorial, 
feel free to follow up and implement your own ideas. 

## Moving the disk



## Changing a text label
## Ergonomic refinements with RxJS
## Coding an NgRX @Effect to perform asynchronous actions
## Discussion

Stateless/Stateful
Pros / cons of the NgRx store, vs a Service, vs an RxJS Subject Scaling with respect

