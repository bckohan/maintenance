# maintenance

This repository documents the philosophy for process and maintenance of my open source projects, including automation strategies. The goal is a standard process and tooling that makes upkeep and routine releases of open source projects as automated and painless as possible. This repository houses a mix of:

* Philosophy/Process documentation
* Reusable github actions that automate routine tasks
* Custom Python tooling to support both of the above

1. [Terminology](#Terminology)
2. [VCS Strategy](#VCS-Strategy)
3. [Versioning](#Versioning)
4. [Automations](#Automations)

## Terminology

Open source ecosystems have a natural flow. Many projects build on foundational frameworks and incorporate extensions to those frameworks along the way to a realized application. Where a given piece of software is in this flow will have implications for its versioning, testing and dependency specification. I tend to use the following terminology:

* **Foundational / Framework / Library** Standalone frameworks or libraries that are not applications themselves but are used to build applications. They may solve a specific problem or provide a scaffold to build a particular type of application.
* **Middlestream** Plugins or extensions to foundational packages. 
* **Application** End user software.
* **Upstream** From the perspective of a given package, any direct dependency or ancestor of a direct dependency.
* **Downstream** From the perspective of a given package, any direct user or descendent of a direct user.

## VCS Strategy

I use the git branching strategy [described by Vincent Driessen](https://nvie.com/posts/a-successful-git-branching-model/).

<div align="center">
    <img src="https://nvie.com/img/git-model@2x.png" alt="Branching strategy" width="75%"/>
</div>


### TODO

    - [ ] CLI tooling for this strategy


## Versioning

There are two widely used versioning strategies for open source libraries:

    - [Semantic](https://semver.org)
    - [Calendar](https://calver.org)

**All of my projects use [SemVer](https://semver.org)**. I do not put much value into getting a date signal from a version number. If I am curious I will go look it up. ([CalVer](https://calver.org) may be more appropriate for applications that are not expected to be upstream of any other software or for some monolithic frameworks that do not expect a big middlestream tier directly downstream of them.

([CalVer](https://calver.org) is not appropriate for middlestream projects because The semantics of the version specifiers can very from project to project. This increases the amount of work you have to do to figure out how to specify a version range on a dependency and because of this will promote very restrictive or exact version match dependency specifiers on middlestream software. This is fine for one-offs, but as the number of middlestream projects using CalVer increases, the potential for version range conflicts between dependencies grows in your middlestream tier.


### TODO

    - [ ] Version tooling

