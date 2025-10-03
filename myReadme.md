# Writing data with "Actions" :

- so lets learn how to write data or to mutate data on the server. So while the loaders that we used earlier are to read data, actions are used to write data or to mutate data. So a state that is stored on some server. Or in other words, actions allow us to manage this remote server state using action functions and forms that we then wire up to routes similar to what we did earlier with the loaders.

- remember that orders are made by sending a post request with the order data to the API. And so these actions and forms that we just talked about are ideal to create new orders.

- so when we submit a new order, we need to submit the user data, olus the selected pizza we have stored in the cart. now we do not code to make a cart yet, so we will use a fake cart to place order. 

- now in create order, we already a fake cart and a form for new order. now in order to make this form work nicely with react router, we need to replace it with the form component that react router gives us which is "Form". 

- in this "Form", we can use PUT, PATCH, DELETE, POST request but not GET request.

- then we could also specify the action where this form needs to be submitted to. but this is not going to be necessary as by default react router will simply match the closest route. 

- now we have to create a action function similar to loaders, which we will then connect to route, so whenever this form is submitted, it will call this action function and pass in the request that was submitted. 

- ALWAYS REMEMBER THAT WE NEED TO RETURN SOMETHING IN THESE LOADER AND ACTION FUNCTONS. 

- then to connect this action to the route, specify the action property in the route. so now whenever there will be a form submission on that route, that action function will be called. 

- also you will not be able to see formData variable(present in code) in console, we first have to convert it to js object, which is done as you can see, and its just a recipe you need to know. now you will be able to see data in console.

- so notice how easy it is this form submission with react router, you do not need to create any state variables for each of these input fields, also do not need to create any loading state etc.

- Now next up we also want to get our cart data into the action. So the cart is right here in createOrder component, but we also now want to basically submit it in the form so that we can then get access to it in the action. So you might think that we can just use the cart variable in the action, but later on, this cart will actually come from Redux. And so then we can really only get this cart right here in CreateOrder component. Now, thankfully for us, there is a nice way of actually getting some data into the action without it being a form field. So what we can do is a hidden input. 

- so just make a hidden input for it, with name and value. now value should be a string, it can not be an array or object, so convert cart to json string. okay so now when you log the data, you will be able to see cart.

- but here there are 2 errors, first is that you will see that json string of cart in console, so we need to convert it to object back, and second is that priority filed only exists when it is on, otherwise it is not present in data if it is off. 

- so we solved these 2 problems in order variable as you can see. so we now have data from form in the shape that we want. so we can now use it to create a new order. so we already have an api endpoint in the starter code to create a new order, createOrder function in apirestaurant. so this function actually returns the newly created order. 

- so we created a newOrder using that function. this newOrder that we get here is already the new object that is coming back from the api as a response of calling createOrder function. so this will also contain an id. 

- now what we want is to redirect user to that order/id. but here we can not use useNavigate hook as hooks can not be used in normal functions. so we will use a function "redirect" which is provided by react router. 

- now we will do one thing that whenever the form is getting submitted, we will make the form submit button disabled. and we can easily do this with useNavigation hook, we have also use this hook in case of loading, now we will use it in case of submitting data.

# Error Handling :

- first of all we have fields as required, so a user can not just simply submit a form. 

- but yeah for example, a user can have some random phone number with letters and characters too, so we have to check if its a valid phone no or not, so we will do it in our action. 

- so what we will do is to check whether the phone is valid or not before creating new order. also we will create an empty errors object first and then if there is any error, we will add that error in this object and then we will check if there are any errors in errors object, and if there are, then we will just return that errors object from our action function. and so then in the component that is connected to this action, we can get access to the data which is returned from that action in case there was no submission. so we use a hook useActionData to access that data and then accordingly display error message.

- lets have a deeper look on this by a summary :

1. The Role of the action Function :

- An action function handles data submissions from forms. It's triggered by POST, PUT, PATCH, or DELETE requests.

- What you return from the action determines what happens next.

2. Two Possible Outcomes of an Action :

- 2.1. Success Case: Return a redirect(). 

- What it is: A command to navigate the user to a new URL.
- When to use it: After a successful data creation or update.
- Effect on useActionData: The useActionData hook will receive undefined because the component is unmounted during the redirect.
- Why it's recommended :

- Good User Experience (UX): Gives clear feedback that the operation was successful by taking the user to a relevant new page.
- Prevents Double Submission: Follows the Post/Redirect/Get (PRG) pattern. After redirecting, the browser's last action is a GET, so refreshing the page won't re-submit the form.

- 2.2. Failure/Validation Case: Return Data :

- What it is: Any plain data, typically an object containing validation errors.
- When to use it: When form input is invalid and you need to display an error message to the user without losing their entered data.
- How it works : 

- React Router stays on the current page.
- The data you returned is made available to your component via the useActionData hook.
- After the action completes, React Router automatically re-runs the loader function for the current route to ensure any displayed data is fresh (this is called "re-validation").

3. The loader Function's Role After an Action :

- A loader fetches data when a route is first loaded.
- Crucially, if an action on the same route returns data (not a redirect), the loader is automatically called again.
- This ensures that if the form submission changed any data that the page displays, that data is instantly refreshed.
- If a route has an action but no loader, this re-validation step is simply skipped, which is perfectly fine.

# Summary in Bhai language :

- so till now we have studied loaders and actions in react router. loaders are used to load some data as the page is loaded and actions are used to submit some data from the forms.

- so a page can either have loaders or have actions or both or none.

- so now when we submit some form and all the form data is valid then it will simply redirect to the page specified in the action function. but if some error occurs, now our action function will return some data which is basically errors. so now react router will stay on the same page and it will reload that same page, so if it has loaders, then that loader will be called again and also in the component that is using useActionData, that will be re rendered and display latest changes. but if that page does not have any loaders, then only that component which is using the action data using useActionData will be re rendered to show latest changes. 

- so in case of to do list we can have both loaders and actions for the same page to show the recently added task. 
