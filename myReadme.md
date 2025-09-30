# Application planning in react :

- So we are building an app fromm which a user can order pizza from a dynamic menu which will be loaded using an api. There will be no login signup feature for now.  
- So we have 4 main feature categories in our app : User, Menu, Cart and Order.  
- Now decide URL for all pages : /, /menu, /cart, /order/new, /order/:id.
- Now decide state management and technologies decisions :

* User : Global UI state. (Redux)
* Menu : Global remote state. (Menu is fetched from API). (React Router)
* Cart : Global UI state. (no need for API, just store in app). (Redux)
* Order : Global remote state. (fetched and submitted to API). (React Router)

# File structure for project :

- So what developers prefer is to use a feature based structure, one folder for each feature.
- So 4 feature folders : menu, cart, order, user.
- Now there are some components which are more reusable and actually do not belong to any of the features, so create one folder for that : UI. So this is for buttons, inputs etc.
- Now create a folder for services for reusable code for interacting with API.
- Now create one folder utilities for helper functions that we can reuse in multiple places in our app. So these are stateless helper functions which do not create side effects. 
- Now copy starter files and place them accordingly. 

