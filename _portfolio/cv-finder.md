---
title: "CV Finder"
excerpt: |
  CV Finder was developed to allow people to create a hosted resume online.
  ReactJS • Redux • NodeJS
header:
  image: /assets/images/bike-zion-thin.jpg
  teaser: /assets/images/bike-zion.jpg
sidebar:
  - title: "Hosted Project"
    text: "[CV Finder](https://cvfinder.jfirwin.com)"
  - title: "Github Repo"
    text: "[CV Finder Repo](https://github.com/jfirwin/devmountian-group-project)"
  - title: "Project Purpose"
    text: "DevMountain Group Project"
  - title: "My Role"
    text: "Back-End Developer"
  - title: "My Responsibilities"
    text: "Managed the NodeJS server. This included creating a RESTful API and managing the PostgreSQL Database."
gallery:
  - url: /assets/images/devils-tower.jpg
    image_path: assets/images/devils-tower.jpg
    alt: "placeholder image 1"
    title: "Caption 1"
  - url: /assets/images/devils-tower.jpg
    image_path: assets/images/devils-tower.jpg
    alt: "placeholder image 2"
    title: "Caption 2"
  - url: /assets/images/devils-tower.jpg
    image_path: assets/images/devils-tower.jpg
    alt: "placeholder image 3"
    title: "Caption 3"
technology:
  - url: /assets/images/tech/react.png
    image_path: assets/images/tech/react.png
    alt: "ReactJS"
    title: "ReactJS"
  - url: /assets/images/tech/redux.png
    image_path: assets/images/tech/redux.png
    alt: "Redux"
    title: "Redux"
  - url: /assets/images/tech/nodejs.png
    image_path: assets/images/tech/nodejs.png
    alt: "NodeJS"
    title: "NodeJS"
  - url: /assets/images/tech/postgresql.png
    image_path: assets/images/tech/postgresql.png
    alt: "PostgreSQL"
    title: "PostgreSQL"
  - url: /assets/images/tech/auth0.png
    image_path: assets/images/tech/auth0.png
    alt: "Auth0"
    title: "Auth0"
classes: wide
date: 2018-07-30
---

## Summary

CV Finder was developed as a final group project for the DevMountain *Fullstack Web Development* course. It is built using ReactJS, NodeJS (using Express), Redux, PostgreSQL, and Auth0 for authentication. It features a RESTful API and Responsive Design. It is being hosted by Digital Ocean. A link to the live project is [here](https://cvfinder.jfirwin.com "CV Finder Hosted") and a link to the GitHub repository is [here](https://github.com/jfirwin/devmountain-group-project).

[Luis Curvelo](https://github.com/lcurvelo27 "Luis' Github") and I built CV Finder to be an online resume tool. Users can login/sign up to create their own profile, or any user can use the search functionality to find someone with a particular set of skills.

There were a few challenges as we developed this project which I will detail below in the [Lessons Learned](#lessons-learned) section. Most of these were gotcha-type issues, but we learned from the obstacles and ultimately (hopefully) grew from them.

## Gallery

{% include custom_gallery %}

## Lessons Learned

We learned a few lessons along the road as we were developing this project.

> Measure twice, cut once.

Surprisingly, we did a fairly good job planning out how the application was going to work in the beginning. It was during the execution that we started to see things unravel. Files became excessively long and hard to debug. The code wasn't clean, but we were far enough along that we couldn't afford to refactor the fundamental issue plaguing our project. What was the problem? See below.

> Read the docs first.

Ah yes, so goes the old adage. The main issue that we encountered stemmed from the way that our Redux store was set up. We had many nested objects. Updates were being made to the Redux Store, but on a grandchild/great-grandchild level. Had we read the docs in advance. We would have known that it is common practice to have a very flat State design. The way that `react-redux` checks for changes in the state is a shallow check. In order for `componentWillRecieveProps` to recognize that changes had been made, we needed to add prolific code to the `reducer`.

For those of you who may be running into issues like "react-redux react component not updating recieving new props" or "shouldComponentUpdate not firing" or "componentWillRecieveProps not firing" perhaps take a look at this lifesaver of a link [here](https://redux.js.org/faq/reactredux#why-isnt-my-component-re-rendering-or-my-mapstatetoprops-running). I hope it helps. the TLDR for this is React-Redux only checks a shallow equality reference check in the `shouldComponentUpdate` lifecycle method. If you havent made changes all the way down your tree, it's not going to pick up on it.

The more detailed explanation is below. (Next lesson located after the two code blocks.)
```javascript
function reducer(state = initialState, action){
	switch(action.type){

    case type.EXAMPLE_FOR_WEBSITE:
      let newData = action.payload.data[0]
      let a = Object.assign({}, state)
      a.b = newData
      return a /* a hasn't changed on a shallow level
                shouldComponentUpdate won't recognize
                that there is anything new */
    default:
			return state
	}
}
```
compared to
```javascript
function reducer(state = initialState, action){
	switch(action.type){

    case type.EXAMPLE_FOR_WEBSITE:
      let a = Object.assign({}, state) // unchanged a
      let updateB = Object.assign({}, a.b) // replacement for b
      let newData = action.payload.data[0]
      updateB.c = newData.updateC // b replacement getting updates for c
      a.b = updateB // a now being updated with new b with new c
      return a // return a that shows differnces down the tree to c

    default:
			return state
	}
}
```

> Browser compatibility

We finally muddled our way through the convoluted nightmare of a reducer, and hosted CV Finder. We hooked up our custom domains and felt the satisfaction of having our application being tested on our phones. Only the iPhone seemed to disagree. Once a user was authenticated we encountered a bug that we hadn't seen yet. The inputs for the user edit pages were not working. We had tested our responsive design in Chrome the entire time, but when we popped the app locally into Safari, we were able to replicate the behavior. After some digging we were able to figure out what was going on But its always worth noting that you should check compatibility via multiple browsers.

## Technologies Used

{% include tech_stack id="technology" %}

## Features

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.



My role initially was to set up the backend. We used PostgreSQL & NodeJS. I put together a RESTful API and modularized the `index.js` folder so that it is only X lines long. I learned that I _really_ enjoy writing up the server side. SQL was challenging but I figured out a way to do it. I learned a lot about how not to set things up in the future to prevent a lot of headache.
