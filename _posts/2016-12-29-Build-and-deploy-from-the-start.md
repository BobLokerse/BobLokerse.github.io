---
layout: post
title: Build and deploy from the start
tags: ci, continuous integration, octopus deploy, appveyor, build server, unit tests, fake db, peer reviews
---
## Intro ##

A lot of times applications are deployed by hand on a developers laptop.

That can be time consuming and it is mostly done by one, or a few developers within the team.

With a build server, you know you have an independent build, unit tests & code analysis checked (if setup) and a package that can be tested by the test team, if deployed.

If the application has had some releases, it is setup for manual builds and deployments.
When that is in place, the application must be adjusted for a build and deploy server. 
For example the transformation of the configs now needs to be done at deploy time instead of at build time; that is because the package from the build can potentially go from test all the way to production. When done manually, it is build for a specific environment.
That also means that when a version is approved by the test team, a new build needs to be made for the acceptance environment; the same for production. 


## From the start ##
So, how to smoothly implement this?
Well, when there is little to nothing to integrate: at the start of the project.

With no history it is easy to configure and the application is setup correctly from the start. The CI setup can grow with the application, although probably little to no changes are required.
And every team member can do a deploy. 

Especially [Octopus Deploy](https://octopus.com/) is easy to use, also non-developers can do a deployments once it it setup
(for .Net projects)

Some options for build servers are:

- Team Foundation Server (TFS). Depending of the version, it might need an upgrade (Compiler version / .net framework version)
- A hosted build server [AppVeyor](https://www.appveyor.com/)
- An on premise option is [Bamboo](https://www.atlassian.com/software/bamboo)


## Extras ##

### Unit test basics ###
Another good thing to setup from the start, is the unit test basics.
Setup the use of a fake database with dependency injection and make some unit tests that can be used as examples.

For Sitecore projects, these are good blogs: 

- [Isolating calls to Sitecore.Context for improved unit testability - Part I: ItemProvider, Moq and FakeDb](http://blog.marcduiker.nl/2014/11/18/isolating-calls-to-sitecore-context-part-1.html)

- [Improving unit test readability: helper methods & named arguments](http://blog.marcduiker.nl/2016/06/01/improving-unit-test-readability-named-args.html)

### Peer reviews ###
To share the code and knowledge of the application and it changes, do peer reviews between developers of a feature. It also triggers the talk about the way of coding, to improve the coding guidelines, uniform coding.
