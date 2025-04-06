# Research and Reflection Journal
## WEEK 8 - FUNCTIONAL USER REQUIREMENTS

User stories allow developers to understand the needs of users, even if they are not the final recipients of the software. A user story is a brief statement from the user's perspective, beginning with "As a user..." and detailing what the user expects from the software in a specific situation. They enable developers to put themselves in the users' shoes and define clear specifications for software features, especially when complemented by user feedback through focus groups.

User stories guide the definition of functional requirements, which are precise technical specifications of the application's features. These requirements serve as the basis for developing 
a complete technical specification.

### RESEARCH A NEW LANGUAGE - Lua

The Lua programming language is especially used in the video game industry and many video games use Lua as a scripting language. Lua is often used in game engines to keep game settings and characters separate, thus making the game engine more flexible and allowing different games to use the same engine.
Another major application area for Lua is network and systems programming. Lua is used to configure and automate programs. Well-known examples are VLC Media Player or Adobe Photoshop Lightroom. In terms of networks, network analyzers such as Wireshark use Lua functions.

### WRITE A USER STORY

Youtube App

User Stories:

- As a user, I can search for videos using a search bar.
- As a user, I can subscribe to channels to receive updates on new content.
- As a user, I can like or dislike videos to express my opinion.
- As a user, I can create and manage playlists to organize my favorite videos.
- As a user, I can comment on videos to share my thoughts with others.

Acceptance Criteria:

- A ‘Subscribe’ button is visible on each channel page.
- Clicking the ‘Subscribe’ button adds the channel to the user's subscription list.
- The ‘Subscribe’ button changes to ‘Subscribed’ after clicking.
- New videos from subscribed channels appear in the user's subscription feed.

### CHOOSE A LANGUAGE FOR YOUR APP DEVELOPMENT PROJECT CODE

We decided to use Python along with a framework, which in this case will be Django, because I personally have experience working with Python and databases, it is easy for me to connect both parts Front With Back.  Our app will be about managing routines that users do at the gym and also managing issues related to gym management.

### STAR GITHUB TOPICS AND REPOSITORIES OF INTEREST

I found it very interesting that there are sections where there are projects that are too big and some that are popular, although I don't really know how you can contribute to them, I find it interesting to understand how GitHub works, how these projects work and how people contribute to them, Boostrap is one of the most popular frameworks and I found it in the collections section.

![image](https://github.com/user-attachments/assets/78405b4c-d7f6-4c6c-b11f-f15d81f3fd07)


### FOLLOW-UP QUESTIONS AND REFLECTIONS

What is one interesting thing that you’ve learned from researching about programming languages and from reading other students’ posting about programming languages in response to the first activity?
- I didn't know about Lua and I think that language is the best option for add or mod a videogame without touching the game logic in the direct code, I really like videogames and for me could be a great way to learn something different related with videogames and coding. 

What other programming languages might you consider to work with for DGL 104? What are your second choices, and why?
- Could be JavaScript because I heard from some students that they know little bit of java and javascript and could be a great backup just in case.

What did you find most interesting when examining repositories on GitHub? Is there anything that surprised you, or that you didn’t expect? What similarities are there across some of the repositories you’ve starred?
- I didn't expect that, for example, Bootstrap was on GitHub, although I'm not very sure what can be done with it, it's a good idea to explore it at the project and code level.


-----------

## WEEK 9 - DESIGN PATTERNS

### RESEARCH ON DESIGN PATTERNS

__SINGLETON IN JAVA__
- Ensure that a class has only one instance throughout the lifecycle of the application.
- Provide a global point of access to that instance.
- Control resource usage by preventing unnecessary object creation.

__Real-World Applications__
- Database connections: Maintain a single connection to the database to avoid conflicts and save resources.
- Logging: Ensure that all logs are handled by a single logging object.
- Configuration Management: Store configuration settings in a single object to prevent inconsistency.
- Thread Pools: Manage resources efficiently by using a single thread pool manager.


**Example (Logging System)**

Imagine you want to log messages to a file. Using a Singleton ensures that the log file is managed by a single instance, preventing conflicts from multiple objects trying to write at once:

```java
public class Logger {
    private static Logger instance;

    private Logger() {}

    public static Logger getInstance() {
        if (instance == null) {
            instance = new Logger();
        }
        return instance;
    }

    public void log(String message) {
        System.out.println("Log: " + message);
    }
}

public class Main {
    public static void main(String[] args) {
        Logger logger = Logger.getInstance();
        logger.log("Application started");
    }
}
```

__OBSERVER IN JAVA__
- Establish a one-to-many relationship between objects.
- When the state of one object (subject) changes, all dependent objects (observers) are automatically notified and updated.
- Promotes loose coupling between objects.

__Real-World Applications__
- Event handling in GUI frameworks – Button clicks, text input changes, etc.
- Stock Market systems – Notify investors when stock prices change.
- Social Media notifications – Notify followers when a user posts a new update.
- Newsletters – When a new article is published, subscribers are notified.

**Example (Stock Price Tracker)**

A stock market app where multiple users (observers) are notified when the stock price changes

`Subject (Stock)`

```java
import java.util.ArrayList;
import java.util.List;

class Stock {
    private List<Observer> observers = new ArrayList<>();
    private double price;

    public void attach(Observer observer) {
        observers.add(observer);
    }

    public void setPrice(double price) {
        this.price = price;
        notifyObservers();
    }

    private void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(price);
        }
    }
}
```

`Observer (Investor)`

```java
interface Observer {
    void update(double price);
}

class Investor implements Observer {
    private String name;

    public Investor(String name) {
        this.name = name;
    }

    @Override
    public void update(double price) {
        System.out.println(name + " notified: New stock price = $" + price);
    }
}
```

`Usage`

```java
public class Main {
    public static void main(String[] args) {
        Stock stock = new Stock();

        Investor investor1 = new Investor("Investor 1");
        Investor investor2 = new Investor("Investor 2");

        stock.attach(investor1);
        stock.attach(investor2);

        stock.setPrice(100.50);
        stock.setPrice(105.75);
    }
}
```

### SUMMARY “HOW TO CONTRIBUTE TO OPEN SOURCE”

The article explains in detail how to contribute to open source projects and why it can be beneficial for you and the community. First, clarify what open source is (software that anyone can view, modify, and distribute) and that contributing doesn't just involve writing code, but also improving documentation, fixing bugs, translating, helping others, and designing interfaces.

It also suggests ways to get started: choosing projects that interest you, reviewing the documentation and open issues, and exploring how work is organized within the project. It recommends starting with small tasks, such as fixing minor bugs or improving documentation, to gain experience and familiarize yourself with the community.

Finally, the article explains best practices for contributing effectively. It's important to follow project rules, communicate respectfully, propose clear changes, and openly accept feedback. It also mentions that contributing to open source is an opportunity to improve your technical skills, expand your professional network, and be part of a global community.

### WRITE A SUMMARY ON SLACK

I think the first step before contributing would be to understand the function of the project, that is, what its purpose is, by reading the documentation and understanding a little about how it is built. In this way, we can say that at a certain point we will do a code review to see if we can contribute something.

In this case, I saw one called "ERPNext."
It's an open-source enterprise resource planning (ERP) system that allows companies to manage and automate key processes such as sales, purchasing, inventory, accounting, human resources, production, and more. It's built on the Frappe framework (also open-source), allowing for high customization and ease of development.

In this case you can contribute to one of the issues

Issue #26136 mentions a 404 error in the `get_item_tax_info` method.

This could be caused by:

- An error in the method path
- A permissions or authentication issue
- Incorrect environment configuration

### FOLLOW-UP QUESTIONS AND REFLECTIONS

Is the programming language that you chose last week still the right choice? Should you consider alternatives?
- Yes I think those choices are the best for developing the kind of app that is required, in this way I can work in backend and my team in front end

What is your plan to develop your application? Have you started creating a tentative timeline to meet the deadline?
- We are going to design as a first step the mockups to know all the screens that our app is going to have then to develop in html and css all the required pages and finally conect them to the backend

-----------

## WEEK 10 - MV* PATTERNS

### MV* OVERVIEW

MV* (Model-View-Controller) patterns form a family of architectural patterns which do provide a clear, modular structure to assist with application development, especially in both web and also mobile environments. The asterisk () in MV* represents different variants. These include MVC, MVVM, and also MVP. The main objective for each of these patterns is to separate concerns in the application, which can promote better maintainability, scalability, and also testability in its codebase. Unlike usual design patterns such as Singleton or Observer, which solve certain object-oriented programming problems, MV* patterns take care of the general organization of a software project. This makes them vital tools for managing complexity in large-scale applications, where it is critical to clearly separate business logic, presentation logic, and the user interface.

#### Example – Web Application Using MVP (Model-View-Presenter):

In a JavaScript-based web app, using the MVP pattern, the Presenter handles user input and updates both the Model and the View. For example, in a task management app, the Presenter would take input from a form (e.g., a new task), update the task list in the Model, and then tell the View to refresh the task display.

### MVC & MVVM

MVC (Model-View-Controller) as well as MVVM (Model-View-ViewModel) are two of the most widely used architectural patterns within the MV* family. MVC divides one application into three parts that are key: Model, which does data and logic that's business; View, which shows the interface a user sees; and Controller, which is between the Model and View. This pattern is regularly used in web development frameworks such as Ruby on Rails. MVVM, on the other hand, has become the main pattern in current mobile development, notably with declarative UI frameworks, like SwiftUI for iOS and Jetpack Compose for Android. In MVVM, the ViewModel generally provides the data as well as actions needed by the View. This allows for automatic data binding, also creating a more reactive and decoupled user interface. The shift to MVVM reflects an emphasis that is growing on code that is modular and testable and on a separation that is clear between interface and logic that is business.

#### Example – MVVM in Android with Jetpack Compose:

An Android notes app using MVVM might include a ViewModel that holds a list of notes and exposes functions to add or delete them. The UI (View), built with Jetpack Compose, observes the ViewModel, automatically updating when the data changes, without directly interacting with the underlying Model.

### Community Code Processes

They offer real-world experience while building skills. Open-source coding is a valuable community opportunity for collaborative development. A typical workflow within these environments starts through forking one repository—creating a personal copy of one existing project upon platforms such as GitHub. From there, it is a best practice to create a new branch on which you could develop features or fix bugs without affecting the main project. Contributors can be able to explore all of the issues section in a repository, where maintainers do document all known bugs or needed features. Working upon these same issues lets you all contribute well to the project. Once through you’ve made your changes, you can open a pull request, which is a proposal for to merge your updates into the main codebase. This process with supports peer review, collaborative learning, and continuous improvement of the software—a necessary workflow in today’s professional development practices.

#### Example  – Forking and Contributing to a CSS Framework:

A student forks an open-source CSS library from GitHub to improve accessibility features. They create a new branch, add keyboard navigation support for dropdown menus, and submit a pull request. The maintainers review the code and merge it into the main repository, crediting the contributor.

### ASSESS EXTERNAL COMMUNITY CONTRIBUTION GUIDELINES

To contribute into the open-source project `H2O Wave`, I first reviewed into its official documentation, including the `CONTRIBUTING.md` and `CODE_OF_CONDUCT.md files`. The guide outlines setup steps to build the project, including cloning repository, installing dependencies via Yarn, building project, and running tests. A number of contributors are expected to then follow the code formatting rules via the make format command prior to changes. Contributions get made through `pull requests`. **Opening a PR requires changes passing tests.**

The `CODE_OF_CONDUCT.md` establishes within it expectations for a respectful, inclusive, and harassment-free community. Contributors are encouraged to act with empathy, as well as respect toward others, plus professionalism. Harassment or discriminatory comments are inappropriate behavior. Consequences, from warning to ban, can result from it.

After exploring the repository, I identified many open issues that are potential opportunities for contribution. A key issue that stood out involves the improving of user experience by adding in error messages to each UI function with required parameters. This should help developers using the framework identify problems sooner and write reliable applications. Another promising issue proposes enabling both row as well as column data to be accessible upon clicking at a table cell, which would improve interactivity for dashboards and data apps. These issues are well-defined as well as approachable, making them ideal starting points for contribution to the project.

Prior to beginning work upon any of these issues, I would first comment within the GitHub issue in order to indicate my interest in contributing and to ensure that no one else is already working upon it. By really following the established community and technical guidelines, I aim to then make some meaningful and quite respectful contribution to just the H2O Wave project.

### FOLLOW-UP QUESTIONS AND REFLECTIONS

I think the biggest challenge this week is definitely having to work on my project while also working on an external project and figuring out how I can contribute. But I think the best thing I could do was use AI to search for a repository that is designed in the same programming languages ​​that I already know, this way even if I don't have much time to participate in that project I can learn on my own what it's like to work in a open source project.

-----------

## WEEK 11 - OBJECT ORIENTED PROGRAMMING

### Key Principles of OOP

**Encapsulation:**

- Encapsulation refers to the bundling of data (attributes) and methods (functions) that operate on the data into a single unit called a class. It hides the internal state of an object from the outside world and only exposes essential functionality.

- This is achieved through the use of access modifiers (e.g., private, protected, and public) that control the visibility of data. For example, sensitive data such as passwords are kept private within an object, and methods are provided to access or modify that data in a controlled way.

- Encapsulation helps prevent unauthorized access to object data and ensures that objects are used only in the intended way, which makes the system more secure and reliable.

**Abstraction:**

- Abstraction allows developers to hide complex implementation details and expose only essential features of an object. Instead of focusing on how an object works, abstraction allows users to focus on what it does.

- This principle simplifies system complexity by hiding unnecessary details, making it easier for developers to interact with objects and understand their purpose without needing to know the intricate workings behind them.

- For example, when using a car class, you don’t need to know how the engine works; you just need to know how to start the car, accelerate, and stop. The engine's internal mechanics are abstracted away.

**Inheritance:**

- Inheritance is the mechanism that allows a new class to inherit attributes and methods from an existing class. The new class is known as a subclass (or child class), and the existing class is called the superclass (or parent class).

- Inheritance promotes code reuse and establishes a natural hierarchy between classes. For example, a `Car` class can inherit properties and methods from a `Vehicle class`, which might include general attributes such as `color`, `make`, and `model`.

- This enables developers to create specialized versions of a general class without rewriting code. For example, `ElectricCa`r and `SportsCar` can inherit from `Car`, each adding their unique features.

**Polymorphism:**

- Polymorphism allows objects of different types to be treated as objects of a common type. Specifically, it allows a single method to behave differently depending on the object calling it.

- This is usually achieved through method overriding or method overloading. Method overriding occurs when a subclass provides a specific implementation of a method that is already defined in its superclass, while method overloading allows a method to have multiple definitions with different parameters.

- Polymorphism simplifies code by enabling the use of the same method name for objects of different types, increasing flexibility and reducing the complexity of the codebase.

### Advantages of Using OOP

**Modularity:** OOP helps break down a large project into smaller, manageable parts (objects). Each object encapsulates a specific behavior and state, which makes it easier to work on different parts of the system independently.

**Reusability:** Once an object or class is created, it can be reused in other parts of the project or in different projects. This is particularly useful in large projects or in scenarios where certain functionalities need to be repeated.

**Scalability:** Since OOP promotes modular design through the use of objects and classes, it allows the codebase to scale easily. Adding new features or modifying existing ones can be done without drastically changing the entire system.

**Maintainability:** With OOP, the code is easier to maintain because it is organized into logical structures. Each object has well-defined responsibilities, and changes made to one object are less likely to affect others. Additionally, OOP makes it easier to test and debug individual components of the system.

**Flexibility:** OOP allows for extensibility through inheritance and dynamic behavior through polymorphism. This flexibility makes it easier to adjust and update the system as new requirements arise.

### Applying OOP in a Group Project

In our group project, which is a gym management application, OOP principles are essential to ensure that our application is scalable, maintainable, and modular. Here’s how we apply OOP concepts:

**Encapsulation:**

We define models like `User`, `Trainer`, `Client`, and `Session` in Django, where each model encapsulates specific data related to the user (e.g., name, email, etc.), trainer (e.g., assigned clients, training schedule), and session (e.g., date, time, type of session).

We make use of private and public methods in each model to control how data is accessed or updated. For example, only the admin or the trainer can modify a client's training sessions.

**Abstraction:**

We abstract the complexity of session management and user role handling. For instance, the admin class abstracts the logic of managing all users, while the trainer class abstracts the logic related to managing their assigned clients and sessions.

Instead of manually managing every user or session, each class provides simple methods like `add_user()`, `get_clients()`, `schedule_session()`, etc., which handle all the necessary logic internally.

**Inheritance:**

We use inheritance in Django to extend the built-in `User model` for creating custom user roles such as `Admin`, `Trainer`, and `Client`. Each of these roles inherits from the `User model` but adds specific attributes and behaviors tailored to the role.

This allows us to reuse the general user model for common functionalities like `login`, `registration`, and `client management`, while extending it for more specific functionalities.

**Polymorphism:**

We use polymorphism to handle different types of users and sessions. For example, we can have a method like `view_dashboard()`, which behaves differently for an admin, a trainer, and a client, showing data relevant to each role.

Polymorphism allows the application to be dynamic and adapt to different user types with minimal code changes.

### FOLLOW-UP QUESTIONS AND REFLECTIONS

When determining whether a programming language seems capable of Object-Oriented Programming (OOP), we must first examine its support for the four core principles of OOP: Encapsulation, Abstraction, Inheritance, and Polymorphism. Let’s consider Python and JavaScript as examples to assess their OOP capabilities.

Python is truly a fully OOP-capable language. It supports from all four major principles of OOP. First, Encapsulation is achieved in Python by bundling data and methods jointly into classes, and it also provides a degree of control over data access, even if the enforcement of private attributes is not as strict as that in languages such as Java. For Abstraction, Python also supports abstract classes with the abc module, allowing developers to then define those abstract methods that must be implemented within subclasses. Python also fully supports Inheritance, enabling subclasses to inherit properties as well as methods from parent classes, which eases code reuse plus organization. Lastly, Polymorphism is supported in Python through method overriding, enabling subclasses to provide differing implementations of methods defined in parent classes. Therefore, Python now fully supports OOP, and everything in Python is treated as of an object, allowing developers to model to real-world entities effectively.

In addition to OOP, Python is also a multi-paradigmatic language, meaning that it supports multiple programming models. While Python is object-oriented, it also allows for Procedural Programming, in which you can write code by use of functions with procedures. Also, Python gives good backing for Functional Programming; that includes aspects such as first-class functions, lambdas, and higher-order functions. These features do allow developers to approach to problems by using different styles depending on the task at hand.

JavaScript, however, supports OOP also, but it uses a more flexible approach based on prototypes, rather than classical inheritance seen in languages like Java or Python. JavaScript allows for Encapsulation by way of objects as well as closures, in which private data can be kept inside of functions. JavaScript doesn’t quite have customary abstract classes themselves. Abstraction can still be achieved through custom code patterns and via interfaces. JavaScript inheritance differs from classical OOP; it uses prototype-based inheritance, meaning objects inherit straight from other objects rather than from predefined classes. This approach gives developers quite a dynamic way to manage inheritance. JavaScript supports Polymorphism, in which methods are often overridden. Subclasses use this to offer more functionality.

Although JavaScript is capable of OOP, it is deemed a limited implementation of standard OOP principles due to its prototype-based nature. Nevertheless, JavaScript is also a multi-paradigmatic language, much like Python. It supports not just OOP but also the Event-driven Programming, in particular, in web development since event handling is important for user interactions. Additionally, JavaScript embraces Functional Programming, offering several features, like higher-order functions, closures, and lambda functions. JavaScript can also be used in an Imperative Programming style. In that style, the programmer defines steps in sequence to achieve a result.

Ultimately, Python is a total OOP-ready language that backs all four OOP tenets, making it a fine pick for object-oriented software creation. It is also multi-paradigmatic in nature. This allows developers to choose between OOP, functional, or procedural approaches based on the task at hand. JavaScript, while supporting some OOP principles, uses a prototype-based inheritance model, which is somewhat different from the classical OOP approach. JavaScript is also multi-paradigmatic and supports from a variety of models such as functional, event-driven, and imperative programming, offering to developers flexibility in how they write their code.

-------
## WEEK 12 - FUNCTIONAL PROGRAMMING

Functional programming (FP) has gained significant popularity in recent years, and it's no longer confined to academic research. Initially considered a tool for academic settings, functional programming is now being increasingly adopted in web and mobile app development. While functional programming languages themselves are used in some cases, the focus today is more on functional tools that can be used within modern programming languages to enhance development processes.

In this class, the emphasis is on using functional-style APIs, which are typically designed for manipulating collections such as arrays or lists. These APIs often provide methods like map, filter, and reduce, which can greatly simplify and improve the efficiency of your code. Many modern programming languages, such as Java, Kotlin, Swift, and JavaScript, include these types of methods as part of their standard libraries.

The key benefit of using these functional methods is the conciseness and beauty they bring to your code. Instead of relying on traditional imperative-style loops (such as for or while loops), these methods allow you to express your logic in a much more compact and declarative way. This makes your code not only shorter but also easier to understand and maintain.

For example:

map transforms each element in a collection based on a provided function.

filter selects elements from a collection that satisfy a given condition.

reduce aggregates all the elements in a collection to produce a single value, like summing all the numbers in an array.

By adopting these functional methods, you can make your code more efficient, readable, and expressive, embracing the power of functional programming in a way that is both accessible and practical for modern development.

In summary, functional programming has moved beyond its academic roots and is now widely adopted in practical programming environments. Even if you're not using a purely functional language, leveraging functional tools like map, filter, and reduce in your code can significantly enhance the quality and efficiency of your development work.
