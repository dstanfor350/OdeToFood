https://app.pluralsight.com/player?course=asp-net-mvc5-web-apps&author=scott-allen&name=45d18322-a58d-4aac-847b-3ccdf67b8437&clip=0

ASP.NET MVC 5 Fundamentals
    ASP.NET 4.x include ASP.NET MVC 5
    
1 Course Overview
    
2 Creating a new ASP.NET MVC Application
        Creating a New ASP.NET MVC Application
        
        Creating a Blank Solution
            select "Blank Solution"
            
        Adding a Starting ASP.NET MVC Project
            add new project of type:
                ASP.NET  Web Application (.NET Framework)
                Select MVC
                Select 'Configure for HTTPS 
                build and run no debug

        Adding a Data Project   
            add a class library OdeToFood.Data
            delete the class1

        Adding a Model Restaurant
            adding classing that define the shape of the data
                Categories of classes
                    Restaurant class
                    class to represent services and component used to access data
                Namespaces for each category
                    add folder 'Models' for category types
                        represents business or domain objects
                    add class to represent a restaurant, make public 
                    add attributes and states as properties
                    add enum for types of Cuisines

        Adding an In-Memory Data Source
            add an abstaction that will simulate a SQL db
            add new folder Services to OdeToFood.Data project
            add new interface to Services folder
            make public and define operations
            add a IEnumerable
            add public class InMemoryRestaurantData : IRestaurantData
            implement interface ctrl-. Implement Interface
            use ctrl-. Move type to its own implementation file
            do implementation

        Respoinding to HTTP Message from a Controller
            cshtml is a razor view
            the controller is responsible for building a model
            
        Building the 
            create IrestaurantData db in controller
            add constructor to make a db instance
            in Index() get data 
                var model=db.GetAll90;
            MVC framework will render default or Home.index.cshtml view
            
        Rendering the Model 
            the '@' will transition the Razor engine from html markup model 
                to C# mode
             using @ can access properties that are part of the view object
                One property is Model
            use a Razor a Model directive '@' to tell Model has to be a IEnumberable
                of Restaurant
     
3 Application Startup and Configuration
    Understanding APS.NET Hosting
        many file types
            configuration files
            .cs file containing C# source code
            script files in Scripts folder
            images
            CSS style sheets
            CSS frameworks like Bootstrap
        Primary output is an assembley OdeToFod.Web.dll
        Web Server VS uses is either IIS or IIS Express
        
    Staring up an ASP.NET Application   
        On startup Global.asax.cs contains the Application_Start()
            Contains all code used at Startup exists in the App_Start folder
    
    Defining Routes for ASP.NET
        mapping an incoming URL or 'routing'
        tells ASP.NET how to process and map URLs to components
            contain C# or Razor code
        MapRoute api
            Maps Url to controller and action which have defaults
            Add a new controller
            
    Configuring ASP.NET with web.config
        can add custom <appSetting>
        make use of the custom appsetting in the controller
        a model will be used so add a new model 
            right-click the model folder, add->new item
            add property to the new model
            all data for the View will be provided by the controller
            in controller ActionResult Index() instantiate a new xxxModel()
            pass model to view
            in view can access model passed to vew
            strongly type Model using a directive 
                @model OdeToFood.Web.Models.GettingViewModel
                
    Install Autofac for Dependency Injection;
        Inversion of control container
        right-click on reference of OdeToFod.Web->Manage NuGet Packages
        search for Autofac.Mvc5
        
    Configuring the Autofac Inversion of Controller Container
        add another .config file file into the App_Start folder
        add class and change namespace to OdeToFood.Web
        add ContainConfig.RegisterContainer() to Global.asax.cs Application_Start()
        add the builder stuff
        
    Understanding MVC Controllers
    
4 Understanding the MVC Design Pattern
    Appling the MVC Design Pattern
        MVC Design Pattern encourages a separation of concerns
            Don't handle too many problems at one time.
        Single Responsibliity Principle 
        Model View Controller
            Controller  Model   View
            Get /restaurants
                Controller is the written
                configure routing to the C# restaurant controller
                ctlr builds Model, does not render or display html
                ctlr selects a view or render a view
                view produces html to render back to the browser 
            
    Working with Query strings
        allows to pass a piece of state along with the request
            https://locahost/greeting?name=Scott
            name can be accessed in the HttpContext property
                httpContext.Request.QueryString["name"]  don't use this
                pass a parameter to Index(string name)
                
    Understanding MVC and API Controllers
        two types of controllers
            1. responds to a http request to build a model and return ing a view
            2. Web API controller to build APIs to return json or xml. 
                add new folder called Api
                add new Scaffolded Item
                select Web API 2 Controller - Empty
                add items in result message
                add http method "Get" to RestaurantsController
            Route: "api/{controller}/{id}
            Verbs for api are: Get, Post, Put and Delete
            
    Installing and configuring Web API
        add to RestarantsController ctor, private db var for injection 
        in Get() add var model = GetAll(); return model;
        this will return the json of the model
        install via nuget AutoFacWebApi2 module
        in ContainerConfig.cs add RegisterApi Controllers
        
        using curl can specify json or xml:
            curl https://localhost:44371/api/restaurants -H "Accept: application/xml"
            
    Building a Restaurant API
        add MVC 5 Controller -Empty, name it RestaurantsController
        to add a menu item to Restaurants goto Views/Shared/_Layout.cshtml
        int the nav div navbar-collapse  add another <li> with 
            @Html.ActionLink(linkText, ActionName, controllerName)
            
    Scaffolding a RestaurantList
        in the RestaurantsController class build a model including all
        the restaurants
            add ctor to RestaurantsController w/IRestaurantData db as parameter
            in Index right click and add view 
            
    Scaffolding restaurant Details
    
    Working with Action Results
    
Using MVC Models
    Understanding Models and View Models
        Model - Not necessarily a View model. But an entity.
        View Models - a Model or Class you create whose only purpose is 
        encapsulate all the information to render a view. A view model may have more infornation than an entity.
        
    Setting up a Create View
    
    Working with Enums
        use the @Html Enum helper @Html.EnumDropDownListFor(...)
        
    Implementing the Create Action
        to RestaurantsController add a ActionResult Create method
            add the [HttpPost] and [ValidateAntiForgeryToken] attributes
    
    Validating Models and Model State
        use ModelState
        
    Validating Models with Data Annotations
        using System.ComponentModel.DataAnnotations;
        
    Following the POST-Redirect-GET Pattern
         in controller add return RedirectToAction("Details");
         
    Implementing tha Edit Action
    
Using Entity Framework in MVC Applications
    Introducing the Entity Framework
        
        
               
        
    
         
        
        
        
        
            
             
                     
        
            
    
    Application Startup and Configuration
    
    Understanding MVC Controllers
    
    Using MVC Models
    
    Using Entity Framework in MVC Applications
    
    Razor Views
    
    Front End Frameworks
    
    Deploying ASP.NET MVC Applications