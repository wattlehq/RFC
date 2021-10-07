# Wattle Cloud Platform

> **NOTE:** the contents of this repository are in **HEAVY** development, so please tread lightly until we declare things as stable. 

![city scape hero][hero]

Wattle is a full open sourced platform that aims to fundamentally improve the software stack for the public sector. Although we are primarily aimed at the public sector, the intellectual property has the potential to improve the workflows of many similar organisations.

This repository houses the request for comments which are current or confirmed future features of the platform.

## Projects

| Project | Description | Status
--- | --- | ---
Design System | A set of React components based on the DTA's design system guidelines | 🚧 In Progress
[RFC-001](RFC/RFC-001.md) | Foundation [Server](https://github.com/wattlecloud/foundation-server) and [Client](https://github.com/wattlecloud/foundation-web-client) | 🚀 Alpha
[RFC-002](RFC/RFC-002.md) | Building and property certificates | 🗺 Planning
[RFC-003](RFC/RFC-003.md) | Membership management | 🚧 In Progress
[RFC-006](RFC/RFC-006.md) | Electronic Property Filing | 🧪 Alpha

## History

Wattle was born out a humble collaboration between Temora Shire, Coolamon Shire councils and Anomaly Software. The initial version delivered a simple workflow and payment solution to manage orders of building and property certificates. The three key features of the initial platform were 

- Online payments (then via their bank) 
- A workflow solution to keep track of the orders
- Ability to cross reference the property details for all orders

Over the years the platform aged considerably, until such point that the payment APIs were deprecated. 

A continued conversation between the two councils and Anomaly, had us build a next generation version of the platform which Anomaly offered as a SaaS platform. It was immediately apparent that it was the wrong approach for the kind of product Wattle is.

Anomaly retracted the SaaS offering to reboot the entire platform as a truly Open Source ecosystem.

## Why Open Source

Anomaly has had the pleasure of working in the local government space building solutions for nimble councils and joint organisations. We've built truly innovative solutions for many organisations, however each project suffered issues of lack of funding or barriers to entry due to high cost of software licenses.

The software industry has changed rapidly but older vendors have stuck to traditional licensing models. The public sector exists to service the citizens. All accompanying digital services exists to amplify the experience the customer has.

At Anomaly we believe that building a truly open source platform we can empower these organisations to bring their services truly online.

Every component, including all of it's dependencies of Wattle are open sourced and are based on open standards, this ensures complete freedom of development and operation on any infrastructure.

Each component ever built will be merged back into the collective for all organisations to benefit from, allowing sponsors of this project to know that intellectual property produced isn't locked to a particular organisation or cause.

Anomaly deeply understands the underlying technologies that large platforms are built upon and has a long history of open sourcing their core intellectual property. We believe we are uniquely placed to restart Wattle as an open source project and give it the life it deserves.

# Sponsoring our work

Wattle is primarily funded by Anomaly Software, who have had long had the vision to fundamentally reboot the software offerings in the public sector. Having examined the landscape we believe that an open sourced model is the ideal model for growth of software in this space.

Financial and in kind contributions are very welcome. If you are an organisation please contact Anomaly if you wish to be invoiced.

# Request for Comments

This repository houses the Request for Comments. Each RFC is a detailed description of a feature that either exists or will be built into Wattle. The aim of the RFC is to clearly spell out the intent of the feature, get feedback from the community of users, iterate over the idea before it's commissioned.

How to start an RFC:

- If you are about to post a new idea, but are unsure then we encourage you [start a discussion](https://github.com/wattlecloud/RFC/discussions/) first
- Fork this repository 
- Make any proposed changes to the RFC or start a new RFC 
- Lodge a pull request for us to review and merge your changes in

Note: that all source code and documentation are housed in different repositories.

# License

All work on the Wattle project is published under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0.html), unless otherwise noted.

[hero]: https://github.com/wattlecloud/RFC/blob/145a1d372c3a5367b07fcc28d4cb6e84d4ed6491/images/hero.png "city scape hero"
