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

Assuming that the software is deployed on the `root` of a domain e.g `service.temora.nsw.gov.au` these URL design patters must be followed. Assuming `prefix` is the name of the module:

#### Server side

- All API will be prefixed with `/api/prefix/`  e.g `/api/auth/login`
- API endpoints must conform to RESTful design principles
- Server modules must depend on the `foundation` module and build upon the authentication layer 
- Use the same `redis` instance that `foundation` manages but have their own set of `workers`
- URLs must be protected based on the permissions of the logged in user

#### Client side

- You must assume you are mounted on `sub-url` of the deployment, i.e  `/prefix/(a-z)`
- Are required to manage `history` based routing from that sub location
- You must support the browser back button for all logical interactions
- Name all URLs so they make navigation sense to users (think about bookmarking and sharing via electronic communication or printing on promotional material) e.g `/certificates` or `/certificates/purchase`
- Must not break cross domain policies

#### URL prefixes

A module typically makes available customer facing, organisation facing and management interfaces.

- `/prefix/customer/*` - customer facing URLs
- `/prefix/staff/*` - URLs for staff members, authorisation to be implemented per module.
- `/prefix/settings/*` - Interfaces for settings, these may be limited to users with elevated privilege.

# Discovery schema

Although Wattle is so modular, we intend to present the user with a unified navigational experience. This is partly facilitate by the design rules above, complimented by a discovery protocol that allows a module to present itself as part of an installation.

- `/prefix/.wattle-discovery/meta.json` - exposes meta data about the module
- `/prefix/.wattle-discovert/dashboard.json` - exposes widget data for the currently logged in user

# Deployment

```
+---------------------------------------------------------+                                           
|                   Wattle Foundation                     |                                           
+---------------------------------------------------------+                                           
+-----------------+ +-----------------+ +-----------------+                                           
|       EPF       | |   Memberships   | |       etc.      |                                           
+-----------------+ +--------|--------+ +-----------------+                                           
                             |                                                                        
                             |                                                                        
                             |                                                                        
                             |                                                                        
                             |                                                                        
+---------------------------------------------------------+                                           
|                                                         |                                           
|                         Docker                          |                                           
|                                                         |                                           
+---------------------------------------------------------+            
```