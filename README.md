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
