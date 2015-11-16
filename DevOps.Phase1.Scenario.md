## Phase 1 Development & Operations Objectives

These are the practical DevOps concerns for a PHP application (Laravel framework) with AngularJS as the front-end. It has Postgresql as its main database and uses a job queue service for scheduled processes that happens in the background. There are many software out there with different manifestations of these concerns, but there are also many that are the same.

The aim of this text is to identify what needs to be achieved. This "what needs to be achieved" scenario can then be used by teams to evaluate and identify the approaches and tools that supports the "how can we achieve this" part of the equation. This can be a plethora of tools, a suite of integrated tools or an integrated PaaS.

Again, the concerns are here for use in a target condition (http://theleanedge.org/?p=1751) and not an end true north in itself. You may have a different true north yourself.

Concerns
========

1. Changeability

2. Scalability

3. Availability

4. Manageability

5. Usability

Changeability
==========

For each repository:

+ When a merge is made to the master branch, a CI that listens to that merge will trigger a versioned build of the related artifact(s)
+ Built artifacts are placed in an artifact repository
+ Built artifacts are then deployed to the Integration Environment (minimally resourced)
+ Tests (unit and regression) are automatically ran on the Integration Environment
+ If all the above completes successfully and passes, a notification is sent to the Staging Environment Administrators

A service should be available to authenticated Environment Administrators to perform a single action deployment to a relevant environment

An elegant mechanism must exist to cater for new versions of software in elastic production environments

Deployable artifact can be in any good and sensible form (such as a .deb package) but the encompassing system in which it belongs must support pre and post deployment scripts.

Scalability
========

The mechanism that runs all stateless application has to be elastic based on defined rules to scale up and down.

Availability
=========

On top of cloud vendor based 99.95% availability, we need the ability to easily run the application ecosystem on another cloud vendor

The software ecosystem will continuously run on a single cloud vendor, where the master database reside. A trigger based replication must happen from this master to a slave on another cloud vendor

Manageability
============

There must be versionable repositories for the following:

 + Applications and services code
 + Artifact/package configuration definition and supporting scripts
 + Infrastructure forming maps for each environment
 + Environment configuration

There must be secure auditable repositories for the environment variables containing credentials to access services for each environment

Centralized identity and role management for access control to all environments and services including CI console (i.e. different roles for different environments) and etc.

Each environment (Integration, Staging, Production) must be defined in the form of a (DSL) code where infastructure and infrastructure-level configuration for all resources within the infrastructure are specified

Environment definitions must be available for at least 2 cloud vendors, be it one that can be used for multiple cloud or separate ones for different cloud vendors

Usability
=======

To maintain continuous usability of the software, the following metrics has to be monitored:

+ Health of instances running the various applications
+ Number of organizational accounts
+ Number of users
+ Time to process big data (account analysis)
+ Number of worker instances
+ Number of application serving instances

Instances can be a VM or container