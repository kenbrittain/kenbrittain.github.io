---
title: What is the Difference Between a Repository and a DAO?
date: 2023-06-04
postindex: 56
url: /post/56/what-is-the-difference-between-a-repository-and-a-dao
---

DAO is a term that was active during my J2EE development days. It referred to an interface for accessing data in the database and returning Data Transfer Objects or DTOs. If you had been doing any Java development you had heard the terms DAO and DTO. These patterns are defined in the book "[Patterns of Enterprise Application Architecture](https://www.amazon.com/gp/product/0321127420/ref=as_li_tl)" by Martin Fowler, et al.

When I started developing in C# a new term as added to vocabulary: Repository. In my mind I thought this was the C# way of defining a DAO. Research has proven that incorrect. A repository, while similar to a DAO, deal with an entirely different set of objects.

Both of these data access patterns are interfaces that provide methods for accessing data in an application. That is where their similarities end.

The Repository pattern is defined by the book "[Domain Driven Design: Tackling Complexity](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215) [in the Heart of Software"](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215) by Eric Evans. I have not read this book. My only contact with the Repository pattern is in the Microsoft documentation [here](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/infrastructure-persistence-layer-design) and [here](https://learn.microsoft.com/en-us/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application).

My understanding is that a repository abstracts objects using an aggregate root or entity object. This could be an order object with references to multiple order lines. The root objects is acted upon by the repository. The repository handles the persistence while being presented as a mere collection of objects.

The DAO pattern provides direct line of access to the persistence layer. The abstraction is around the actual storage implementation. For instance, a table would generally have its own DAO and DTO classes.

Both of these patterns provide interface for access data. A repository provides a higher level of abstraction than a DAO. Both are built to abstract your applications data into objects.
