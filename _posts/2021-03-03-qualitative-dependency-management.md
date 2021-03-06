---
title: "A Qualitative Study of Dependency Management and Its Security Implications"
author: Team (p)Mango
categories: [Qualitative, Meta]
tags: [dependency management, tooling, qualitiative]
pin: true
---

## Paper Info
- **Paper Name**: A Qualitative Study of Dependency Management and Its Security ImplicationsAttacks on Neural Networks
- **Conference**: CCS '20
- **Author List**: Ivan Paschenko, Duc-Ly Vu, Fabio Massacci
- **Link to Paper**: [here](https://www.researchgate.net/profile/Duc-Ly-Vu/publication/343403374_A_Qualitative_Study_of_Dependency_Management_and_Its_Security_Implications_To_be_appear_in_ACM_CCS_2020/links/5f4d0536a6fdcc14c5f6ef05/A-Qualitative-Study-of-Dependency-Management-and-Its-Security-Implications-To-be-appear-in-ACM-CCS-2020.pdf)
- **Food**: caramel apples

## Problem

Experiments show that researchers and developers from Maven, NPM, and Android ecosystems do not often update their vulnerable software software thus exposing them to the security risks. So they run 25 semi-structured interviews with developers from large and small-medium companies located in nine countries, and investigated the following questions:

RQ1: How do developers select dependencies to include into their projects, and where (if at all) does security play a role?
 
RQ2: Why do developers decide to update software dependencies and how do security concerns affect their decisions?
 
RQ3: Which methods, techniques, or automated analysis tools (e.g., Github Security Alerts) do developers apply while managing (vulnerable) software dependencies?
 
RQ4: Which mitigations do developers apply for vulnerable dependencies with no xed version available?

Those questions are addressed from different aspects, including dependency management and  mitigation of dependency issues, technologies/ tools for automating the software development process, and information needs and decision making during software development. 

## Findings (abridged)

The following are more or less the most relevant observations made by the authors paraphrased for readability.
They are more actionably analyzed in the following section, but seeing the individual observations themselves is helpful.

### Reasons for selection of dependencies

- Security is considered when bringing in new dependencies if company policy requires it.

- Developers rely on community support for a library and the assumption that bug fixes will be prompt and easy to upgrade to.

- A specific developer or architect is often tasked with selection of dependencies.

- Selection of dependencies is often based on information *about* those dependencies (such as GitHub stars or number of contributors).

### Reasons for not updating

- Developers pay attention to vulnerabilities if they're updating dependencies.

- Security fixes are perceived as simple to adopt in general since they are for well-supported libraries.

- Developers often prefer to avoid updating dependencies rather than deal with breaking changes caused by updating.

- Company policy leads to either of two main camps: *never update* and *adopt every new version*.

### Automation of dependency analysis

- Dependency analysis tools are used to find potential issues, but updating dependencies is still manual.

- Some developers want a clear metric and accompanying project badge that indicates project maturity, security, and low number of transitive dependencies.

- Developers perceive dependency analysis as having too many false positives.

- Developer recommendations for dependency analysis tools include: lower false positive rate, offline use, easy integration, and reporting of both new and old safe versions.

### Mitigation of unpatched vulnerabilities

- If fixes for unpatched vulnerable software are difficult, developers often stay with the vulnerability even if it affects functionality they use.

- Some developers simply disable functionality awaiting an official patch.

- Skilled developers fix the vulnerability for themselves and contribute those fixes.

- As a last resort, compatible dependencies may be swapped out.

## Implications and conclusions

The paper draws several conclusions from the above observations.
First, considering security often requires time and expertise that may simply not be available.
The previous suggestion for clear metrics about a project's security and accompanying badge could help address the issue at this point, but that time and expertise is still required at some point in the process.

Second, small, medium, and large enterprise developers are more likely to apply standalone security fixes over those bundled with new functionality.
Research ideas to possibly alleviate this issue include improvements on the deployment side (such as automatic distinguishing of features and security fixes so that they may be released independently) and on the incorporation side (such as automatically applying security fixes that do not have accompanying feature changes).
Both aspects would seem to be particularly unpleasant to deal with in the general case.

Third, while large enterprises tend to use automated dependency analysis, there is no such pressure to use them in most small/medium enterprises.
The authors give specific recommendations to creators of dependency analysis tools:
- report only relevant vulnerabilities
- identify the part of the project affected by vulnerabilities
- suggest multiple safe versions so that approaches other than "update to the newest version" can be considered
- warn if fixes require breaking changes

The final observation is of the tendency for large enterprises to work proactively with respect to vunerabilities in dependencies while small/medium enterprises are more passive.
Differences in skill level, recognition of dependency management as important work, and simply available time lead small/medium enterprises to rely more on community support.
As such, specific mitigation recommendations for dependency analysis tools focus on the needs of large enterprises.
Recommendations include both support for directly accessing dependency source code to attempt to fix vulnerabilities and tooling to evaluate compatible replacements and the work required to switch to them.

## Discussion

This paper did a good job of investigating a developer's mindset while managing software dependencies and the security implication which come with it. Most of the difficulties and challenges described in the paper are from the point of view of a developer in a large organization and since most of us have very less experience working in the industry, the discussion for this paper was relatively quite.

Often companies seem to have policies and restrictions in place with respect to the usage of open source tools and open sourcing the tools they develop. Many open source projects tend to use GPL, which means that any derivative work must be distributed under the same or equivalent license terms, which might not be what companies want to do. Most of the projects and tools developed by our lab are open source and hosted on github, so generally we don't have any issues having dependencies or updating them. We have found dependabot to be really useful for managing them.

We also think that the data and insights collected from a qualitative analysis research is really interesting. It might even be a good idea to write a qualitative analysis paper before doing a quantitative paper. What do you think?
