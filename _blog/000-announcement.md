---
title: Let's Make A Web App  -  Part 0 - Announcement
description: This is the start of a series that is following me making an application using React and Node as the primary platform. As I progress, I will duplicate and update the Index below, as well as a links to the adjacent article.
---

![Photo by Fotis Fotopoulos on Unsplash](https://cdn-images-1.medium.com/max/1200/0*Op5BdCXesqy3827b)

I’ve been developing web based applications for close to 25 years now. The browsers, tools, technology, operating systems and essential knowledge and skills needed to do this kind of work have all evolved. I have about 3 personal projects that I’m wanting to build as web based applications. I’ve decided to do a lot of the boilerplate and initial work for them in public so that others may learn from what I am doing, or simply copy the final boilerplate as a jumping off point for themselves.

I’ve created a [repository on github](https://github.com/lets-make-an-app/node-react-boilerplate) for this. Right now, it’s just a starter repo configured for Node with a boilerplate README file and an MIT License file. I will try to create a docs/article/STEP markdown file for each step as I work through this, it may take a while to get through, and my process may change as I go along. In the end, I hope to have something useful as a jumping off point as well as interesting.

I will try and update this article as the process moves forward. I’m going to attempt to dedicate 4–12 hours a week as time permits into this project.

# Tools

The main tools I will be using will include but not necessarily be limited to the following.

* [Visual Studio Code](https://code.visualstudio.com/) - this is my editor of choice, you can use whatever you like. I also use bash with starship for my terminal.

* [Node](https://nodejs.org/en/) 12.13+ - Web apps tend to require JavaScript to run at some level or another. Most of the tooling around this is build in JS with Node and NPM as hard dependencies. I happen to like JS and it runs just about everywhere the same. All build and orchestration scripts will leverage Node.

* [Docker](https://docs.docker.com/install/) - I find that docker is infinitely useful for local development, I’ll be using it for local use as well as using [Dokku](http://dokku.viewdocs.io/dokku/) for deployments.

* [Github](https://github.com/) - I’ll be using Github’s Actions for my CI/CD process, pretty much whenever anything falls into master, it will get deployed once tests run. I’ll work through a lot of this as I go. Most of the techniques here will be to document what I’m doing/thinking as I work.

* [SQLite](https://www.sqlite.org/index.html) - Since this is mostly for demonstration purposes, I will be using SQLite which is perfectly usable for internal/small application services. I’ll detail more in the next article.

* [React](https://reactjs.org/) - In my opinion React is the first application framework that feels like the right way to do things. If you are getting started, you might also want to look at Vue. Alternatively there are a number of similar frameworks with a lighter output, but I feel that React offers enough to offset the extra payload that you start with.

* [Redux](https://redux.js.org/) - It’s the defacto standard for state management on the client. I would suggest also considering a look at [GraphQL](https://graphql.org/) (which I may also add later) as well as full on [Flux](https://facebook.github.io/flux/) or [MobX](https://mobx.js.org/).

* [Material-UI](https://material-ui.com/) - I really happen to like [Material Design](https://material.io/design/) in general and feel it’s more often than not one of the better approaches. You can always tweak or adapt the color scheme and create controls that are a tighter fit to your needs, that said in general it’s a great approach. Material-UI in particular is a component library for use with React that handles a lot of the heavy lifting for you.

* [Koa](https://koajs.com/) - Is a server project created by the same author that started Express, but with both hindsight and an eye towards what are baked in features in JavaScript. In particular a much better process for integrating middleware and supporting asynchronous request handlers.


# Directories

The following directories in the source repository will be integrated into this application.

* configuration — In order to support application options (feature flags) as well as localization, and varying deployment models, there will be a configuration directory and associated scripts setup to build specific configurations from yaml to json for use.
* srv — will be the primary api interface as well as the hosting application.
* pub — will be a public facing application containing baseline assets for the root of the site/application as well as any public facing pages that will not require authentication
* auth — will be the credential/authentication pieces. This will include both local user logins as well as facebook, google, and microsoft authentication as initial social integrations (others may be considered).
* app — the actual application code will go here, there may be some shared components with the public interface.
* shared — components and modules that may be shared with both pub and app.
* scripts — any scripts used for build/setup as well as local configuration options.


# Features

The following are the upcoming features that are intended to be worked on…

## Application Structure

Get the baseline directories setup as well as separate package.json files for each section. Each section will have it’s own scripts as well as dependencies and will be able to be built and run together or separately.

## Configuration

Will take a first pass at getting the configuration project setup with some placeholder values to be used in the Server and UI later.

## Server (srv)

Initial server implementation details, will wireup the support for wwwroot assets as well as pub and app directories underneath.

## Public Site App (pub)

Initial boilerplate for public display.

## Private App (app)

Initial boilerplat for private display.

## Shared Components (shared)

The following component features need to be developed for both pub and app…

* layout — initial shared base layout
* header — initial header implementation
* footer — initial footer implementation
* app menu — application menu (top left)
* user menu — user menu (top right)
* General Error — displayed when application error condition occurs (unrecoverable)
* Unsupported Browser — displayed by older/legacy browsers
* Toast Messages — used for alerts and notifications.


## Database

The database access will be behind segmented “services” that will all be integrated directly into the API, but conceptually able to be separated, the access to different “collections” should be siloed to specific services.

Implementation will use a single SQLite3 database, but each service can be separated to use its’ own data access down-stream.

The schema for each table that a service uses will strictly use a 3-part key-value that aligns with Cassandra, ScyllaDB, Azure Table Storage, AWS SimpleDB and others and can be implemented/changed to easily support other data sources. These include a composite key of Partition + Row as well as a Value.

This is conceptually more difficult than a typical SQL database, but will offer better flexibility, and can be displaced/replaced at the services level. The partition and row will be path oriented, all lower-case and will have each part of the path URI Component Encoded.


## Authentication

The following components and features will need to be developed…

**Menu Login** for integration into the User menu for unauthenticated users.

**Login Page** for direct login, or display when denied access to application routes.

**Auth Database / Service** will have the following concerns…

* Login — represents an account/access control for a given user (email, google, twitter, etc…)
* User — represents an individual that may access the system.
* Account — represents an aggregate account in the system, actions not part of a user profile should be done as an account, even if that account is a 1:1 user account type.
* UserRoles, UserAccountRoles — represents the roles assigned to a user in relation to the entire system or a specific account.

## MFA

Multi-factor authentication will be a future feature/option that will expad Authentication to support the following.

* Text / SMS via twillio
* Email via SendGrid or Mailgun
* TOTP Shared Secret (QR Image)

## Administration (UI/API/Service)

There will need to be an administration section, a default (“ADMIN” or “ROOT”) user role should be created with a default user in this context. The following will be very generic boilerplate not needed by any given app and should be developed in such a way that it can be easily ripped out.

**Application Roles** — for defining global application roles that may be assigned to users.

**Account Roles** — for creating/managing accounts, at a very basic level including the roles that may be assigned to any given account user.

**3rd Party Auth Integration** — for managing integration keys for third party authentications, as well as any roles that should auto-assign to users.


# Other References

TBD

# Articles In This Series

* Let’s Make A Web App (this article)
* Developer Tools

## Future Articles

* Application Structure
* Configuration
* Server
* Pub
* App
* Shared Components
* Database
* Auth Service
* Auth API (JWT)
* Auth UI (Routing)
