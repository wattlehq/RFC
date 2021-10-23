# Request for Comment

Request for Comment is a publication that proposes the build of a feature or an enhancement by the core development team or if you wish for the official project to adopt a third party module.

You are not required but encouraged to write an RFC for third party modules, especially if you intend to publish it in the public domain.

ID | Title | Rationale | Status
--- | --- | --- | --- 
[001](RFC-001.md) | Base platform | A definition of the based technology platform and officially supported deliverables | 🧪 Beta
[002](RFC-002.md) | Building and property certificates | An online workflow for ordering and managing the delivery of building and property certificates | 👷‍♀️ Rebuild
[003](RFC-003.md) | Membership management | Membership management workflow for recreation centres (e.g swimming pool) | 📃 Proposed
[004](RFC-004.md) | Facilities geospatial mapping | A baseline platform to build Geomapping features e.g Safe Sharps | 📃 Proposed
[005](RFC-005.md) | Building and property inspection workflow | A mobile workflow for conducting building and property inspections | 🛑 Deferred  
[006](RFC-006.md) | Electronic Property Filing | A purpose built filing system for property documents | 🚧 In Progress 

## Lifecycle of an RFC

An RFC follows goes through these stages:

- [ ] A customer or project participant proposes a feature, proposals must be defined at a high level to capture the requirements of the organisation
- [ ] The RFC is revised by the technology team in consultation with the customer
- [ ] A build is commissioned upon approval
- [ ] Upon successful completion and validation the repositories are accepted into the main project
- [ ] Revisions are made to the RFC to keep adding new features

> Development can begin outside the Wattle project and subsequently be merged back into the main project.

## General design rules

Wattle is made up of numerous sub-projects. This makes it rather challenging to ensure that each project is able to colocate with another. These are general set of guidelines that each module must adhere to. Some of these are technological, others are conventional.

### Schema

Wattle is designed to be use `postgres` as a backend (using other database servers is possible, however our design assumes `postgres` as the standard), a notable requirement is support for [schemas](https://www.postgresql.org/docs/9.1/ddl-schemas.html). Each module must create tables in a `schema` they control, they must also ensure that `alembic` migrations are local to this schema.

A module may cross reference one or more mother modules. A module must not create tables, views on another schema other than their own.

### Naming modules and repositories 

Each module must have a unique name that is accepted by the rest of the project. The name `foundation` is reserved for the base module that everyone else depends on. All changes to `foundation` must be approved by the core team.

A module must at a minimum have two repositories:

- `prefix-server` - which houses the code the to server side API, worker, webhooks, etc
- `prefix-web-client` - which has a PWA built using (but not limited to) React

### URL schemes

Each module is expected to make available:

- A set of APIs (which build upon foundation)
- A PWA that is mounted on a base URL



# Discovery schema