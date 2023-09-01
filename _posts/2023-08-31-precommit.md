---
layout: post
title:  "Precommit"
date:   2023-08-31 18:00:00
categories: wiki
tags: [precommit,ci]
lang: en
ref: precommit
description: Better code using pre-commit hooks
img: https://images.unsplash.com/photo-1516321497487-e288fb19713f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80
---

## Better Git Hooks

[Git hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks) are scripts that are trigered when some action from Git is perfomed. They can run before or after common actions such creating a commit, push or pull.

This can be used to define a local quality gate for the code that is triggered before each commit, push or pull action. Therefore, they enable catching errors ahead and preventing defective code been commited or sended to the remote server. 

One can create any hook by adding a executable script at the `.git/hooks` stored in the repository home. But there is a more pratical for managing and maintaining Git hooks by using the Python package [Pre-commit](https://pre-commit.com/).

It uses a yaml config file placed in the repository as source, install and run all hooks. 


### Installing Pre-commit

It can be installed using pip using the following command:

```bash
pip install pre-commit
```

### Basic Configuration

Once pre-commit is installed, you can create a file `.pre-commit-config.yaml` in the repository root with the following content:

```yaml
repos:
-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
    -   id: end-of-file-fixer
    -   id: check-yaml
    -   id: check-added-large-files
    -   id: check-merge-conflict
```

The hooks [end-of-file-fixer](https://github.com/pre-commit/pre-commit-hooks#end-of-file-fixer), [check-yaml](https://github.com/pre-commit/pre-commit-hooks#check-yaml), [check-added-large-files](https://github.com/pre-commit/pre-commit-hooks#check-added-large-files), [check-merge-conflict](https://github.com/pre-commit/pre-commit-hooks#check-merge-conflict) are already defined inside the the repository https://github.com/pre-commit/pre-commit-hooks.

In order to install them, just run the following command

```bash
pre-commit install -c .pre-commit-config.yaml
```

This will download the repository and install the hooks inside the `.git/hooks` folder. Then, the pre-commit hooks registered will run everytime that you run `git commit` before the commit be generated.

#### Using hooks with Parameters

pre-commit enable also to use some tools

For instance, if you would like to use the following command with all python files inside the a repository:

```bash
yapf --style=pep8 --parallel --in-place
```

This can be translated to the following config lines:

```yaml
repos:
# ...
-   repo: https://github.com/google/yapf                     # yapf repository url
    rev: v0.40.0                                             # repository version to be used
    hooks:
    -   id: yapf                                             # id (used to call hook individualy)
        name: Ensure PEP-8 complience for all Python files   # short description
        args:                                                # Define arguments to be passed whenever yapf is called 
          - '--style=pep8'                                   # yapf arg: Ensure PEP-8
          - '--parallel'                                     # yapf arg: Allow run in parallel
          - '--in-place'                                     # yapf arg: edit file and fix error found
        files: \.(py)$                                       # Apply hook to all *.py files and trigger hook whenever a python file is changed
```

### Using local commands as custom hooks

Some tools might be available only localy. In this case, you can use the `repo: local` combined with `language: system` to translate the command required by the tool to hook in the yaml config file.

For instance, the following command

```bash
pytest --junitxml=pytest.xml --cov-report=xml --cov=src -v
```

Can be translated to

```yaml
repos:
# ...
-   repo: local
    hooks:
    -   id: pytest
        name: Ensure all tests are passing
        entry: pytest
        language: system                    # Uses entry as direct system command
        args:
          - '--junitxml=pytest.xml'
          - '--cov-report=xml'
          - '--cov=src'
          - '-v'
        files: \.(py)$                      # Trigger hook whenever a python file is changed
        always_run: true                    # This will the command will always run
        pass_filenames: false               # This will prevent the files to be passed to command since some tools might not need.
```

## Git++

There so much more! Go ahead check the documentation page at https://pre-commit.com/ to enable even more powerful hooks.
