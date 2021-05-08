# T2A1-A Workbook - Matthew Sterling

<!-- TOC -->
- [Q1 - Rails Application Architecture](#q1---rails-application-architecture)
- [Q2 - Database Management System](#q2---database-management-system)
    - [**Pros**](#pros)
<!-- /TOC -->


## Q1 - Rails Application Architecture

Rails is a Ruby language framework designed to ease and facilitate the creation of applications and APIs for use cases that require server-side logic, data security and database interaction. As an opinionated framework with an emphasis on "convention over configuration", Rails forces developers to create applications using the **Model/View/Controller (MVC) pattern**. The MVC system allows developers to separate concerns, minimise potential software errors, more easily manage large enterprise applications and adhere to DRY (**D**on't **R**epeat **Y**ourself) coding standards.

Rails applications are executed as a web server that can receive and process HTTP requests from a web browser when accessed via the appropriate IP address and port number, using the MVC system to interact with the user.

The MVC system consists of Models, Views, and Controllers, each serving a specific, discrete purpose to contribute to the function of an application.

- **Models** serve as the backbone of the application; they are the link between the application's code and its database management system. Models contain methods for the creation and manipulation of database records; they are named in the singular, and Rails models will automatically interact with a database table with a name that is the plural form of the model name.

- **Views** contain templates for the information that will be displayed to the user in a web browser. In Rails-only applications they are usually written in **ERB (Embedded Ruby)**, a templating language that allows Ruby to be embedded within HTML code, facilitating dynamic input and output of data when a user interacts with the application.

- **Controllers** are the link between models and views. Using paths outlined in the application's **routes**, which dictate the flow of the application and instruct controllers on which action to call, controllers handle HTTP requests *(GET, POST, CREATE, DELETE)* from specific URLs, and pass objects and variables between the view and the model.

These three discrete parts work together to create a specific flow of information: when an HTTP request is sent to the Rails server via a URL, Rails will check its routes file and call the corresponding method from a controller, which will then interact with methods in the required model. The model will fetch or manipulate data in the database as instructed and pass an object back to the controller, which in turn will forward the object to a view; the view will fetch any assets required (such as CSS files or media files) and then send the information to be rendered to the user's web browser.

## Q2 - Database Management System

A commonly used database management system in Rails and other web framework applications is MongoDB. MongoDB is a document-based NoSQL database, however its design relatively unique as a DBMS in that its design seeks to combine the best features from both traditional SQL-based relational databases and NoSQL databases.


### Pros

-----
- *Scalability* - in contrast to relational databases, MongoDB has high horizontal scalability and is designed to have multiple failure points, allowing for seamless expansion of the database's capability.

- *Flexibility* - unlike the concrete schemata of relational databases, MongoDB allows the structure of existing documents to be live-altered to keep up with the changing needs of an agile business, allowing MongoDB databases to be built and scaled in a modular fashion rather than the traditional requirement of a huge amount of forethought, planning and redundancy implementation.

- *Ease of use* - MongoDB stores data in BSON (Binary JavaScript Object Notation), which especially when working with JavaScript allows developers to interact with the database in a very simple and intuitive way, as information is handled by both the application and database in virtually the same format.

### Cons
-----

- *Availability* - distributed database systems such as MongoDB suffer from endemic problems by nature as described by the CAP theorem (*any distributed system can only provide two of the following: <u>C</u>onsistency, <u>A</u>vailability, and <u>P</u>artition Tolerance*). In pursuit of replicability and data integrity, MongoDB's design sacrifices availability: each copy of the database may only have one primary node which handles all write requests, and if this primary node fails the other nodes must go through a process of electing a new primary node, during which time the database is not able to receive write requests at all.

- *No schema* - the schematic flexibility that allows MongoDB database managers to alter their databases so freely can also cause issues when accessing data. MongoDB does not enforce the same structure for each document in a collection, which can require a great deal of error handling for when an application successfully fetches a document and then is unable to find a specific key-value pair within it.

- *High memory usage* - owing to their requirement of high data redundancy and their need to explicitly store the key name in each key-value pair in every document, MongoDB databases can become very large very quickly.

## Q3 - Agile Project Management Methodology

