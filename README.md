# maintenance

This repository documents the philosophy for process and maintenance of my open source projects, including automation strategies. The goal is a standard process and tooling that makes upkeep and routine releases of open source projects as automated and painless as possible. This repository houses a mix of:

* Philosophy/Process documentation
* Reusable github actions that automate routine tasks
* Custom Python tooling to support both of the above

1. [Terminology](#Terminology)
2. [VCS Strategy](#VCSStrategy)
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

I use the [strategy described by](https://nvie.com/posts/a-successful-git-branching-model/).

![Branch Strategy](https://nvie.com/img/git-model@2x.png)

### TODO

    - [ ] CLI tooling for this strategy


## Versioning

There are two widely used versioning strategies for open source libraries:

    - [Semantic versioning (semver)](https://semver.org)
    - [Calendar versioning (calver)](https://calver.org)

### TODO

    - [ ] Version tooling

