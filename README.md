# Technology Outreach
This collection of documents is intended to provide strategic and technical architecture guidance and examples, from several years of accumulated experience working with both open-source and proprietary technologies.

- **Core Principles -** Simplify Adoption, Reduce Complexity, Define Ownership, Reduce Friction/Constraints
- **Target Audience -** Developers, Infrastructure Operations, Enterprise IT

Typical Enterprise Architecture tends to be overly prescriptive (e.g. use 'preferred technology stack' for everything,  eliminate outliers). This rigidity results in individuals and small teams in organisations working outside of the boundaries defined (i.e. Shadow IT). Once a central IT team is established within an org, ensuring the goals of that team are to simplify the usage of IT as well as removing overlap (by defining ownership), then steady progress can be made in several other areas for the whole organisation.

TL;DR - Ensure organisational oversight exists for all technology usage, and provide a clear simple path (such as these documents) to secure and efficient technology modernisation for outliers.

## Baseline artifacts
- Central register of technologies. Include platforms, business applications, operational technology.
- Central logging and monitoring infrastructure.
- Ownership model. Include technical staff, developers, sysadmins, procurement responsibilities.

## Guidance
In a small organisation a single team will hav
TODO: target below at owners of various responsibilities. Small orgs will have to be across all areas where larger orgs can divide responsibilities between teams. Below guidance is in order of usefulness/implementation (i.e. first item will have biggest ROI and lowest effort to implement)

### For Developers
Developers resource allocation should be led by Enterprise IT
1. [Code Management](Documents/CodeManagement.md)

### For Infrastructure Operations
Infrastructure Operations focus should be streamlining developer workflows and securely integrating with external SaaS systems
1. [Security Uplift](Documents/SecurityUplift.md)

### For Enterprise IT (Portfolio & Project Management)
Enterprise IT should guide the organisation into optimal investments to either adjust business processes to match existing commercial offerings, or clearly define unique organisational problems for internal/external developers to build, customise and maintain solutions for.
1. Enterprise Architecture

### [Azure Security Fundamentals - Shared Responsibility](https://docs.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility)
Define at a high level what your central team has skills in and what can be outsourced (most likely to a public cloud provider or SaaS provider).
![shared responsibility](https://docs.microsoft.com/en-us/azure/security/fundamentals/media/shared-responsibility/shared-responsibility.svg)



