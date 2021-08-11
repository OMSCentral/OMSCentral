# omscentral

Monorepo for [omscentral.com](https://omscentral.com) containing the following projects:

- [GraphQL](./graphql/README.md)
- [Server](./server/README.md)
- [Client](./client/README.md)

## Getting Started

To install top-level dependencies:

```sh
npm ci
```

Before proceeding, follow the instructions in project-specific READMEs in the order above (graphql, server, then client).

## Scripts

### `npm run format`

Formats all source code and package.json.

### `npm test`

Tests services.

### `npm run dev`

Starts services in development mode w/hot-reload.

### `npm run build`

Builds services.

### `npm start`

Starts services in production mode. Note: You must run `npm run build` first.

### `npm run cypress`

Runs cypress integration tests that enforce correct behavior. Requires the application to be up with `npm run dev` or `npm start` first.

### `npm run cypress:clean`

When finished, users created during tests may be cleaned up using this script.

## System Architecture overview

- OMSCentral is a course review website primarily written in [TypeScript](https://www.typescriptlang.org/).
- This section provides a high level summary of the current architecture:

### Client

- The client is a React single-page-application(SPA) that allows users to see anonymous reviews.
- Authenticated users may also publish, edit, or delete reviews, that they own, for the courses.

#### Tools used

The following is a short list of tools used, ordered by category:

#### UI

- [React](https://reactjs.org/) library is used for building the user interface.
- [material-ui](https://material-ui.com/) is used as a React UI framework.
- [react-hook-form](https://react-hook-form.com/api/) is used for creating forms.

#### Logging

- [sentry](https://docs.sentry.io/platforms/javascript/guides/react/) is used for error reporting and logging.

#### Communication

- [graphql](https://graphql.org/) is a query language used to communicate between the client and the server.
- [apollo](https://www.apollographql.com/docs/react/) is a graphql client library.

#### Deployment

- [Firebase](https://firebase.google.com/) is used for deployment.

#### Build time

- [eslint](https://eslint.org/docs/user-guide/getting-started) for build time linting and static analysis.
- [prettier](https://prettier.io/docs/en/) is used for code formatting.

#### Testing

- [cypress](https://docs.cypress.io/) is used for writing tests.

Please refer to the [package.json](client/package.json) file the for the most up-to-date list of tools used with version numbers mentioned.

### Server

The server

- persists course reviews and semester information to the database(See Persistence section below).
- updates the  statistics for courses
  - e.g average workload, minimum rating etc

### Tools used

The following is a short list of tools used, ordered by category:

### Framework

- Node.js based [express](https://expressjs.com/)

### Database

- [Objection](https://vincit.github.io/objection.js/) is used for Object Relational Mapping(ORM).
- [knex](https://knexjs.org/) is used as a query builder.

### Synchronization

- [bluebird](http://bluebirdjs.com/docs/api-reference.html) is used for access to synchronization primitives like promises in JavaScript.

### Logging

- [Winston](https://github.com/winstonjs/winston) is used for logging.

Please refer to the [package.json](server/package.json) file the for the most up-to-date list of tools used with version numbers mentioned.

### Persistence

- The courses, semesters and reviews data is stored in a relational database.
- Relational Database used: [postgres](https://www.postgresql.org/)
- The server reads and writes to postgres database using objection js and knex js.

## User Authenication

- User authenication is a security layer.
- It allows a user to register his/her profile.
- After his/her credentials are verified at time of login, the user can modify review data after.
- Tools used:[Firebase](https://firebase.google.com/docs/auth/web/start)

## Package management

- The third party dependencies are obtained using npm.
- Tools used: [npm](https://www.npmjs.com/)

For a system architecture diagram, please see [here](./diagrams/SystemArchitecture.png).

