# OSS Package Maintenance

This repository documents the philosophy for process and maintenance of my open source projects, including automation strategies. The goal is a standard process and tooling that makes upkeep and routine releases of open source projects as automated and painless as possible. This repository houses a mix of:

* Philosophy/Process documentation
* Reusable github actions that automate routine tasks
* Custom Python tooling to support both of the above

1. [Terminology](#Terminology)
2. [VCS Strategy](#VCS-Strategy)
3. [Versioning](#Versioning)
4. [Dependencies](#Dependencies)
5. [Testing](#Testing)
6. [Static Analysis and Formatting](#Static-Analysis-and-Formatting)
7. [Releases](#Releases)
8. [Appendix](#Appendix)
    1. [Automations](#Automations)

## Terminology

Open source ecosystems have a natural flow. Many projects build on foundational frameworks and incorporate extensions to those frameworks along the way to a realized application. Where a given piece of software is in this flow will have implications for its versioning, testing and dependency specification. I tend to use the following terminology:

* **Foundational / Framework / Library** Standalone frameworks or libraries that are not applications themselves but are used to build applications. They may solve a specific problem or provide a scaffold to build a particular type of application.
* **Middlestream** Plugins or extensions to foundational packages. 
* **Application** End user software.
* **Upstream** From the perspective of a given package, any direct dependency or ancestor of a direct dependency.
* **Downstream** From the perspective of a given package, any direct user or descendent of a direct user.

(TODO diagram)

## VCS Strategy

I use the git branching strategy [described by Vincent Driessen](https://nvie.com/posts/a-successful-git-branching-model/) with some modification to support automated administrative PR merging (TODO explain).

<div align="center">
    <img src="https://nvie.com/img/git-model@2x.png" alt="Branching strategy" width="75%"/>
</div>


(TODO CLI tooling and cheat sheet for this strategy)


## Versioning

There are two widely used versioning strategies for open source libraries:

* **Semantic** [SemVer](https://semver.org)
* **Calendar** [CalVer](https://calver.org)

**All of my projects use [SemVer](https://semver.org)**. Calendar based versioning can [make sense in some contexts](https://calver.org/#when-to-use-calver), but for most highly connected ecosystem projects the clarity of [SemVer](https://semver.org) is more useful. [CalVer](https://calver.org) may be more appropriate for applications that are not expected to be upstream of any other software or for some monolithic frameworks that do not expect a big middlestream tier directly downstream of them.

The semantics of [CalVer](https://calver.org) can very from project to project. This increases the amount of work you have to do to figure out how to specify a version range on a dependency and because of this will promote very restrictive or exact version match dependency specifiers in middlestream software. This is fine for one-offs, but as the number of middlestream projects using [CalVer](https://calver.org) increases, the potential for version range conflicts between dependencies grows in your middlestream tier. [SemVer](https://semver.org) makes more sense for packages that have a high degree of dependency edges in their ecosystem graph.

Projects that use [SemVer](https://semver.org) often leak breaking changes into minor and bug fix releases. Perfection should not be the enemy of the good here. A 95% success rate is still very useful and when combined with robust CI should enable a high degree of reliability while minimizing the potential for version conflicts in your dependency tree. Good automation, PR and release practice can reduce the likelihood that breaking changes will leak into minor releases. To that end I use a tagging system for all feature PRs merged into develop:

- **BREAKING** - This change requires a major version update because there is a reasonable likelihood that it could break downstream software.
- **FEATURE** - This change adds new functionality to a previous version but there is a reasonable likelihood that it will not break downstream software.
- **BUG** - This is a bug fix that only touches private internals and brings actual behavior inline with documented behavior.

(TODO Version tooling)


## Dependencies

## Testing

## Static Analysis and Formatting

## Releases

## Appendix

### Automations
