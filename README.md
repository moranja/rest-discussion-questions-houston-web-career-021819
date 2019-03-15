# REST Discussion Questions

Take 30 minutes with your table choose a *resource* that your server contains data about. A resource will be something like 'books', 'users', 'episodes', or 'characters', something that your users will be performing CRUD actions on.

-Episodes of game of thrones

1. Write out the 7 RESTful routes that correspond to the 4 CRUD actions.  Be sure to include the HTTP verb, the name of the route and the corresponding CRUD action.  

   * What SQL (if applicable) would be fired in the controller actions for each of the routes?

       -GET, '/episodes/new', Create (form), No SQL fired
       -POST, '/episodes', Create, "INSERT INTO :episodes (column1, column2....) VALUES (value1, value2....)"
       -GET, '/episodes', Read (Everything), "SELECT * FROM episodes"
       -GET, '/episodes/:id', Read (One thing), "SELECT * FROM episodes WHERE id = (params[:id])"
       -GET, '/episodes/:id/edit', Update (form), "SELECT * FROM episodes WHERE id = (params[:id])"
       -PATCH, '/episodes/:id', Update, "UPDATE episodes SET column1=new_value1, column2=new_value2... WHERE id = (params[:id])"
       -DELETE, '/episodes/:id', Destroy, "DELETE FROM episodes WHERE id = (params[:id])"

   * Why might it be important that routes and resources have a conventional structure?

      -So that it's for everyone to know whats happening on your website, and easier to understand each other's websites.

   * Which routes would you `render` a view and for which would you `redirect to` another route? Why?

      -You render a view anytime there's a GET verb, and redirect otherwise

2. Let's say you have built a Sinatra app that is a blogging platform. You have a Post and an Author model and you have controllers and routes for the CRUD actions of each model. You sit down at your computer and visit www.youramazingsinatrablog.com/posts:

   * What kind of web request is this making? (i.e. is it a `GET`, `POST`, etc request?)
      -GET request
   * What controller action (i.e. which route in which controller) will recieve that web request?
      -post controller,
      GET '/posts' do
        erb :index
      end
   * What is the response that your Sinatra app will send back to the client, i.e. the browser?
      -sends back the index.erb

3. Spend a few minutes mapping out a domain model for a parking lot. How would you model the relationship between cars and spaces? How would you keep track of how long a car had been parked in a space? How would you keep track of how much money someone would need to pay for having parked a certain amount of time?

      Cars  -<  ParkingLot   >-   Spaces, some method in the ParkingLot model, if you know how long they were in the space, charge them for that time.
