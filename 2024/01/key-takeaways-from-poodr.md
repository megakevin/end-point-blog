---
author: "Kevin Campusano"
title: "Key Takeaways from Practical Object-Oriented Design by Sandi Metz"
date: 2024-01-22
tags:
- object oriented design
- ruby
---

[Practical Object-Oriented Design: An Agile Primer Using Ruby](https://www.poodr.com/) by [Sandi Metz](https://sandimetz.com/) is one of those books that everybody who writes or aspires to write object oriented code should read. Indeed, a read through this book will be of value for seasoned practicioners and inexperienced novices alike. Whether it be to discover new concepts, remember why they are important, or articulate the reasons behind that warm fuzzy feeling you get in your stomach when you read well designed code; POODR can help.

I personally really like this book. In fact, I like to dust it off every now and then to give it a re-read. To help with that, I've come up with a list of key takeaways from the book, with some of my own interpretations sprinkled in. For me, it serves as a sort of summary to help commit the book's contents to memory. I thought I'd share it with you today.

> While this book uses the Ruby language for its examples and discussions, the concepts it describes are equally applicable to any classical object oriented language. Dynamically typed language users do get a little more milleage than users of statically typed ones. But still, something like 90% of the content is relevant to both.

# Chapter 1: Object-Oriented Design

## About design

1. Following the principles and patterns of object oriented design produces code that is both cost-effective and a joy to work with. "Cost effective" means that it doesn't take more effort than necessary to evolve. To change.
2. The reason design is important is because software changes. A good design is one that makes software easy to change.
3. Object oriented design sees the world as a collection of parts that interact with each other. The parts, we call "objects", and the interactions, we call "messages".
4. In order to send messages to each other, objects need to have some knowledge about one another. This knowledge produce "dependencies" between them.
5. Managing these dependencies is a big part of object oriented design. OOD aims to create dependencies in such a way that they don't make the process of changing objects too difficult.
6. Design is important no matter the size of the application. Because both small and large applications change. And change is that design allows. A badly design small application will eventually become a badly designed large one.
7. Design is the way in which code is arranged. Good design is an arrangement of code that makes change easy.
8. Our job as developers is to take our application's requirements and our knowledge of design principles and use that to produce code that is cost effective today and tomorrow. Code that is easy to change.
9. The idea is not to predict future changes. Instead, we have to accept that change will come and prepare for it. We prepare for it by writing code that leaves our options open for the future.
10. "The purpose of design is to allow you to design later, and its primary goal is to reduce the cost of change".

## Failures of design

11. Design fails when you don't do it. Code bases that lack design will eventually evolve into unmaintainable messes. Change become increasingly hard even for the most minor new requirements. "Throwing everything away and beginning from scratch" becomes a viable alternative.
12. Design fails when you overdesign. Armed with basic design skills, it's easy to fall in the trap of developing wrong abstractions, applying principles incorrectly, seeing the wrong pattern in the wrong context. Applications that suffer from overdesign become gigantic castles of code full of indirection that become hard to change.
13. Design fails when you separate it from programming. Design is best executed as an iterative and incremental process with a quick feedback loop. The design needs to be adjusted frequently, as understanding of the domain changes. Design that is dictated to programmers from on high as part of a "[Big Up Front Design](https://en.wikipedia.org/wiki/Big_design_up_front)" are doomed to failure. Such arrangements are not agile enough to be resilient to requirement changes.

## Agile and design

14. Agile says: "Avoid Big Up Front Design because you can't know what the application will end up being because requirements always change and they do so often".
15. Agile also says: "Good design is essential. Because change comes often, your code needs to be ready to accomodate those changes in an efficient and cost effective way."
16. Design is not a "one time at the beginning of the project" type of task. It is an ongoing, iterative and incremental task that happens as requirements change, and our domain knowledge and skills increase.

## Metrics

17. Bad Object Oriented Design metrics are an indicator of a bad design. But good metrics are not an indicator of good design. A code base with bad metrics will most likely be hard to change.
18. The ideal software metric would be "cost per feature per time interval". But this is nigh on impossible to calculate because "cost", "feature" and "time interval" are in most cases nebulous concepts.
19. Still, "cost per feature per time interval" tells us that our goal should always be to write code with a low cost per feature. Making sure that it is also low cost to evolve in the future.

## Technical debt

20. "Technical debt" is borrowing time from the future. That is, putting out a bad design today in order to release a feature quickly. Tomorrow, when change comes, the bad design will prevent cost effective change. So time will have to be spent refactoring, turning the bad design into a good one. If refactoring doesn't happen, the debt increases, making future changes more and more expensive.
21. How much design to do depends on your skill and your timeframe. You can't do so much design that it prevents you from delivering on time. Design is an investment, and for an investment to be good, it needs to return some profit. Good design's returns are quick and plentiful.
22. "They trick to getting getting the most bang for your design buck is to acquire an understanding of the theories of design and to apply them appropriately, at the tight time, and in the right amounts".

# Chapter 2: Designing Classes with a Single Responsibility

## About classes

1. Classes are the most basic organizational structure of object oriented systems written with class-based object oriented languages. As such, that's the first thing that we focus on when designing such systems.
2. Your first insticnct should be to keep things simple. Use classes to model only the features that your application needs today and make sure that they are easy to change tomorrow.
3. "Design is more the art of preserving changeability than it is the act of achieving perfection".

## Write code that is TRUE

4. In order to be easy to change, code should be **TRUE**.
5. **Code should be "Transparent"**. It should be easy to tell what the consequences will be of changing the code.
6. **Code should be "Reasonable"**. The cost of a change should be proportional to the size of the requirement that provoked the change.
7. **Code should be "Usable"**. The code should be easy to reuse in other situations than the one it's currently being used on.
8. **Code should be "Exemplary"**. The code should exhibit qualities that guides and/or encourages those who change it to continue to keep and replicate those qualities.
9. The [Single Responibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle) is a preqrequisite to creating code that is TRUE.

## Single Responsibility

10. A class should have one single responsiblility. That means that it needs to do one thing and do it well. It needs to be as small as possible to fulfill its purpose. It needs to have only one reason to change. "It needs to do the smallest useful thing".
11. A good way to identify what classes your system needs is to read through your user stories or problem descriptions and identify nouns. Those nouns are good candidate for classes.
12. If there are verbs and properties associated with those nouns, then it is most likely a class. Because classes represent bundles of both data (attributes) and behavior (methods).
13. Classes that have many responsibilities are hard to reuse. And because they are not "Usable", they are not easy to change.
14. A class that has many responsiblilities usually means that unrelated code is tangled together within it. Which makes the class hard to reason about, and hard to reuse.
15. In order to reuse the behavior defined within a class with multiple tangled responsibilities, you either need to duplicate code or use the entire class, even the parts that you dont need. 
16. If you are using a class that has many reasons to change, when something unrelated to your use case changes, you will still have to change your code. This is unexpected and surprising. This is not "Transparent".
17. Depending on classes that have many responsibilities increases the chances of your application breaking.
18. A good way to determine whether a class has a single resposibility is to try an enunciate what it does in a single sentence. That sentence should be simple, because classes should be simple. Look out for the words "and" and "or" in this sentence, as they point to it having more than one responsibility.
19. Another good way to determine whether a class has a single responsibility is thinking about every one of its methods as a question that the class, if it were a sentient being, would be able to respond to. For example "Array, what is your lenght?". If the question doesn't make sense, then maybe the method does not belong in the class.
20. Cohesion is the meassure of how related to their core purpose are all of the different elements of a given component. Classes that have a single responsibility are highly cohesive because all of their parts work towards a single goal.

## When to make design decisions

21. Only design as much as you need to for right now. Don't make design decisions prematurely. Sometimes waiting for more information before committing to a design is the way to go. More information in the future will often reveal a better design.
22. Consider postponing design decissions when the information available to you today does not point clearly to a good design. Also, when the cost of not doing it now does not considerably make tomorrow's change more expensive.
23. On the other hand, consider that a class that's left in a "bad state", may be reused by others. Making their code depend on badly designed code. The application will suffer as a result.
24. The structure of a class is supposed to reveal your design's intention to other developers. When it doesn't, when it is not "Exemplary", then future maintenance costs increase.
25. The tension between "improve it now" and "improve it later" is always present. Our jobs as designers is to strike a good balance "between the needs of the present and the posibilities of the future" so that the costs of change are kept low.

## Techniques for writing code that's easy to change

26. **Depend on behavior, not data: Hide instance variables**. Instead of accessing instance variables directly, use accessor methods. Even from within the class that owns them. "Always send messages to access data".
27. That way you consolidate the knowledge of what the data represents in a single place. Single Responsibility Principle in action. Changing it becomes easy as a result because instead of changing references to a variable in potentially multiple places; you only need to change the definition of a method, in a single location.
28. **Depend on behavior, not data: Hide data structures**: When code depends on or receives as input a complex data structure like a big array or hash; encapsulate the data structure in a class with clear interface, instead of accessing and manipulating the structure directly.
29. This style of coding tends to propagate. If the incoming data structure changes, even slightly, then a lot of your code needs to also change because it depends on a very particular structure.
30. Handling complex raw data structures thrugh classes and messages with clear intention revealing names, demistifies the structure and gives it meaning within the context of the application domain.
31. **Enforce single responsibility everywhere: Extract extra responsibilities from methods**. Methods should also have a single responsibility. Just like classes, that makes them easy to reuse, change and understand.
32. To determine if a method has a single responsibility, the same techniques that work for classes apply. Try to enunciate their purpose in a single sentence, and ask them what they do.
33. Methods that iterate on items and act upon them is a common case of multiple responsibilities. Separating iteration and action into two methods is a common refactoring to correct it.
34. Complex calculations embedded within methods are also good candidates to be separated into other methods. It gives them a name and makes them reusable.
35. These refactorings are useful and even necessary even when you don't know the what the final design will look like. In fact, these refactorings (and good practices like these) will often reveal the final design.
36. Methods with single responsibilities: Make a class's details, features and components more obvious, are self-documenting, encourage reuse, establish a styling of programming that is self-perpetuating, become easy to move to another class when and if that time comes.
37. **Enforce single responsibility everywhere: Isolate extra responsibilities in classes**. Move the responsibilities that are extraneous to a class into another class. If you can afford it, create a separate class to hold them. If not, at least encapsulate them in an embedded class so that they are contained and don't leak.
38. Embedded classes say: This class only has meaning and value when thought about within the context of this other class.
39. Embedded classes can be easily promoted to independent classes later if the need arises.
40. Once all methods inside a class have a single responsibility and are each doing the smallest useful thing, it becomes easier to identify the features that may belong to another class.
41. The purpose of design is not to produce "perfect" code but istead to produce code that's "good enough".
42. The Single Responsibility Principle "allows change without consequence and reuse whitout duplication".

# Chapter 3: Managing Dependencies

## About dependencies

1. Objects should have a single responsibility and do the smallest useful thing. This means that, in order to fulfill complex application requirements, many objects need to collaborate.
2. Objects collaborate by knowing things about and sending messages to each other. That creates dependencies. A good design manages these dependencies, making sure they don't couple objects so much that change becomes painful.
3. An object has a dependency when it knows the name of another class.
4. An object has a dependency when it knows the name of a method from another class.
5. An object has a dependency when it knows the arguments of that method.
6. An object has a dependency when it knows the the order of those arguments.
7. Dependencies create a situation where if an object changes, then other objects that depends on it may be forced to change as well.
8. Dependencies couple objects to each other. Highly coupled objects behave as if they were a unit. It becomes hard to reuse one without the other. If not managed properly, dependencies will disseminate and entangle the entire codebase.
9. Some dependencies are unavoidable. So the purpose of design is to reduce and contain dependency. Ensure objects only have the minimum number of dependencies that they need to do their jobs. Keep the essential ones, remove the rest.

## Techniques for writing loosely coupled code

10. [**Dependency injection**](https://en.wikipedia.org/wiki/Dependency_injection). It can help eliminate dependencies on concrete classes. Instead of instantiating new objects of another class inside your object, let it receive it as a constructor or method parameter. The object's client code can do the instantiation.
11. An object that knows less can often times do more. The knowledge of how to instantiate a particular object limits its potential. Object creation and utilization don't need to be contained in the same unit of code.
12. When an object hard-codes the reference to a class, it advertises that it can't work with any other type. Replace the reference to the concrete class with an abstraction (e.g. an [interface](https://en.wikipedia.org/wiki/Interface_(object-oriented_programming)) or [duck type](https://en.wikipedia.org/wiki/Duck_typing)). That gives it the flexibility to be able to collaborate with other objects that respond to the same messages.
13. Sometimes it is not posible to remove a dependency from an object. In those cases, your best bet is to isolate it.
14. **Isolate dependencies: Isolate instance creation**. Sometimes it is not possible to apply dependency injection. In those cases, the next best thing is to encapsulate instantiation of external classes into their own methods.
15. An instantiation encapsulated in a method allows the code to clearly and explicitly communicate that there's an extraneous dependency here. One that we'd like to remove but for now cannot. We also protect the class from that dependency propagating through it.
16. **Isolate dependencies: Isolate vulnerable external messages**. The same technique can be applied to invocations of methods on external classes. Encapsulate such calls into their own methods in order to contain the dependency.
17. **Reduce argument dependencies: Use keyword arguments**. If your language supports them, keyword arguments are a great way of reducing the dependency incurred via method invocations. They allow the parameters to be sent in any order, which means that changes to the method definition and signature and less likely to cause the callers to change. Also, they have a self-documenting property on both caller and callee. ([Named arguments in C#](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments); [keyword arguments in Ruby](https://thoughtbot.com/blog/ruby-2-keyword-arguments)).
18. **Reduce argument dependencies: Explicitly define defaults**. If your language has the feature, parameter defaults are a great way of reducing dependencies to method parameters, as establishing a defaul for a parameter makes it optional.
19. **Reduce argument dependencies: Isolate multiparameter initialization**. If you don't own the code for a complex object initialization or method invocation, you can always encapsulate it in an object or method of your own. A thin wrapper that exposes an interface that follows the techniques we've discussed and that uses the language of your application.
20. Classes should depend on things that change less often than they do.
21. There are three truths about code related to change and dependencies: 1. "Some classes are more likely than others to change". 2. "Concrete classes are more likely to change than abstract classes". 3. "Changing a class that has many dependents will have many consequences".
22. It's OK to depend on classes with a low likelyhood of change. For example, classes in the built-in library of your language generally will change less than your own custom classes. Framework classes commonly change less often too, but that may not always be the case if you framework is rapidly evolving.
23. Abstractions are generally much more stable than concretions. Because of this, it is safer to depend on abstract classes (e.g. interfaces and duck types) than on concrete ones.
24. Avoid classes that have lots of dependencies. Any changes done to them produce a ripple effect of changes throughout the codebase. Also, because of that, people will go to great lengths to try to avoid changing them.
25. When thinking about dependents and likelyhood of change, the following is harmless: 1. Classes with few dependents and low likelyhood of change (e.g. specialized infrastructure interaction classes). 2. Classes with few dependents and high likelyhood of change (e.g. concrete classes that implement your app's domain logic). 3. Classes with many dependents and low likelyhood of change (e.g. interfaces and other abstractions).
25. When thinking about dependents and likelyhood of change, the following is harmfull: Classes with many dependents and high likelyhood of change (e.g. concrete classes that are used throughout the codebase). 

# Chapter 4: Creating Flexible Interfaces

## About interfaces

1. The messages that objects pass between each other are a big concern for design. In addition to what objects know (resposibilities), and who they know (dependencies), design cares about how they talk to one another. Messages pass between objects through their interface.
2. Objects that expose too much of themselves and know too much about other objects are hard to reuse and make systems hard to change.
3. Objects that minimize what they expose of themselves and know little about others are easily reusable and changeable.
4. An object's public interface is the set of messages that it resonds to. That is, the set of methods that other objects are welcome to invoke. Good design calls for objects with clear and concise public interfaces.
5. Classes should have one responsibility, but they will likely have many methods. Some methods are more general and expose the main features of a class, they are the services that the class offers its callers. These make up the class' public interface. Other methods are more specific, serve to support those features, and contain implementation details internal to the class and uninteresting to callers. These make up the class' private interface.
6. The methods in a class' public interface: 1. "Reveal its primary responsibility". 2. "Are expected to be invoked by others". 3. "Are not likely to change". 4. "Are safe for others to depend on". 5. "Are directly covered by tests".
7. The methods in a class' private interface: 1. "Handle implementation details". 2. "Are not expected to be invoked by other objects". 3. "Are likely to change". 4. "Are unsafe for others to depend on". 5. "May not even be referenced in the tests".
8. Public methods list the specific features of a class that allow it to fulfill its responsibility. They advertise to the world what's the purpose of the class they belong to.
9. Public methods are stable, expected to not change often, so others are welcome to depend on them.
10. Private methods are not stable at all. They are hidden from others so they should not depend on them.

## Designing a public interface

11. When analyzing a problem domain, the nouns in the narrative usually become your first classes. These are called "Domain Objects".
12. Don't let Domain Objects be your only classes though. Shift your focus into messages and away from classes to discover new, less obvious objects that will home key functionality. Not doing so will risk overloading your domain objects with more responsibility than what they can handle.
13. [UML sequence diagrams](https://en.wikipedia.org/wiki/Sequence_diagram) are an excellent way to explore design alternatives. You can use them to draft objects and their interactions. I.e. the messages they send each other. They are quick, low cost and allow easy communication of ideas between team members.
14. The transition from class-based design to message-based design is one that yeilds more flexible applications. It means asking "I need to send this message, who should respond to it?" instead of "I know I need this class, what should it do?".

## Focusing on "What" instead of "How"

15. Public methods should focus on "What" instead of "How". That is, they should express what the caller wants insted of how the calee must behave.
16. If you're in a situation where an object calls many methods on another in succession, try to refactor so that all the logic is executed as a result of a single message. This consolidation reduces the size of the second object's public interface, which reduces what callers need to know about it, which reduces dependency, which makes change easier. The caller only knows "what" it needs, not "how" to make the callee deliver.

## Liberate objects from their context

17. The context of an object are the things that it knows about others. What other objects it calls and how. What it needs to work.
18. A good design tries to allow objects to work with minimal context. "Objects that have a simple context are easy to use and easy to test; they expect few things from their surroundings. Objects that have a complicated context are hard to use and hard to test; they require complicated setup before they can do anything".
19. In order to reduce context, we need to reduce the knowledge that callers have about the other components they call. A simple public interface helps with that.
20. Focusing on what the caller wants instead of what the callee does is a way to keeping context in check. Allowing objects to collaborate with other regardless of the type they are and what they do.
21. Dependency injection is a mechanism through which objects can collaborate with others when they don't know their type. A dependency injected via parameter (declared as an interface or duck type) hides its identity from its user.
22. Renaming the methods of this injected dependency from the perspective of the caller reveals a generic interface that offers the features that the caller wants in the vocaulary that it understands. The caller does not need to know what the injected dependeny does, only what it needs from it.
23. Higlhy coupled objects with verbose public interface say to their collaborators: "I know what I want, and I know how you do it".
24. More decoupled objects with concise public interface say to their collaborators: "I know what I want, and I know what you do".
25. Highly decoupled objects with concise public interface and minimal required context say to their collaborators: "I know what I want, and I trust you to do your part."

## Rules of thumb for writing code with good interfaces

26. **Create explicit interfaces**. Be intentional and obvius when defining public and private methods. Use your language access modifiers (i.e. public, private, protected, etc). Your public methods should: 1. Be explicitly identified as such. 2. Be more about what than how. 3. Have names that are unlikely to change. 4. Use keyword arguments.
27. **Respect the public interface of others**. Invoke only public methods on the classes that you use. Avoid circumventing their public interfaces and directly calling private members. Depending on the private interface of framework and library classes is like a ticking time bomb. The reason they are private is because they are expected to change or dissapear entirely.
28. **Minimize context**. Focus on "what" instead of "how" when designing public interfaces. Favor public methods that allow callers to access your classes' functionality without having to know how they do it. Use interface and duck types to name methods from the perspective of and with the vocabulary of the callers.
29. If you have to interact with a class that does not have a clean interface, and you don't own it or otherwise can't refactor it so that it does, isolate it. Use the same techniques for dependency isolation mentioned in Chapter 3. Wrap the invocation in a new class or method to contain it and give that wrapper a clean public interface.
30. **Follow the law of Demeter**. The law of Demeter states that you should't chain multiple method calls thta navigate across many different types of objects. In other words "talk only to your close neighbors" or "use only one dot".
31. Violations of the law of Demeter make for code that's not TRUE. Changes in the object at the end of the chain ripple through the entire chain. This is unexpected and laborious, making the code neither transparent nor reasonable. The class that uses the chain depends on all the objects in the chain, making it non usable. These chains are easy to replicate and harm changeability, making the code not exemplary.
32. Always evaluate the cost of violating the law of Demeter versus the cost of abiding by it. Method chains that ultimately read an attribute are generally less harmful. Also, method chains on really stable classes like those of your language library or framework have low impact.
33. Delegation can appear to be a solution to law of Demeter violations. Unfortunately, all it does is remove the evidence that it's there.
34. In reality, a violation to the law of Demeter indicates that there's an object missing or that the public interface of an object is lacking. Find the object, and its interface, by thinking more about messages and less about classes. Define the interface by thinking about what the object needs of its collaborators, and not about how it can get it by itself.

# Chapter 5: Reducing Costs with Duck Typing

## asdasdasd

1. asduahsd
2. sjkfhsdf
3. sdfjkhsdfhj

## asdasdad