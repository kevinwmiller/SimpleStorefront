# My Simple Storefront
--------------------
The goal of this training project is to provide a very basic storefront layout for someone selling something.
The project has been scaffolded using Symfony 3.0 and any additions should follow Symfony styles and standards.

## System Requirements:

1. Vagrant- https://www.vagrantup.com/docs/installation/
2. Git- https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

## Recommended Tools:

1. Zend Studio 13- http://www.zend.com/en/products/studio/downloads
2. Scipteden Bootstrap Builder- http://scripteden.com/builder/bootstrap/# (For quickly building sample templates)

## Some high level requirements are as follows:

* System should represent a simple business
* System should allow for Admin to log in in order to maintain the inventory and product recipes
* System should keep track of the business' current capital
* System should maintain prices for inventory bought and products sold
* System should allow guest users to buy products

## Instructions for running the project:

1. Start the vagrant box using the provided Vagrantfile: ``vagrant up``
2. After the vagrant box starts, ssh into it: ``vagrant ssh``
3. Inside the vagrant, cd into the SimpleStorefront: ``cd SimpleStorefront``
4. Inside the vagrant, run the install script: ``composer install``
5. Inside the vagrant, initialize the database: ``php bin/console doctrine:schema:update --force``
6. Inside the vagrant, load data fixtures: ``php bin/console doctrine:fixtures:load``
7. Open up a terminal to connect to the vagrant: http://192.168.33.10/
8. Attempt login with default credentials username: "admin", password: "password"

## Frontend Structure:

The frontend source files are contained in the ``src/NoInc/SimpleStorefront/ViewBundle/Resources/src/`` directory. Your vagrant should have a few utilities installed to make development a breeze. Upon intialization, the default and base frontend should be built an installed. As you work on the frontend, you will need to re-compile the views, styles and scripts. You can use the following steps to do so:

1. After the vagrant box starts, ssh into it: ``vagrant ssh``
2. Inside the vagrant, cd into the SimpleStorefront Viewbundle: ``cd SimpleStorefront/src/NoInc/SimpleStorefront/ViewBundle``
3. Use gulp to compile: ``gulp``
4. If you are actively developing, and wish to automatically recompile as you work, run: ``gulp watch --develop``

Running gulp with the command ``watch`` will cause gulp to continuously watch the frontend files for changes and recompile on the fly as you edit them (the process will not exit unless a major syntax error is present).
Running gulp with the ``--develop`` switch will prevent the javascript linter from cancelling the build upon errors.

All Javascript should be in the ``src/scripts`` folder, all views are written in Pug in ``src/views``, and styles in ``src/scss``:

* Javascript is written in ES6 and should conform to [the AirBnB Javascript styleguide](https://github.com/airbnb/javascript) with some modifications (see the .eslintrc file). The Javascript linter will fail the frontend build if the JS doesn't conform (use the --develop switch as noted above to see errors without needing to restart the build each time, or if you want to intentionally bypass the linter)
* Views are written in [HTML pre-processed language Pug](https://pugjs.org/language/attributes.html)
* Styles are written in [SCSS](http://sass-lang.com/documentation/file.SCSS_FOR_SASS_USERS.html)

If you are curious with how files are compiled, linked and placed, look at the ``gulpfile.js``, which powers most of the frontend build chain.

## This project is not finished!  

The following is a list of tasks that should be completed. They are in three levels, beginner, intermediate and advanced, and broken into frontend and backend components. You don't need to complete all the tasks define, but complete as many as you are comfortable and able to do. We are paying attention to completeness, code style, and architecture of your work.

### Beginner

#### Frontend challenges
* Add a header with a login/logout button
* Create an interface for viewing ingredients
* Create different interfaces for administrators and customers viewing the storefront
* Use AJAX calls to the API layer to display recipes and their ingredients.

#### Backend challenges
* Add another Recipe and list of Ingredients through data fixtures
* Check to make sure Ingredients are in Stock before making a Product

### Intermediate
#### Frontend challenges
* Add a UI library (such as Materialize, Bootstrap or Angular Material) and style all pages using this library
* Allow administrators to create and modify recipes using AJAX calls to the API layer.
* Allow administrators to buy ingredients using AJAX calls to the API layer.
* Make sure to implement front-end checks for quantities (i.e. if you have no sugar in stock, you can't make lemonade!)
* Add static product images (can be hard-coded image files)
* Create an admin dashboard to show sales and revenue (minimally, in a textual format)

#### Backend challenges
* ???

### Advanced
#### Frontend challenges
* Add a shopping cart/checkout interface
* Modify the admin dashboard to show graphical charts (using a charting library of your choosing)
* Create custom styles and design extending a UI library, or write your own UI without a library.
* Make sure the interface is WCAG 2.0 AA-level compliant [use the WAVE tool to help verify compliance](https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh?hl=en-US)
* Make sure the interface is mobile-friendly targeting screen sizes as small as an iPhone 5.
* Optionally, modify the frontend build chain to be more efficient.

#### Backend challenges
* Add in a shopping cart/checkout system
* Add in a CDN or Amazon S3 for image serving
* Add in managers for Ingredients and Recipes
