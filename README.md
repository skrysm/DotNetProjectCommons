# AppMotor Coding Style Guide

This repository contains coding style guide files for AppMotor projects.

The relevant files are:

* `AppMotor.StyleGuide.DotSettings`: Coding style guide settings for **ReSharper**

## How to use it

This repository must be included in a project as a **git submodule**:

    git submodule add https://github.com/skrysmanski/AppMotor.StyleGuide.git

Afterwards, add the file `AppMotor.StyleGuide.DotSettings` as settings file to ReSharper's **Solution XXX team-shared** settings layer.

*Note:* To clone a git repository that contains submodules, you need to add the `--recurse-submodules` parameter to your `git clone` call. (Sadly, there seem to be no way to enable this option by default.) If you've already cloned your git repository, call `git pull` followed by `git submodule update --init`.
