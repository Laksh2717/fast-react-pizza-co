# Building App Layout :

- basically now we want that whatever page we are on, we want a layout for it, like a header on top and something in below, that should be rendered in every page, this is called app layout.
- so create AppLayout in ui, and add content in it accordingly.
- now how to connect this layout to every page i.e. route. so we have to make a parent route with no path and element your layout component. and make all routes as its children, so all its children will get this layout on their page. 

* So any route with no path and only element is treated as layout route, and all its children get that layout on their page.

- now in that layout, we have to render different content corresponding to the page we are on,like if we are on /cart, then render content of Cart element, if on / then render Home element etc. so we use Outlet for that. 