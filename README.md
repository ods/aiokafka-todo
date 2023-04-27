## Import needed code from python-kafka

### Why?

It's not supported, issues and PRs (including [my one from 2021](https://github.com/dpkp/kafka-python/pull/2285)) are ignored. With it we can't provide compatibility with newer versions of Python ([an example of problem](https://github.com/dpkp/kafka-python/pull/2304)).

### How?

We can filter out needed modules with full history using [`filter-repo`](https://github.com/newren/git-filter-repo) tool. Also something similar can be done with `git subtree add ...`. But the history will be destroyed by current merge policy (squash).

### What stops us from doing it?

Probably nothing, this step doesn't depend on anything else. But we have to look through issues/PRs for kafka-python and apply them to our code base.


## Apply black autoformatting

### Why?

To make style consistent and simple to manage.

### What stops us from doing it?

* It spoils attribution for the code. It would be nice to find a solution that allows us to keep it. But we can mitigate this issue by providing `.git-blame-ignore-revs` file and using `git blame --ignore-revs-file` (see [docs](https://docs.github.com/en/repositories/working-with-files/using-files/viewing-a-file#ignore-commits-in-the-blame-view)). Probably we should also look through the history and add other commits to ignore, if they are not mixed up by "squash" policy.
* All the existing PRs have to be rewritten. We have to either close or merge them before doing this.


## Add type annotations

### Why?

Nowadays libraries are expected to be typed.

### What stops us from doing it?

It's better to do massive changes after autoformatting.


## Rewrite tests with pytest

### Why?

We have a lot of problems in tests, they are hard to read. It's easier to fix the with `pytest`s fixtures and `pytest-asyncio`.

### What stops us from doing it?

It's better to do massive changes after autoformatting.


## New kafka versions

### What stops us from doing it?

* The current image doesn't seem to work for kafka 3.
* No access to Docker Hub account. Probably we can move images to GitHub?


## Fix flaky test

### What stops us from doing it?

The test is flaky by nature (race), we have to come with some solution for it.


## Replace codec dependencies

### Why?

Some of them are not supported, we already have problems with python-snappy in Python 3.11.


### What?

One probable candidate is [cramjam](https://github.com/milesgranger/pyrus-cramjam) could replace them all. According to [download statistics](https://pepy.tech/project/cramjam) it's much more popular, than aiokafka itself.


## Move from setup.py to pyproject.toml (PEP-517)

### Why?

Both direct invocation of setup.py and setuptools [are effectively deprecated](https://blog.ganssle.io/articles/2021/10/setup-py-deprecated.html). The modern approach is to use `pyproject.toml`

### What?

I personally prefer `hatch`. But we have to find out if it plays well with cython.
