# Code Repositories

The below guidance is targeted at staff developing software for their organisation.

## Storage and Upload Management

Where possible, all relevant code for systems should be stored in Git repositories. Using open-source repositories on a large host like [Github](https://github.com/) enables [Advanced Security](https://docs.github.com/en/get-started/learning-about-github/about-github-advanced-security) which provides code scanning, secret scanning and dependency reviews. Good practices for public open-source repositories include, but are not limited to:

- Separation of sensitive information into env variables excluded using gitignore files:
  - organisation specific configuration (e.g. references to URLs, file and folder paths, etc.)
  - security credentials (e.g. usernames, passwords, etc.)
- Ignoring media and other persistent content related to applications such as:
  - Organisation specific media and static content (e.g. uploaded files, customised styles, etc.)
  - Extraneous files generated during development (e.g. database dumps, fixture data)

Essentially, the code repository should only contain code and build scripts required for anyone (i.e. public users) to download and build the system for own use, and therefore should not contain any organisation-specific details or information that may compromise internal systems. A useful library of .gitignore templates is maintained in this repository: [github/gitignore](https://github.com/github/gitignore).

## Development Workflow

Software development projects being undertaken by teams greater than one person are recommended to adopt a defined standard of development workflow in order to use source control effectively across the team. The appropriate workflow is context-sensitive to the project and the team. A number of different workflow procedures that use Git are compared in this article: [Comparing Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows/).

## Private Repositories

In the event that the use of a public repository is not possible, code may be uploaded into a private repository.

These private repositories should be kept to a minimum, with the intention of refactoring/stripping the code of sensitive artifacts in the future to enable publishing of the code via a public repository.

## Project dependencies and reproducibility

It is a good practice to always work in an isolated project environment. In the case of Python/Django projects, this means making use of tools such as [Poetry](https://python-poetry.org/docs/) to isolate and contain the project environment and libraries from other projects. Ensuring an application can be [built as a a docker image](https://github.com/docker/setup-buildx-action) and pushed to a [package repository](https://github.com/docker/login-action#github-container-registry) is a good way of ensuring reproducibility across development and production environments.

## Testing and continuous integration

The usage of tests to check for correct behaviour, exceptions and regressions is generally considered desirable. However, implementing tests requires an investment of resources and the scale of testing depends on a project’s scope. Small proof-of-concept works and projects making heavy usage of agile development may not benefit from extensive tests. Larger, mature projects with a well-defined specification might be good candidates for test coverage (especially where there is an expectation of ongoing updates of functionality).

Project developers will be best placed to make the decision about the type and scope of tests that are implemented. The following points should be considered:

*   Tests should be limited to code that is owned by the project; don’t test the behaviour of external libraries and dependencies.
*   Prioritise testing of low-level business rules and custom methods ahead of end-user GUI behaviour.
*   Make use of framework testing tools where possible to minimise the effort required to generate tests.
*   Use generated test input as well as defined inputs to locate unexpected behaviour.
*   Use automated testing tools to run tests and record the results to minimise developer effort and to catch regressions earlier.

A practical example of automated testing is the [PRS](https://github.com/dbca-wa/prs) corporate application. This project uses test classes defined in the [Django](https://docs.djangoproject.com/en/4.0/topics/testing/overview/) framework, and a library ([mixer](https://mixer.readthedocs.io/en/latest/)) to generate (most) test data. A [Github Action](https://github.com/dbca-wa/prs/blob/master/.github/workflows/run-tests.yml) automatically runs unit tests for new commits and pull requests.

## Code Access by external parties
External contractors should be setup with only access to code repositories, carrying out any development work on local environments. No direct access to code deployed to internal systems should be needed by external contractors.

## System Deployment
Deployment of these systems to organisational infrastructure should be controlled by the organisations equivalent to ITIL processes (e.g. standard change).