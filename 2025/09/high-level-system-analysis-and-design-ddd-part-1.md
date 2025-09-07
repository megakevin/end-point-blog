---
author: "Kevin Campusano"
title: "High level system analysis and design with Domain Driven Design"
date: 2025-08-25
tags:
- domain-driven-design
- software-engineering
- architecture
- design
- books
---

> This is part 1 of a series of blog posts on Domain Driven Design:
>
> 1. [High level system analysis and design with Domain Driven Design](https://www.endpointdev.com/blog/)
> 2. [Blog post #2](https://www.endpointdev.com/blog/)
> 3. [Blog post #3](https://www.endpointdev.com/blog/)
> 4. [Blog post #4](https://www.endpointdev.com/blog/)

Domain Driven Design is an approach to software development that focuses on, [as Eric Evans puts it](https://www.oreilly.com/library/view/domain-driven-design-tackling/0321125215/), "tackling the complexity in the heart of software". And what is in the heart of software? The business domain in which it operates. Or more specifically: a model of it, made of code. That is, the code that implements the business logic and rules that come into play when solving problems within the realm of a particular business activity.

DDD is not just about writing code though. It's a whole methodology that touches on business needs, requirements gathering, organizational dynamics, high level architectural design, and lower lever patterns for implementing business logic.

In this series of blog posts we're going to explore many aspects of DDD. We will be following the structure laid out by Vlad Khononov's excellent book on the topic "Learning Domain-Driven Design: Aligning Software Architecture and Business Strategy". So you can think of this series as a summary of sorts. An abridged version of the contents of the book that can serve as a review for anybody who has read it; but also as an entry point for people who are new to DDD.

# Chapter 1. Analyzing Business Domains

It is a well understood notion that before writting code, we need to understand the problem we're trying to solve. DDD is consistent with this notion and argues that developers need to, first and foremost, gain an understanding of the business that the software is being built for. To this end, DDD relies on three concepts: domains, subdomains and domain experts.

## Domains and subdomains

In simple terms, the domain of a business is what it does, its area of business activity. For example, Starbucks is in the business of making coffee. Ford is in the business of making automobiles. AMC is in the business of movie theathers.

Of course, analyzing a business as a single integrated whole can be unmanageable. That's where subdomains come in. Subdomains are the different divisions within a domain. Starbuck's domain, for example is making coffee. But there are many smaller parts that make up that business and allow it to be successful. There's of course, the subdomain of coffee preparation. But there's also real estate management to find and secure good locations, there's inventory management and logistics, there's marketing, there's human resources, etc. All these are the subdomains that make up the overall business of Starbucks.

Depending on the business and on the project, these will vary greatly in granularity. And you can also sub-divide subdoimains further and discover new fine-grained subdomains nested within more coarse-grained subdomains. The sizes and nesting levels can be very different from business to business. One good rule of thumb to keep in mind is that generally, subdomains encapsulate a set of coherent, closely related use cases. That is, use cases that involve the same set of closely related actors, busines entities or data.

And finally, we have domain experts. As the name suggests, these are the people within the organization who have intimate knowledge of the business, or certain aspects of it. They are the subject matter experts. Usually they are the ones who identify the problems and come up with requirements. Developers need to rely on domain experts to gain the necessary understanding to be able to produce useful software solutions.

So, when approaching software projects, DDD suggests that developers work closely with domain experts in order to learn from them about the business domain and subdomains. After all, it is their mental models and understanding that will be modeled and implemented in code.

## Types of subdomains

With the help of domain experts, developers can identify subdomains, and understand their business value and how they fit within the overall business strategy. This is very important because it helps making some initial architecturaly significant decissions. Namely, the general approach to solving the problems in the subdomains, how much to invest, how to organize development teams, etc. The main objective in this analysis stage is to identify the subdomains and whether they fall into one of three types: core, generic, and supporting.

Core subdomains are the highest value activities of the business. The ones that confer differentiation in the market and competitive advantage. They are the business raison d'être. For example, for Google, their search engine is a core subdomain. For Ford, their automotive engineering area would be a core subdomain. Core subdomains are generally the most complex parts of the business. They are constantly evolving and improving, and the company is compelled to invest highly in them.

Generic subdomains are also very complex. However, they are not business differentiators. Instead, these are the areas of the business that all organizations handle in the same way. Think accounting, a ticketting system, an online storefront. There's no presure to innovate in these areas, so the solutions are very stable and evolution is slow.

Supporting subdomains on the other hand, do not provide any competitive advantage, nor are they high in complexity. They are however, necessary because they support the core business activitites, and are fairly unique. The solutions to problems in these areas usually take the form of [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) or [ETL](https://en.wikipedia.org/wiki/Extract,_transform,_load) oriented activities. Imagine for example populating a data warehouse, translating transactional business data into a format appropriate for analytics and business intelligence in a manufacturing corporation. Or maybe the digitalization and storage of a registry of court documents for a law firm. These are behind the scenes activities that support the organizations' main businesses, but their business logic complexity is low, and they don't really represent big selling points for the companies.

It's worth noting as well, that there may be subdomains where software solutions are not appropriate, even if they are higly complex core subdomains. They are still part of the business so it's worth identifying and considering for high level architectural design decissions. If anything, to know what parts of the business the planned software system should and should not focus on. You could have a restaurant, for example, who prides themselves in having the best desserts in the city. For their business, the recipe development activities constitute a core subdomain. This is dependant on the art and craftmanship of the chefs. Not an area in which software solutions could help a whole lot.

It's also worth noting that, just as organizations' business strategies are dynamic, to too can be their subdomain distribution. Today's generic subdomain can be tomorrow's core subdomain, and so on. For example, imagine a big retail store chain that, up until now, managed its inventory in an industry standard way. But is has grown so much that the standard way of doing things has become a bottleneck for them. So they design a new procedure for higly efficient inventory management, and that gives them an edge against competitors. Inventory management started as a generic subdoimain for them, but due to an ever evolving business strategy, it became a core subdomain.

In summary, these are the main characteristics of the three types of subdomains:

1. Core subdomains have high complexity, provide competitive advange, and change and evolve frequently.
2. Generic subdomains have high complexity, do not provide competitive advantage and change overtime, although at a slower pace than core subdomains.
3. Support subdomains have low complexity, do not provide competitive advantage and are the slowest to change.

## Using subdomains to make strategic decissions

Like I've already alluded to, armed with this knowledge, DDD practicioners are ready to start making some higher level architectural decisions. Depending on the type of subdomain that a problem belongs to, DDD has specific prescriptions on how to handle the implementation of software solutions for them.

When working on core subdomains, that's where we want to make the biggest investments. We deploy the most advanced engineering tools, patterns and practices. This is to make sure that the software is efficient and high quality, but also easy to maintain and evolve. This is necessary because core subdomains have to evolve rapidly by nature, if the business is to maintain competitive advantage. Software solutions that operate within the context of core subdomains have to be implemented by high skill and high trust teams. Either in-house, or via trusted development partners, working hand in hand with domain experts.

Problems in generic subdomains, by nature of their business logic being very complex but also very common, are likely to have already been solved. For these types of problems, DDD recommends against implementing custom software, and instead buying and/or adopting tried and true, industry standard, off-the-shelf solutions. Their implementation and integration can be outsourced or handled by less specialized or skilled teams. The change management of these solutions is simple, given that they are not custom software, as they get delivered generally via patches and updates.

For support subdomains, whose business logic is generally simple but uncommon, it is less likely that off-the-shelf solutions would be available. So software addressing problems in these subdomains will most likely have to be implemented as custom solutions. Due to their low complexity though, they can be easily outsourced, or handled by more junior team members. They can also be handled with [RAD](https://en.wikipedia.org/wiki/Rapid_application_development), low-to-no-code technologies, since a lot of the times they are little more than ETL and CRUD applications.

Here's a table to summarizes the differences between the types of subdomains:

| Type of subdomain     | Core               | Generic                 | Supporting         |
|-----------------------|--------------------|-------------------------|--------------------|
| Competitive advantage | Yes                | No                      | No                 |
| Complexity            | High               | High                    | Low                |
| Rate of change        | High               | Medium                  | Low                |
| Implementation        | Custom development | Buy/adopt off-the-shelf | Custom development |
| Team                  | In-house/partners  | Can outsource           | Can outsource      |
| Team skill            | High               | Regular                 | Low                |
| Investment            | High               | Medium                  | Low                |
| Problems              | Interesting        | Solved                  | Simple             |

# Chapter 2. Discovering Domain Knowledge
# Chapter 3. Managing Domain Complexity
# Chapter 4. Integrating Bounded Contexts