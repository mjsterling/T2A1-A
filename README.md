# T2A1-A Workbook - Matthew Sterling

<!-- TOC -->
- [Q1 - Rails Application Architecture](#q1---rails-application-architecture)
- [Q2 - Database Management System](#q2---database-management-system)
    - [Pros](#pros)
    - [Cons](#cons)
- [Q3 - Agile Project Management Implementation](#q3---agile-project-management-implementation)
- [Q4 - Source Control Workflow](#q4---source-control-workflow)
- [Q5 - Software Testing Process](#q5---software-testing-process)
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

## Q3 - Agile Project Management Implementation

Agile is a set of guiding principles for efficient and effective project management. As laid out in the Agile Manifesto<sup>1</sup>, its primary tenets lie in the prioritisation and valuation of:
- "Individuals and interactions over processes and tools";
- "Working software over comprehensive documentation";
- "Customer collaboration over contract negotiation"; and
- "Responding to change over following a plan".

Businesses adopt Agile primarily by implementing a change in management style that requires managers to abandon the traditional methods of micromanagement and specific task delegation in favour of instead empowering their teams to make operational decisions, by delegating high-level objectives only and stepping in only to remove roadblocks or clarify direction.

Agile development is often operated within the Scrum framework, a system which attempts to decrease the time between planning and deployment by breaking software development down into multiple shorter timeblocks called "sprints". in sprints, features of the software are developed in their entirety within a set period, with the goal of creating a Minimum Viable Product that can be potentially deployed to customers in the shortest amount of time, allowing teams to then add more features and iteratively improve the product while it is in use instead of one immutable product at the end of a project.

Agile and Scrum came about as a solution to a number of endemic problems with the older industry standard of "waterfall" development methodology, which required each phase of an application's development to be entirely complete prior to commencing the next, which across a lengthy project timeframe of months or years often resulted in a finished product being obsolete by the time it was released. Agile and Scrum, together emphasising the importance of working closely with the customer to fulfil their needs and of iteratively developing and delivering software that can be more closely fit to their needs, allow development teams to both keep up with the breakneck rate of change of the tech industry in the modern era, and to make better products faster.

## Q4 - Source Control Workflow

Source control is a system for allowing changes to a project with multiple contributors to be easily tracked, merged and reverted, by storing snapshots of different versions of the project's source code files within special folders called repositories. Source control in the software industry is often implemented using a tool called Git, an example workflow of which is provided below:

1. Begin work by initiating a new project with `git init` if a repository does not exist, or cloning an existing repository with `git clone`. Initiating a new repository will enable the tracking of files within that folder; while cloning a repository will download a snapshot of the latest version of a particular project from a hosting server, such as Github or Bitbucket, to a local machine to be worked on.

1. When cloning a repository, any new features that are being worked on will often be done in a different branch of the repository using the `git checkout` command to avoid potential bugs and issues with the main body of the application.

1. Work on the project by making modifications, additions or deletions to files within the project.

1. Once a significant enough amount of work has been done and changes are ready to be added, the user can run `git status` to ensure that all file changes are intended and no accidental file modification has occurred.

1. Once satisfied with the status of the changes, running `git add` will allow the user to add their selected changes to the "staging area".

1. After all desired files are added to the staging area, users may run `git commit` to save a snapshot of their modifications to the repository.

1. If work has been completed in a different branch, a *pull request* may be initiated to merge these changes back into the main branch.

1. The above steps are then repeated until the conclusion of the project.

## Q5 - Software Testing Process

Software testing is the process of performing specific operational tasks on an application in development, which can be done by manually operating the application as a user, or by using scripted testing libraries such as RSpec, Mocha or Selenium.

In manual testing, software testers will:

1. First assess the testing requirements of the application in line with standards and specifications set by the application's documentation;
1. Create a comprehensive "test plan" containing a series of unique test cases designed to assess whether or not the application is operating as expected;
1. Run each of the tests in this plan on the application and document any discrepancies between actual and expected results;
1. Report any bugs to the development team, and re-run the specific tests once any fixes have been applied.

Manual testing is usually executed in stages of increasing complexity in order to easily identify where errors are occurring:

1. *Unit testing* is the most basic level and is done first - ensuring that the smallest discrete pieces of code, such as UI components, are functioning as intended;
2. Next, *integration testing* combines these individual components to ensure they are working cohesively;
3. *System testing* takes this one step further by checking whether all of the integrated parts of the application are working together as intended;
4. Finally, *acceptance testing* is performed to see if the application is suitable for its intended use case in a deployed environment.

## Q6 - System Security Requirements

Information security is an important focus for any online business, however for  e-commerce enterprises it is absolutely critical that appropriate security measures are implemented due to their propensity to be targeted by cybercriminals. By nature of the significant amounts of sensitive personal and financial data that must be stored by online marketplaces, these requirements are: 

- *Encryption and authentication* - personal identities and credit card details must be sent over an encrypted protocol that is protected from unauthorised access and indecipherable even if intercepted;

- *Integrity and irrepudiability* - unmodified records of transactions must be stored on the server and accessible when required to ensure that parties to a transaction cannot deny sending or receiving goods or payments, and that the transaction records cannot be altered;

- *Operational protection* - sufficient systems must be in place to prevent attackers from disrupting the website's operation through Distributed Denial of Service and other similar attacks.

## Q7 - Data Protection Methods

- *User authentication* - ensuring users are who they say they are mitigates the ability of attackers to gain unauthorised access to data. For a marketplace application this is a mandatory requirement, and is usually executed in e-commerce with a simple password login, however this system often proves insufficient due to human fallibility and so I would strongly recommend a two-factor authentication system using the user's smartphone with Google Authenticator or equivalent, biometric verification, or an SMS code to limit fraud.

- *Data protection* - appropriate data server security such as firewalls, hasing algorithms and DDoS protection services such as offered by Cloudflare would be required for the project, as well as use of SSL encryption (HTTPS) to prevent sensitive information from being stolen while being transmitted to the server.

- *Website authenticity* - to prevent users falling victim to phishing and other similar attacks, a security certificate/digital signature system, along with a unique and easily recognisable URL would be applied to the project so that users may verify they are communicating with the true application.

## Q8 - 

# References

1. http://agilemanifesto.org/

