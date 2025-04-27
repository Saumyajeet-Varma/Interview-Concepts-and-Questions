# React Router DOM

React Router DOM is a popular library used in React applications to handle routing — meaning, it lets you define different URLs (paths) for different components or pages in your app.

> It helps you navigate between different pages without refreshing the entire website.

Instead of loading a brand new HTML page every time you click a link, React Router DOM changes the content dynamically, making the app feel faster and smoother — like a true Single Page Application (SPA).

### Some important things React Router DOM provides:

- **`<BrowserRouter>`**: Wraps your whole app and enables routing.
- **`<Routes>`**: Groups all your <Route> components.
- **`<Route>`**: Defines a path and which component to show.
- **`<Link>`**: Lets you navigate without a page reload (like an `<a>` tag but smarter).
- **`useNavigate()`, `useParams()`, `useLocation()`**: Hooks that help you programmatically navigate, read URL parameters, etc.

## Step-by-step setup with react-router-dom (v6+)

### Install react-router-dom

```bash
npm install react-router-dom
```

### Wrap your app with `<BrowserRouter>`

> (In your entry point, usually index.js or main.jsx)

```javascript
import React from 'react';
import ReactDOM from 'react-dom/client';
import { BrowserRouter } from 'react-router-dom';
import App from './App';

ReactDOM.createRoot(document.getElementById('root')).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

### Define routes inside your App component

```javascript
import { Routes, Route, Link } from 'react-router-dom';
import Home from './pages/Home';
import About from './pages/About';
import NotFound from './pages/NotFound';

function App() {

  return (
    <div>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="*" element={<NotFound />} /> {/* catch-all */}
      </Routes>
    </div>
  );
}

export default App;
```

### Example Page Components

```javascript
// Home.jsx
export default function Home() {
  return <h1>Welcome Home</h1>;
}

// About.jsx
export default function About() {
  return <h1>About Us</h1>;
}

// NotFound.jsx
export default function NotFound() {
  return <h1>404 - Not Found</h1>;
}
```

# How do you create dynamic routes in React Router ?

## Define Dynamic Routes

Use `:` in the route path to indicate a dynamic segment.

```javascript
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Home from './Home';
import UserProfile from './UserProfile';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/user/:userId" element={<UserProfile />} />
      </Routes>
    </BrowserRouter>
  );
}
```

## Access the Dynamic Params

Inside the component (UserProfile in this case), use useParams to grab the dynamic part from the URL.

```javascript

import { useParams } from "react-router-dom";

function UserProfile() {

  const { userId } = useParams();

  return (
    <div>
      <h2>User Profile for ID: {userId}</h2>
    </div>
  );
}
```

# How do you programmatically navigate in React Router ?

`useNavigate()` is a React Router hook that gives you a `navigate` function.

Calling `navigate('/dashboard')` programmatically redirects the user to the `/dashboard` route.

No page reload, it just changes the view instantly

## Basic Programmatic Navigation

```javascript
import { useNavigate } from 'react-router-dom';

function MyComponent() {
  const navigate = useNavigate();

  const handleClick = () => {
    navigate('/dashboard');
  };

  return <button onClick={handleClick}>Go to Dashboard</button>;
}
```

## Navigate with Parameters

You can pass parameters in dynamic routes like this

```javascript
navigate(`/user/${userId}`);
```

## Navigate with State

You can pass state along with navigation

```javascript
navigate('/dashboard', { state: { from: 'login' } });
```

Then in the target component

```javascript
import { useLocation } from 'react-router-dom';

const location = useLocation();
console.log(location.state?.from); // "login"
```

## Navigate Backward or Forward

```javascript
// Go backward
navigate(-1);

// Go forward
navigate(1);
```

# BrowserRouter

BrowserRouter is the most common router you use in React apps to manage navigation.

It uses the browser's built-in History API (`pushState`, `replaceState`, etc.) to keep your app's URL in sync with what's displayed on the screen — without refreshing the whole page.

So when you change the URL (like going from `/` to `/about`), BrowserRouter updates the view by swapping components, not by reloading a new HTML page.

## How BrowserRouter works:

- The URL changes normally (like `/about`, `/contact`).
- It uses history stack to move forward, back, and navigate.
- You can handle "Back" and "Forward" browser buttons smoothly.
- But: Your server needs to be set up to return `index.html` for any route, otherwise refreshing the page on a deep link (`/about`) will cause a "404 Not Found" error.

# Routes

- Routes is a wrapper that contains all your Route components.
- It replaces Switch from React Router v5.
- It renders the first `<Route>` or `<Route>`-like element that matches the current URL.
- All `<Route>` components must be children inside one `<Routes>` — you cannot have them floating separately.

```javascript
import { Routes, Route } from 'react-router-dom';

<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
</Routes>
```

## Why did they replace Switch with Routes ?

- More powerful matching (like "ranking" and "sorting" of routes automatically).
- Simpler and more predictable behavior.
- Smarter nesting of routes.

## Routes vs Switch

| Feature         | Switch (v5)               | Routes (v6)                          |
|-----------------|----------------------------|--------------------------------------|
| Matching        | Manual                     | Automatic and smart                 |
| Children        | `<Route>` or `<Redirect>`  | Only `<Route>`                      |
| `component` prop| Yes                        | No (use `element` instead)          |
| `element` prop  | No                         | Yes (`element={<Component />}`)     |

# Route

- Defines a specific path and tells React Router which component to show when the URL matches that path.
- Uses the element prop to render a component (not component like in older versions).
- You can include dynamic parameters in the path, like :id, to match variable parts of the URL.

```javascript
<Route path="/user/:id" element={<UserProfile />} />
```

# Link

- Used to navigate between routes inside a React app without reloading the page.
- Replaces the traditional `<a>` tags.
- It does not cause a full-page reload — it maintains the Single Page Application (SPA) experience.

### Why use `<Link>` instead of `<a>` ?

- `<a>` refreshes the page by default
- `<Link>` updates the URL in memory and lets React Router change the view without a page reload.

```javascript
import { Link } from 'react-router-dom';

<Link to="/">Home</Link>
<Link to="/about">About</Link>
<Link to={`/user/${userId}`}>Profile</Link>
```

# NavLink

- Just like `Link`, it is used to navigate between routes without reloading the page.
- `NavLink` can automatically add an "active" style or class when the link matches the current URL.
- `isActive` is a special prop provided by NavLink.

### Why use `<NavLink>` instead of `<Link>` ?
- When you want to highlight the link of the current page in a navbar or menu.
- Example: the "Home" button looks bold when you are on the Home page.

```javascript
import { NavLink } from 'react-router-dom';

<NavLink to="/">Home</NavLink>
<NavLink to="/about">About</NavLink>
<NavLink to={`/user/${userId}`}>Profile</NavLink>
```

If you want to customize the active link style, you can do something like:

```javascript
<NavLink 
  to="/" 
  style={({ isActive }) => ({
    fontWeight: isActive ? 'bold' : 'normal',
    color: isActive ? 'blue' : 'black',
  })}
>
  Home
</NavLink>
```

# Handling 404 pages in React Router

You add a **"catch-all"** route at the bottom using `path="*"`.

```javascript
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './Home';
import Profile from './Profile';
import NotFound from './NotFound';  // 404 page

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/profile" element={<Profile />} />
        
        {/* 404 Route */}
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

> You create `NotFound.jsx` to show a custom message when a page is not found (404 error).

## How it works

- `path="*"` matches any route that wasn’t matched earlier.
- It must be the last route inside `<Routes>`.
- When someone visits an unknown URL (like `/random-url`), they see the `NotFound` component.

# URL parameters and query strings in React Router

## URL Parameters

Define a route with parameters

```javascript
<Route path="/user/:userId" element={<UserProfile />} />
```

Navigate to it

```javascript
navigate(`/user/${userId}`);
```

Access it inside the component

```javascript
import { useParams } from 'react-router-dom';

function UserProfile() {
  const { userId } = useParams();
  return <div>User ID: {userId}</div>;
}
```

## Query Strings

Navigate with query parameters

```javascript
navigate('/search?query=react&sort=desc');
```

Read query strings

```javascript
import { useLocation } from 'react-router-dom';

function SearchPage() {
  const location = useLocation();
  const queryParams = new URLSearchParams(location.search);
  
  const query = queryParams.get('query');
  const sort = queryParams.get('sort');

  return (
    <div>
      Searching for: {query}, sorted: {sort}
    </div>
  );
}
```

> Quick tip: Combine both (URL parameters and query strings)

# Outlet component in React Router

The `<Outlet />` component in React Router is used as a placeholder in your parent component where the matched child routes will be rendered.

- Parent Route: A component that is always rendered when its route is matched.
- Child Routes: Routes that are nested inside the parent route.
- The `<Outlet />` component is placed inside the parent component, and it’s where the child routes will be rendered based on the current URL.

Suppose we have a layout that all dashboard routes should share

```javascript
// Layout.js
import { Outlet } from "react-router-dom";

export default function Layout() {
  return (
    <div>
      <h1>Dashboard Layout</h1>
      <nav>/* Nav links here */</nav>
      <main>
        <Outlet /> {/* This is where nested route components render */}
      </main>
    </div>
  );
}
```

Now set up routes

```javascript
import { Routes, Route } from "react-router-dom";
import Layout from "./Layout";
import DashboardHome from "./DashboardHome";
import DashboardSettings from "./DashboardSettings";

function App() {
  return (
    <Routes>
      <Route path="/dashboard" element={<Layout />}>
        <Route index element={<DashboardHome />} />
        <Route path="settings" element={<DashboardSettings />} />
      </Route>
    </Routes>
  );
}
```

## What Happens Here:

- Visiting `/dashboard` renders `Layout` + `DashboardHome`.
- Visiting `/dashboard/settings` renders `Layout` + `DashboardSettings`.
- Whatever child route is matched, its component goes into the .

## When to Use It

- Use when you are building nested routes.
- Use when you want a shared layout (like a sidebar, header, etc) with route-specific content inside.

# Nested routes in React Router

## What Are Nested Routes ?

- Nested routes allow you to define routes within routes, reflecting the hierarchical structure of your UI in the URL and routing configuration.
- They enable you to create parent-child relationships between views, where a parent component provides a layout or context, and child routes render inside it.

## Why Use Nested Routes ?

- Modular UI: Many UIs have shared layouts (e.g., a dashboard with a sidebar) where only a portion of the screen changes depending on the route.
- Maintainability: Nesting routes keeps routing definitions clean and organized, especially in large applications.
- Logical Structure: URLs like `/dashboard/profile` or `/dashboard/settings` make sense to users and developers when tied to a shared layout.

## How They Work (Conceptually)

- Parent route defines a layout (ex: with navigation, sidebar, header).
- Inside the parent component, there is a special `<Outlet />` — a placeholder where child routes will be rendered.
- Parent component stays always visible, Child component changes depending on the URL.

## Analogy

- Think of nested routes like folders within folders:
- /dashboard → opens the main "Dashboard" folder (layout)
- /dashboard/profile → opens a subfolder inside the dashboard (child route)
- The main folder (layout) stays open while you explore subfolders (child views)

These could all render inside a shared Dashboard layout.

> `/dashboard` <br> `/dashboard/settings` <br> `/dashboard/profile`

## Step-by-Step: Using Nested Routes in React Router

### 1. Create a Layout Component

This component renders common UI (like a navbar, sidebar) and an where child routes appear.

```javascript
// DashboardLayout.jsx
import { Outlet, Link } from 'react-router-dom';

function DashboardLayout() {
  return (
    <div>
      <h2>Dashboard</h2>
      <nav>
        <Link to="profile">Profile</Link>
        <Link to="settings">Settings</Link>
      </nav>
      <Outlet /> {/* Child routes will render here */}
    </div>
  );
}
```

### 2. Define Routes with Children

```javascript
<Routes>
  <Route path="/dashboard" element={<DashboardLayout />}>
    <Route path="profile" element={<Profile />} />
    <Route path="settings" element={<Settings />} />
  </Route>
</Routes>
```

> `/dashboard/profile` → renders DashboardLayout with Profile inside <br> `/dashboard/settings` → renders DashboardLayout with Settings inside

- The parent component (like `DashboardLayout`) is always rendered when the route matches.
- Inside the parent, there's an `<Outlet />`.
- The child component (like Home, Profile, etc.) will fill into the `<Outlet />` based on the URL.

# Private Routes

## 1. Create an Auth Context (optional but recommended)

```javascript
// AuthContext.js
import { createContext, useContext, useState } from 'react';

const AuthContext = createContext();

export const AuthProvider = ({ children }) => {
  const [user, setUser] = useState(null); // null = not logged in

  const login = (userData) => setUser(userData);
  const logout = () => setUser(null);

  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
};

export const useAuth = () => useContext(AuthContext);
```

## 2. Create a PrivateRoute Wrapper

```javascript
// PrivateRoute.js
import { Navigate, Outlet } from 'react-router-dom';
import { useAuth } from './AuthContext';

const PrivateRoute = () => {
  const { user } = useAuth();

  return user ? <Outlet /> : <Navigate to="/login" replace />;
};

export default PrivateRoute;
```

## 3. Use PrivateRoute in your Routes Setup

```javascript
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import { AuthProvider } from './AuthContext';
import PrivateRoute from './PrivateRoute';

function App() {

  return (
    <AuthProvider>
      <Router>
        <Routes>
          <Route path="/login" element={<LoginPage />} />
          
          {/* Protected routes */}
          <Route element={<PrivateRoute />}>
            <Route path="/dashboard" element={<Dashboard />} />
            <Route path="/profile" element={<Profile />} />
          </Route>
          
          {/* Public route */}
          <Route path="/" element={<Home />} />
        </Routes>
      </Router>
    </AuthProvider>
  );
}
```

### How it works

- PrivateRoute acts like a gatekeeper. 
- If the user is authenticated, Outlet renders the nested routes (/dashboard, /profile).
- If not, the user is redirected to /login.