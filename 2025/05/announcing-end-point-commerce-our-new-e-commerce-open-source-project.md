---
author: "Kevin Campusano"
title: "Announcing End Point Commerce, our new E-Commerce open source project."
date: 2025-05-28
tags:
- dotnet
- ecommerce
- opensource
---

Today we're pleased to announce a new open source project: End Point Commerce. A minimalist E-Commerce backend that's quick to set up and easy to understand. Meant for developers to own, adapt, customize and extend.

You can fork it today on [GitHub](https://bits.endpointdev.com/end-point-open-source/end-point-commerce).

## Key Features

- Built with [ASP.NET](https://dotnet.microsoft.com/en-us/apps/aspnet), [PostgreSQL](https://www.postgresql.org/) and [Authorize.NET](https://www.authorize.net/)
- Multiple deployment strategies, including [Docker Compose](https://docs.docker.com/compose/).
- Code base designed to follow [Clean Architecture](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures#clean-architecture) and [Domain Driven Design](https://learn.microsoft.com/en-us/archive/msdn-magazine/2009/february/best-practice-an-introduction-to-domain-driven-design) concepts, without being dogmatic about it. Simplicity trumps all.
- Good test coverage with [xUnit](https://xunit.net/).
- Includes a backend admin portal for managing the store, a REST API for building user-facing store frontends, and a sample frontend for demonstrating key REST API features.
- Limited functionality. Implements the bare minimum of E-Commerce user cases.
- Product catalog, shopping cart, order submission, email delivery.

## How we got here

We recently had the opportunity to help one of our clients migrate their E-Commerce site. They were using an established E-Commerce engine and were having various problems with it. Their requirements were simple, and they didn't need all the bells and whistles of big E-Commerce solutions. They didn't want to deal with the overhead, bloat and difficulty with finding maintainers.

During initial investigation and planning, we didn't find any options that were small, easy to set up, understand and customize, so we decided to build them a new site from scratch.

We realize that there may be others out there in the same boat that we were. You want to set up a custom E-Commerce site but you don't want to deal with the bloat and complexity of bigger off-the-shelf solutions. You want something on which you can get an intimate understanding quickly, and modify to your heart's content, as if it were your own code base that you developed from scratch.

## Who is this for

This project is meant for .NET developers who want a solid and simple foundation to build and customize E-Commerce sites. To that end, the feature set is very basic, the code base is very straightforward, and the documentation is very developer-oriented. The idea being that developers can quickly get up to speed with how everything works, develop ownership over the code base, and implement their bespoke use cases.

A sample web store frontend app is included to demonstrate some of the key features of the REST API. This is not production ready though, as most users will probably want to develop their custom frontends from scratch.

This project is not meant for non-technical folks. There is no installation wizard, no templating engine, no plugin framework, no no-code customization capabilities.

If you want to set up a simple online store, or develop a highly customized one from scratch, think of this as a way of skipping the first few steps of building the foundational architecture and basic functionality.

Please check it out! And do whatever you want with it!
