# Architecture

The following is the definition of the officially supported technologies used across the project. All officially supported modules must use this stack. Third party modules are not required to use the proposed stack.

## Server Technologies

- [Python](https://www.python.org) 3.9+ is our server side language of choice
- [Poetry](https://python-poetry.org) is our package manager of choice

Particular Python frameworks in use:

- [SQLAlchemy](https://www.sqlalchemy.org) is our ORM of choice, coupled with [Alembic](https://alembic.sqlalchemy.org/en/latest/) to manage migrations
- [Celery](https://docs.celeryproject.org/en/stable/getting-started/introduction.html) used to schedule and manage background tasks, primarily configured using a `Redis` backend running in a Docker container.
- [FastAPI](https://fastapi.tiangolo.com/) is used to build REST APIs. At the moment we don't have a use case for GraphQL
- [Pydantic](https://pydantic-docs.helpmanual.io/) is used for validation in various parts of the application

## Client Technologies

All of our web clients are built a [Single-page-application](en.wikipedia.org/wiki/Single-page_application) (SPA) using the [React](https://reactjs.org) framework. You are not required to use these technologies for third party plugins but are encouraged to. We prefer the use of [Typescript](https://www.typescriptlang.org/) for efficiency across the team.

# Types of Modules


## Truth

## Workflow

These modules encapsulate a workflow for the target audience. These modules may have:

- A customer facing experience
- An organisation facing experience
- Require taking payments online or over the counter
- Depend on one or more truth or workflow module

Modules are not required to have all outlined features.

### Example 1: Building and property certificates

Allows councils to accept orders and payments for building and property certificates, and manage the workflow of delivering these back to the customer via the portal. 

This module has a customer facing experience where they can order the certificates and access a history of their orders.

Customers are able to pay for the order via a credit card.

The council has a back office experience where they can manage and deliver the orders. Council can use the back office to lodge orders over the counter.

This module depends on the Property Data Truth module to ensure that orders are being placed for a valid property in the jurisdiction.

### Example 2: Electronic property files

This module assists councils to keep a record of documents related to a property.

This module depends on the Property Data Truth module to ensure that files are being stored against a valid property in the jurisdiction.
