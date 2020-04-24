Overview: The main function of this application seems to be to provide a password protected login for users. 

*The config file contains a middleware    directory, a config.json file, and a passport.js file.

-The middleware directory contains a file called isAuthentication: This file exports a function that restricts user routes if user isn't logged in.  So, if the user is logged in they can proceed and if they aren't they will be redirected to the login page. 
-The config.json file contains configuration for three different database connections that will be used in the development, test, and production stages of the project.
-The passport.js file uses the passport npm to authenticate a password protected user login. 

*The models folder contains an index.js and a user.js
-The user.js file provides a sequelize model for a user that contains an email and a password.  It also uses the npm library bycrypt to perform validation for the user's hashed password and a hook that seems to be creating the password hash before the user is created.  I'm not sure exactly what lines 28&29 are doing. They seem to be using some kind of method specific to bycrypt?  The model and functions are all exported. 
-The index.js file connects with the config.json file, reads through it and sets up ways to connect to each of the different database connections (development, test and production). I'm not entirely clear on all the details here, including exactly what the filter is doing or why we have sequelize both upper and lower case?

*The Public directory contains a js directory, a stylesheets directory, and three html files.
-The three js files are "login, members, and signup," coordinating with the three html files by the same name.  The javascript files contain the functions that define various actions a user may take on the related page and what kinds of api calls may result.  For example, the loginUser function checks the "/api/login" route and sends the user to the members page if successful. 
-The css file adds a 50px margin to the top of the login form. 
-The html pages provide the html that displays the three pages for login, singup and members.  These files are connected to their corresponding js files and to ajax. 

*The routes directory contains an api-routes.js file and an html-routes.js file.  
-The api routes file calls the models directory and the config/passport file and creates crud routes for user login, logout, signup and user data.
-The html-routes.js file calls path and creates html routes about where to send the member based on different conditions.  It also uses the isAuthenticated middleware from the config file. 

*The package.json file contains the npm install information for the application. 

*The server.js file contains the many connections required to run the server and make the application work.  This includes bringing in express and other npm packages, including the required middleware.  It also sets up the PORT and the db as defined in the index.db file, and brings in the html and api routes.

  