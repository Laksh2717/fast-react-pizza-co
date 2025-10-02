# Loading indicator :

- Now, in order to be able to display an indicator like this, we need to know whether this data is actually being loaded right now, right? So currently, we don't have that information anywhere here yet, right? So there's no like is loading state somewhere to be seen.

- so we will use a hook useNavigation provided by react router and with this we will be able to see whether our app is currently idle or whether it is loading data, or submitting data, and this information is actually for the entire app and not just for one page. so if one of the pages is loading, then navigation state will become loading no matter which of the page is being loaded. 

- so we can not create loader per page. we will just create one generic loader and use it everywhere in case of loading data. 

# Handling errors :

- So with create browser Router whenever there is some error that is thrown in a loader, an action, or simply while rendering a component, we can render an error element instead of these elements here that correspond to the actual pages.

- so we will specify an errorElement in the parent route because the errors that happen in the nested route will bubble up to parent route. and then we will check 2 types of errors, first is go to a route that does not exist, so it will show an error message there, and then try to get an error in data fetching, so change the api url, then also you will see an error message. 

- but now you can notice that the error message is shown without our app layout, but we want to show error component within the layout, so we have to put error inside any of the nested route, and so we will put it in menu route, as it is most probable that an error will occur here only. 

- So this is the very basic and most straightforward way of dealing with errors using the new React Router. So basically using the error element property that we can define on each of the routes, it's just important to notice that each of these errors here will bubble up to the parent route unless it is actually handled in the route itself. So by placing error element right on the route where the error might happen.