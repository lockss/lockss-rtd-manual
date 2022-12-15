# `lockss-rtd-manual`

This repository contains the source for the [LOCKSS System Manual](https://docs.lockss.org/projects/manual/) project on Read The Docs.

**WARNING:** This documentation is versioned and the `master` branch does not contain anything that can be easily viewed online:

*   There is one branch per released version.

*   Read The Docs is configured so that the pseudo-version `latest` is a synonym for the branch named after the actual latest release.

*   Read The Docs is configured so that by default, the version is `latest`.

*   Additionally, there is a branch called `unstable` that is meant to contain the currently unreleased version (equivalent of `develop` branch).

### Getting Started

This LOCKSS System Manual uses [Sphinx](https://www.sphinx-doc.org/), a Python documentation generator, which uses the 
[reStructuredText](https://docutils.sourceforge.io/rst.html) markup language by default. Contributors to the LOCKSS
System Manual are encouraged to set up a Sphinx environment for rapid building and testing of source material on their 
local machine. Follow the instructions below to get started:

#### First time setup:

1. Clone the Git repository and change your working directory, if you haven't done so already:
```shell
git clone https://github.com/lockss/lockss-rtd-manual.git
cd lockss-rtd-manual
```

2. Create a Python virtual environment and activate it:
```shell
python3 -m venv .venv
source .venv/bin/activate
```

3. Install dependencies into the virtual environment using `pip`:
```shell
pip3 install -r requirements.txt
```

#### Building the LOCKSS System Manual:

1. Activate the Python virtual environment, if it is not already activated:
```shell
source .venv/bin/activate
```

2. Change the working directory to `docs` and build using `make`:
```shell
cd docs
make html
```
**Note**: The provided `Makefile` offers many other build targets. Run `make` alone to see all options. The above builds
source material to HTML output.

3. Open `_build/html/index.html` in a web browser to view and navigate the built documentation.