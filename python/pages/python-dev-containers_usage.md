# Python Development Container Usage
## Overview
* Usage guide for installed tooling.

## Requirements

* [**Python Development Container**](https://github.com/MikeLee343/my-dev-environments/blob/main/python/pages/python-dev-containers.md)

## pipenv
**pipenv** serves the purposes of **venv** and **pip**, managing concerns related to virtual environments, package installation and package dependencies.  pipenv, and its commands, manage **pipfile** and **pipfile.lock** files to track dependencies within your Python projects.
### Useful Commands (For use in project directories with a pipenv virtual environment)
* Initialize pipenv virtual environment for the current project context, if not automatically activated:
    ```
    pipenv shell
    ```
* Install package \<package name> + dependencies:
    ```
    pipenv install \<package name>
    ```
* List installed packages + dependencies:
    ```
    pipenv graph
    ```
* Rehydrate project packages + dependencies from pipfile/pipfile.lock:
    ```
    pipenv install
    ```
* Uninstall package \<package Name> + dependencies
    ```
    pipenv uninstall \<package name>
    ```
