# .NET Project Commons and Coding Style Guide

This repository contains common project settings and coding style guide files for .NET projects.

## How to use it

The easiest way to use this repository is to use the <https://github.com/skrysm/base-dotnet> repository as base.

If you can't do this, use the following steps:

First, this repository must be included in a project as a **git submodule**. To do this, call this command in your project root directory:

```sh
git submodule add https://github.com/skrysm/DotNetProjectCommons.git _ProjectCommons
```

Then add a file named `Directory.Build.props` to your project root directory and add the following contents:

```xml
<Project>
  <Import Project="$(MSBuildThisFileDirectory)_ProjectCommons/Common.Directory.Build.props" />
</Project>
```

Next, add a file named `Directory.Build.targets` to your project root directory and add the following contents (note how the file extension differs for the two files):

```xml
<Project>
  <Import Project="$(MSBuildThisFileDirectory)_ProjectCommons/Common.Directory.Build.targets" />
</Project>
```

Afterwards, add the file `StyleGuide.DotSettings` as settings file to ReSharper's **Solution XXX team-shared** settings layer.

*Note:* To clone a git repository that contains submodules, you need to add the `--recurse-submodules` parameter to your `git clone` call. (Sadly, there seem to be no way to enable this option by default.) If you've already cloned your git repository, call `git pull` followed by `git submodule update --init`.

## Why no NuGet package?

I thought about providing this repository as a NuGet package. However, this didn't work out because this repository provides files for the **solution itself**.

NuGet doesn't have support for solution-level packages (only for project-level packages). It used to have something like this (see [NuGet issue #522](https://github.com/NuGet/Home/issues/522)) but the developers decided to remove this functionality (and to [not bring it back](https://github.com/NuGet/Home/issues/1521)).

As a result, users of this repository would need to reference the ProjectCommons NuGet package in a project. This has two drawbacks:

* It may *not* be obvious which project should contain the package reference (if there are multiple projects in the solution).
* The package's contents would only become available after a "NuGet restore" - which usually happens when the solution is first built. Until then, users may (accidentally) edit code in the solution without realizing that the style guide has not been enabled yet.
