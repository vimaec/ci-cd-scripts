# CI/CD scripts #

This repository contains:
- GitHub [actions](actions/) that are used in the VIM testing and building pipeline.
- Bash [scripts](scripts/) that are used by the actions.
- [Templates](templates/) for a quick and easy setup of a new repository.

## Actions ##

- [Build and Test](actions/build-and-test/action.yml) action compiles the project and runs its unit test. It can also check if the current project version has already been pushed to NuGet.org.
- [Publish to Nuget](actions/publish-nuget/action.yml) action runs the "Build and Test" and after that creates a NuGet package and pushes it to NuGet.org. The API key has to be provided.

## Scripts ##

- [csproj-version.sh](scripts/csproj-version.sh) retrieves the project version from a .csproj file specified by the `<Version/>` tag.
- [check-nuget-version.sh](scripts/check-nuget-version.sh) checks if the project version already exists on NuGet.org.
- [tag-commit.sh](scripts/tag-commit.sh) marks the most recent commit with a tag with the project version and pushes this tag.

## Templates ##

- [build-test.yml](templates/build-test.yml) - put this workflow into the `.github/workflows` folder of the repository in which you want to build and test a VIM project using GitHub Actions. You'll need to set the project path and NuGet package name.
- [publish.yml](templates/publish.yml) - put this workflow into the `.github/workflows` folder of the repository you want to push NuGet packages from using GitHub Actions. You'll need to set the project path and NuGet package name. Also this repository will need the NuGet.org API key to be set as a secret named `NUGET_KEY`.