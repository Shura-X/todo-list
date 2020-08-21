# todo-list

This todo-list is my pet-project aiming to improve my Vue.js and Vue CLI skills using components.
But it can be usefull to write some task to do.

## Installation

At first, when you downloaded the file system, you must init the project using this CMD command (if you have [NodeJS](https://nodejs.org/en/), of course):

```
npm init
```

Then, you must launch the project in *development mode* or *production mode*.

### Development mode
The only thing you must do is to use this command in CMD:

```
npm run serve
```

### Production mode
Launching the project in the *production mode*, you must use this commands:

1.
```
npm run build
```

2.
```
npm install -g serve
```

3.
```
serve -s dist
```

## Component system

This app is run by [Vue CLI](https://cli.vuejs.org/), so the components are in `src` and `src/components` directories. `src` conrains `App.vue`, the main component, which stores and processes data for the list. `src/components` contains `add.vue`, responsible for input new items to the list components, and `list.vue`, responsible for removing items from the list component.