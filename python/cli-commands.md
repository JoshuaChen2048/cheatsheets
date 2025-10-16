# Python Cheatsheet - Command Line Commands

## [pyenv](https://github.com/pyenv/pyenv)

A tool for managing multiple Python versions.

```bash
# Install or remove a specific Python release
pyenv install 3.11.4
pyenv uninstall 3.8.12

# Show pyenv root and available virtualenvs
pyenv root
pyenv virtualenvs

# Set the interpreter version
pyenv global 3.11.4  # Set the global default
pyenv local 3.11.4   # Set for the project (creates .python-version)
pyenv shell 3.10.6   # Set for the current shell session
```

## [Python](https://docs.python.org/3/)

The Python interpreter itself.

```bash
python -V                               # Print the Python version
python run_me.py                        # Run a script file
python -m http.server 9090              # Run a library module as a script
python -c "import sys; print(sys.version)" # Execute short inline code
python -i demo.py                       # Run a script and drop to the interactive prompt
```

## [venv](https://docs.python.org/3/library/venv.html)

A tool for creating isolated Python environments.

```bash
# Create and manage a virtual environment
python -m venv env                  # Create a virtual environment named "env"
source env/bin/activate             # Activate on Unix/macOS
.\env\Scripts\Activate.ps1          # Activate on Windows PowerShell
env\Scripts\activate.bat            # Activate on Windows CMD
deactivate                          # Deactivate the environment

# Quick recreation
rm -rf env && python -m venv env
source env/bin/activate
```

## [pip](https://pip.pypa.io/en/stable/)

The package installer for Python.

```bash
# Manage packages
pip install flask                     # Install a package
pip install --upgrade flask           # Upgrade a package
pip uninstall flask                   # Uninstall a package
pip install -r requirements-dev.txt   # Install packages from a requirements file
pip freeze --local > requirements.txt # Save current environment packages to a file

# Inspect packages
pip list                              # List installed packages
pip list --outdated                   # List outdated packages
pip show flask                        # Show metadata for a package
pip check                             # Verify installed packages have compatible dependencies
```

## [uv](https://pypi.org/project/uv/)

A fast, lightweight Python package and environment manager.

```bash
# Create and manage a virtual environment
uv venv                                # Create a virtual environment
source .venv/bin/activate              # Activate the environment

# Initialize a uv-managed project (creates uv.lock / uv.toml)
uv init                                # Create project metadata and lock file

# Add/install a dependency
uv add requests                        # Add and install 'requests' into the project environment
uv add "django@^4.2"                  # Add Django with semver constraint

# Sync environment with lockfile
uv sync                                # Install dependencies from uv.lock

# Remove a dependency
uv remove requests                     # Remove 'requests' from project

# Update dependencies (single or all)
uv update requests                     # Update a single package
uv update                              # Update all packages according to constraints

# Run a script inside the uv environment
uv run python manage.py runserver      # Run commands with the project's env active

# Export lockfile to requirements.txt
uv export -o requirements.txt          # Useful for CI or legacy tools
```

## [pipx](https://pypa.github.io/pipx/)

Install and run Python applications in isolated environments.

```bash
# Manage CLI tools
pipx install ruff                      # Install a tool
pipx upgrade ruff                      # Upgrade a tool
pipx upgrade-all                       # Upgrade all tools
pipx uninstall ruff                    # Uninstall a tool
pipx list                              # List installed tools

# Run an app without installing
pipx run cowsay "Hello, World!"        # Run the latest version of a package
pipx run pycowsay --version 2.0.0 "Hi" # Run a specific version
```

## [pytest](https://docs.pytest.org/)

A framework for writing and running tests.

```bash
# Run tests
pytest                                 # Run all tests in the current directory
pytest tests/test_app.py               # Run tests in a specific file
pytest tests/ -k "test_login"          # Run tests with names matching a keyword
pytest -m "slow"                       # Run tests with a specific marker
pytest -x                              # Stop after the first failing test

# Control output
pytest -v                              # Increase verbosity
pytest -q                              # Decrease verbosity
pytest --tb=short                      # Shorter traceback format
```

## [ruff](https://docs.astral.sh/ruff/)

An extremely fast Python linter and code formatter.

```bash
# Linting and formatting
ruff check .                           # Lint all files in the current directory
ruff check . --fix                     # Lint and automatically fix issues
ruff format .                          # Format all files in the current directory

# Rules management
ruff rule --all                        # Show all available rules
ruff rule --select I001                # Explain a specific rule
```