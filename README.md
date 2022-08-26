# How to build a 3D App using React, Typescript and React Three Fiber (Three.js)?

This article was largely inspired by [Learn Three.js using React: Build a 3D Tesla Workshop 2021](https://www.udemy.com/course/threejs-using-react/) Udemy course. At the time of writing this article, 24th of August, 2022, the course has been outdated by more than a year. Since then, both Three.js and React Three Fiber has been drastically updated, and this article will see to those changes.

## Introduction

Although we will be using a lot of the philosophies from the Udemy course as a guide, I will be adding in other requirements to build out our end product.

My goal for the end product is to create a 3D application that features a user interact-able camera, a user-controllable model, and a dynamically changing scene such as a day/night cycle with a rotating Sun and shadows.

We will be building a React Typescript app using ViteJS. We will also create our 3D scene using React Three Fiber, and other helper packages to make the process smoother. Lastly, we will be using Zustand as a state management library.

### Setting up a Development Environment

To start this project, we will create our React Typescript app using ViteJS.

    yarn create vite r3f-app --template react-ts

After creating the application, we are going to install the following dependencies.

We will be using React 18:

    yarn add react@^18.0.0 react-dom@^18.0.0

We will have to install Three JS and its type library:

    yarn add three@^0.143.0 three-stdlib@^2.13.0

We will also need to install React Three Fiber and the rest of their helper functions:

    yarn add @react-three/cannon@^6.3.0 @react-three/drei@^9.19.2 @react-three/fiber@^8.2.2 @react-three/postprocessing@^2.6.1

Lastly, we will need to install our state management library, wouter as our React routing library, and emotion for our CSS-in-JS styling.

    yarn add zustand@4.1.1 wouter@2.8.0-alpha.2 @emotion/react@^11.10.0

We will also need to install our dev dependencies.

    yarn add -D @types/react@^18.0.0 @types/react-dom@^18.0.0 @types/three@^0.143.0

#### Table of Dependencies

The table below shows the dependencies you have installed. This is reflected in your `package.json` file.

| Dependencies                | Versions      |
| --------------------------- | ------------- |
| react                       | ^18.0.0       |
| react-dom                   | ^18.0.0       |
| three                       | ^0.143.0      |
| three-stdlib                | ^2.13.0       |
| @react-three/cannon         | ^6.3.0        |
| @react-three/drei           | ^9.19.2       |
| @react-three/fiber          | ^8.2.2        |
| @react-three/postprocessing | ^2.6.1        |
| zustand                     | 4.1.1         |
| wouter                      | 2.8.0-alpha.2 |
| @emotion/react              | ^11.10.0      |

| Dev Dependencies | Versions |
| ---------------- | -------- |
| @types/react     | ^18.0.0  |
| @types/react-dom | ^18.0.0  |
| @types/three     | ^0.143.0 |

## Building a 3D Scene

### Setting up the Application

Before we build our 3D scene, let's start by running our app. After running the following commands, the app should be hosted at <http://localhost:3000/>.

    cd r3f-app
    yarn dev

We will creating 3 folders: `public/` in the root directory, and `components/`, and `pages/` in our `src/` directory. Our project structure would look like this:

    r3f-app
    ├─ node_modules/
    ├─ public/
    ├─ src/
       ├─ components/
       ├─ pages/
       ├─ App.css
       ├─ App.tsx
       ├─ index.css
       ├─ logo.svg
       ├─ main.tsx

We will remove `App.css` and `logo.svg` from our `src/` folder directory since we will not be using them.

In our `App.tsx`, we will remove all of the imports and return a normal `null` for now.

    import  React from  "react";

    const  App  = () => {
      return null;
    }

    export default App;

Since we are also using React v18, our `main.ts` will need to use `createRoot` like the following.

    import React from "react";
    import ReactDOM from "react-dom/client";
    import App from "./App";
    import "./index.css";

    ReactDOM.createRoot(document.getElementById("root")!).render(
      <React.StrictMode>
        <App />
      </React.StrictMode>
    );

#### Creating Pages

To set up our app properly, we will create 2 new pages. A `Home` page and a `Scene` page under our `pages/` directory.

    r3f-app
    ├─ src/
       ├─ components/
       ├─ pages/
          ├─ Home/
             ├─ Home.tsx
             ├─ index.ts
             ├─ styles.tsx
          ├─ Scene/
             ├─ Scene.tsx
             ├─ index.ts
             ├─ Scene.tsx
          ├─ index.ts

For our `pages/Home/Home.tsx`, we will export a function that outputs a JSX with a "Home" name,

    import React from "react";

    const Home = () => {
      return <div>Home</div>;
    }

    export default Home;

and re-export it in our `pages/Home/index.ts`.

    export {default as Home} from "./Home"

We will do the same for `pages/Scene/Scene.tsx`,

    import React from "react";

    const Scene = () => {
      return <div>Scene</div>;
    }

    export default Scene;

as well as our `pages/Scene/index.ts`.

    export {default as Scene} from "./Scene"

We will also re-export them in our `pages/index.ts`.

    export {default as Home} from "./Scene"
    export {default as Scene} from "./Home"

#### Creating Routes to those Pages

After we create these pages, we will have to link them. On our `src/App.tsx`, we will import our newly created Pages and use wouter to link them together.

## Geometry, Lighting, Materials and Textures

## Events and Controls: Becoming Interactive

## Adding Physics and Models to the Scene

## All about the Camera and Shadows

## Postprocessing
