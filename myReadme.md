# New way of implementing routes with more features (v6.4+) :

- install react-router-dom.
- use createBrowserRouter function from this package and pass in an array of objects, where each object is a route. In traditional routing method using browserRouter, we define routes in a more declarative way, but here in new way of implementing routes, we have more of a imperative way to declare routes.
- in this new method of routing, there are more features including data fetching and data loading etc. 
- also, notice that we do not have a route for Page not found with path * at the end of all paths, because we will handle it in a new way.