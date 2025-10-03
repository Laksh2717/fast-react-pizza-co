# Fetching order information :

- now what we want is that when i search a order id, then i get all its information. so we have to fetch order information. so you can see that we have a getOrder function in apirestaurant. so we will be using that. 

- so first create a search field in header. make it controlled element.

- now when we write some id in search bar and hit enter, it will redirect us to that page i.e. /order/:orderId, so now what we want is to load that order id data in that page. so we will do exactly same thing which we have done in menu.

- first create a loader function in Order.jsx file. now we have to fetch information about the order using getOrder here, but getOrder needs an id.

- So, how do we get the ID from the URL right into this function? so we can think of using useParams hook. However, since this is a hook it only works inside components. It doesn't work in regular functions.

- But, luckily for us, React Router has, of course, thought of the situation, and therefore it passes in some data into the loader function as it calls it, and one of the properties of the object that the loader function receives is exactly the params. so use it in the loader function.

- now connect the loader function in the route, and read the data using useLoaderData.

- also when you run the code, you will be able to see loading indicator while the order information is being fetched. 

