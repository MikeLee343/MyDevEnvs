# Python Development using Dev Containers
## Why Follow These Steps?
* Support development environment tooling isolation between projects on a single desktop via **VSCode Dev Containers**.
* Simplified Python interpreter version management via [**pyenv**](https://github.com/pyenv/pyenv).
* Simplified virtual environment and dependency management via [**pipenv**](https://github.com/pypa/pipenv).
* Bundled [**Postgres**](https://www.postgresql.org/) Container.

## Requirements
* **Windows, MacOS or Linux Desktop**
* [**Visual Studio Code**](https://code.visualstudio.com/)
* [**Docker Desktop**](https://www.docker.com/products/docker-desktop/)

## Setup Steps (~10 mins)
### Create New Project or Clone Project Locally
1. Create a new directory for your project or git clone the desired repository into your local project directory.  

### Reopen Project in Python Dev Container
2. Open your project directory in Visual Studio Code.

3. Confirm the following Extensions are installed in your Visual Studio Code instance.
    * Dev Containers
    * Remote Development

4. Reopen the active project directory in a Dev Container.
    * Open the Command Palette and run the **Dev Containers: Reopen in Container** command. 
    * Alternately, if missing, run the **Dev Containers: Open Folder in Container...** command, selecting the project directory when prompted.
    * From the Command Palette, select the following configuration options:
        * **From a predefined container configuration definition...**
        * **Python 3 & PostgreSQL** 
        * **3.11-bullseye (default)** 
        * **Ok** or **[Enter]**
    * Allow the Dev Containers extension to complete the process of downloading the configuration template and building a new Ubuntu-based Dev Container instance pre-configured for Python development.  
    * Some things to note, on completion:
        * The extension will automatically start up and attach itself to the newly created Dev Container for development activities. 
        * The extension will configure your Dev Container to bind mount your local, active workspace, overriding the default mount defined in the configuration template.

### Install Development Python Interpreter with pyenv
5. Open the Visual Studio Terminal and use the following steps to install **pyenv** within your Python Dev Container.
    * Run the following command to download and execute the installation script maintained at [**pyenv-installer**](https://github.com/pyenv/pyenv-installer/):
        ```
        curl https://pyenv.run | bash
        ```
    * Open your **.profile** file using the following command:
        ```
        code ~/.profile
        ```
    * Append and save the following bash commands to the end of the file:
        ```
        export PYENV_ROOT="$HOME/.pyenv"
        command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
        eval "$(pyenv init -)"
        ```
    * Open your **.bashrc** file using the following command:
        ```
        code ~/.bashrc
        ```
    * Append and save the following bash commands to the end of the file:
        ```
        export PYENV_ROOT="$HOME/.pyenv"
        command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
        eval "$(pyenv init -)"
        ```
    * Close any open Visual Studio Code Terminal sessions.

6. Reopen the Visual Studio Terminal and use the following steps to install your development Python interpreter within your Dev Container. 
    * Update pyenv, its plugins including the list of available versions:
        ```
        pyenv update
        ```
    * List versions installed:
        ```
        pyenv versions
        ```
    * List available versions available for download:
        ```
        pyenv install --list
        ```
    * Install desired version of Python interpreter:
        ```
        pyenv install <version>
        ```
    * Set desired global version of Python interpreter:
        ```
        pyenv global <version>
        ```

### Create Development Virtual Environment with pipenv
6. The **pip** utility gets installed with your global Python interpreter.  Use **pip** to install **pipenv**.
    * Update pip package, using pip:
        ```
        pip install --upgrade pip
        ```
    * Install pipenv package globally for the current Dev Container/pyenv environment user:
        ```
        pip install pipenv --user
        ```

7. The **pipenv** tool supports virtual environment management and more robust dependency management over **pip**.  Use **pipenv** to create a new a Python virtual environment within your Dev Container.
    * Create a new Python virtual environment using your desired Python interpreter version:
        ```
        pipenv --python <project version>
        ```
    * Close any open Visual Studio Code Terminal sessions.

### Set Python Interpreter Version Used by Visual Studio Code IDE
8. Visual Studio Code will attempt to "find" the correct version of Python interpreter, but it's better to specify the Python interpreter that should be used explicitly.
    * Open the Command Palette and run the **Python: Clear Cache and Reload Window** command.
    * Open the Command Palette and run the **Python: Select Interpreter** command.
    * From the Command Palette, select the Python interpreter entry with the **Pipenv** designation on the right.

Congratulations, your Python Environment with **pyenv** and **pipenv** is ready for use with Visual Studio Code!
