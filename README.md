## Drop support for kafka 0.x and 1.x

### Why?

Probably nobody develop for them now. Nobody creates new images for them. The code could be simplified.

### What stops us from doing it?

Before doing so it would be nice to:

* Get usage statistics by version to estimate the impact.
* Decide the way how we handle unsupported versions.

## Import needed code from python-kafka

### Why?

It's not supported, issues and PRs (including [my one from 2021](https://github.com/dpkp/kafka-python/pull/2285)) are ignored. With it we can't provide compatibility with newer versions of Python ([an example of problem](https://github.com/dpkp/kafka-python/pull/2304)).

[The statement from the author](https://github.com/dpkp/kafka-python/issues/2290#issuecomment-1009133967).

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


## Fix flaky tests

[The list of flaky tests](./flaky-tests.md).


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


## Update github actions

### Why?

We already get warnings for them:

```
Node.js 12 actions are deprecated. Please update the following actions to use Node.js 16: actions/checkout@v2, actions/setup-python@v2, actions/cache@v1. For more information see: https://github.blog/changelog/2022-09-22-github-actions-all-actions-will-begin-running-on-node16-instead-of-node12/.
```


## Fix towncrier flow

We need to update instruction and keep `CHANGES` directory.  Otherwise supporters [don't understand what to do](https://github.com/aio-libs/aiokafka/pull/912#issuecomment-1660290007).


## Verify protocol structs, use names as in spec

[Protocol specification](https://kafka.apache.org/protocol)
