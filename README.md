# Example application code for the "Architecture Patterns with Python" book

>## Downstream Fixes
>
>I, [evokateur](https://github.com/evokateur), will push fixes (mostly having to do
>with SqlAlchemy 2.0) that make the tests pass in chapter branches here.
>
>I will keep the version of Python at 3.8. This will be good for sanity checks as I'm
>[coding along](https://github.com/evokateur/python-architecture) in 3.12
>
>### Tests Passing Branches
>
> - [chapter_02_repository](https://github.com/evokateur/python-architecture-code/tree/chapter_02_repository) (works with SqlAlchemy 2.0)
> - [chapter_04_service_layer](https://github.com/evokateur/python-architecture-code/tree/chapter_04_service_layer) (ditto)
> - [master](https://github.com/evokateur/python-architecture-code) (SqlAlchemy pinned to <2 upstream, aha.)

## Chapters

Each chapter has its own branch which contains all the commits for that chapter,
so it has the state that corresponds to the _end_ of that chapter.
If you want to try and code along with a chapter,
you'll want to check out the branch for the previous chapter.

<https://github.com/cosmicpython/code/branches/all>

## Exercises

Branches for the exercises follow the convention `{chapter_name}_exercise`,
eg <https://github.com/cosmicpython/code/tree/chapter_04_service_layer_exercise>

## Requirements

- docker with docker-compose
- for chapters 1 and 2, and optionally for the rest: a local python3.8 virtualenv

## Building the containers

_(this is only required from chapter 3 onwards)_

```sh
make build
make up
# or
make all # builds, brings containers up, runs tests
```

## Creating a local virtualenv (~optional~ recommended)

```sh
python3.8 -m venv .venv && source .venv/bin/activate # or however you like to create virtualenvs
```

>_(I like to do it like this)_
>
>```
>pyenv shell 3.8
>python -m venv .venv
>source .venv/bin/activate
>```

```
# for chapter 1
pip install pytest 

# for chapter 2
pip install pytest sqlalchemy

# for chapter 4+5
pip install -r requirements.txt

# for chapter 6+
pip install -r requirements.txt
pip install -e src/
```

<!-- TODO: use a make pipinstall command -->

## Running the tests

```sh
make test
# or, to run individual test types
make unit-tests
make integration-tests
make e2e-tests
# or, if you have a local virtualenv
make up
pytest tests/unit
pytest tests/integration
pytest tests/e2e
```

## Makefile

There are more useful commands in the makefile, have a look and try them out.
