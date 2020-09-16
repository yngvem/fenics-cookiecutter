# Cookiecutter template for projects using FEniCS
This is a template to create FEniCS driven applications and libraries.

## About
This cookiecutter template will create a folder with a VSCode-friendly development Docker container. In the .devcontainer folder, there is a Dockerfile that bootstraps the official FEniCS image, and installs the following libraries:

### Developer tools  (in requirements.txt)
 * flake8 (linter)
 * black (code formatter)
 * isort (import sorting)
 * bump2version (code version manager)
 * removestar (automatically remove *-imports with explicit list of used names)
 * sphinx (documentation)
 * numpydoc (documentation)
 * pytest (unit testing)
 * pytest-cov (unit testing)
 * pytest-randomly (unit testing)
 * coverage (unit testing)

### Upgraded libraries  (in requirements-upgrade.txt)
 * numpy (multidimensional arrays)
 * scipy (scientific code)
 * matplotlib (plotting)

### Notebook plugins (in .devcontainer/Dockerfile)
 * jupyter_contrib_nbextensions
 * jupyter_nbextensions_configurator

The Notebook plugins are also activated.

Then, when the Docker image is built, VScode will start a container, while forwarding the ports specified when running cookiecutter. Then, it will mount the project directory and install the code in [editable mode](https://packaging.python.org/guides/distributing-packages-using-setuptools/#working-in-development-mode). The library will by default have the following dependencies which then will be installed too

### Dependencies (used by code in /src/*) (in setup.cfg)
 * tqdm (progress bars)
 * pandas (tabular data)
 * numpy (multidimensional arrays)
 * scipy (scientific code)
 * matplotlib (plotting)

## Adding new libraries
Any additional libraries you use in the src/ folder should be added to setup.cfg and any you use in the notebooks, scripts, test and documentation folders should be added to requirements.txt. For more information about structuring dependencies, see [this tutorial](https://github.com/yngvem/python-project-structure).

Once new libraries are added to the correct files, rebuild the container (press the green button on the lower left side of VSCode and choose rebuild container).

## Documentation
To add documentation, run sphinx-quickstart. If you want to upload the documentation to readthedocs, you need to add a .readthedocs.yml file that contain the following text

```yaml
python:
   setup_py_install: true
```

to have readthedocs properly run your code.

## Further reading
For more information about how to structure Python projects, you can read [this tutorial](https://github.com/yngvem/python-project-structure).


## Credits
The cookiecutter is heavily inspired by *audreyfeldroy*'s [cookiecutter-pypackage](https://github.com/audreyfeldroy/cookiecutter-pypackage) template.