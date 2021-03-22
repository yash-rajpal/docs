# Basics stucture of Codebase

Rocket.Chat has a huge Codebase, anyone can get overwhelmed by going through it for the first time. This guide should give you a basic overview and understanding of the codebase.

## Technologies we use at Rocket.Chat

Rocket.Chat is built on the isomorphic full-stack framework [MeteorJS](https://www.meteor.com/). MeteorJS handles the server-side code and logic.
The client-side code is being slowly ported into [ReactJS](http://reactjs.org/) from the older code which was written using [Blaze Templates](https://guide.meteor.com/blaze.html).

## Basic overview of Codebase

<!-- Needs refactoring -->

Meteor is a full-stack isomorphic framework built on top of NodeJS. This means Meteor applications differ from most applications in that they include code that runs on the client, inside a web browser , code that runs on the server, inside a Node.js container, and common code that runs in both environments. Our backend is managed by MeteorJS, all api calls and database queries are written in Meteor. As we use Meteor, we have all major code divided between server and client folders. The code in server folder runs on server side, and code in client folder runs on client side.

We are porting all of our Meteor's front end implementation to ReactJS. To provide a consistent UI/UX, we have created a npm package known as [Fuselage](https://github.com/RocketChat/Rocket.Chat.Fuselage), where we have implemented all basic components used by Rocket.Chat. In the codebase, the components from fuselage are the building blocks for more complex components and UI of Rocket.Chat. Refer [here for Fuselage docs](https://rocketchat.github.io/Rocket.Chat.Fuselage/fuselage/master/?path=/story/box-intro--page).

<!-- End Refactoring -->

## Folder Structure

**`app`** folder contains the majority of business logic code for the Rocket.Chat, including 3rd-party integrations (OAuth, Video Conferencing, File-Upload tools, chat-importers, slashcommands, notifications, cloud integrations, etc.). Most of the codebase relies on the functions, utilites, and apis provided in this folder. This folder is also the home for core components such as the **database** models and the **api** endpoints.

**`client`** folder contains code (which can run only on Browsers) for frontend implementation using React. It has conventionally named sub folders, throught which one can easily identify what frontend code is in which folder. (for example - `sidebar` folder has all frontend implementation for sidebar. Similarly, `views/admin` and `views/omnichannel` have frontend implementations for the same).

**`server`** folder code which can run only on a server-side NodeJS runtime. It mostly contains the _Meteor_ methods, code to run during server startup, database migrations, [cron job](https://en.wikipedia.org/wiki/Cron) codes.

**`definition`** contains Type Declarations for the Typescript files in the codebase.

**`tests`** contains the code for unit tests (such as API endpoints), integration tests, end-to-end tests (such as UI tests using Cypress).

**`ee`** contains all the enterprise features, like Omnichannel, LDAP-authentication.

**`packages`** folder mainly contains modules (such as `i18n` for _internationalization_) consumed by Rocket.Chat and MeteorJS.

**`public`** folder contains the assets including fonts, icons, images, svgs and sound files.
