## Drop support for kafka 0.x and 1.x

### Why?

Probably nobody develop for them now. Nobody creates new images for them. The code could be simplified.

### What stops us from doing it?

Before doing so it would be nice to:

* Get usage statistics by version to estimate the impact.
* Decide the way how we handle unsupported versions.


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
The following actions uses node12 which is deprecated and will be forced to run on node16: actions/checkout@v2, actions/setup-python@v2, actions/cache@v1. For more info: https://github.blog/changelog/2023-06-13-github-actions-all-actions-will-run-on-node16-instead-of-node12-by-default/

Node.js 16 actions are deprecated. Please update the following actions to use Node.js 20: actions/checkout@v2, actions/setup-python@v2, actions/cache@v1. For more information see: https://github.blog/changelog/2023-09-22-github-actions-transitioning-from-node-16-to-node-20/.

The `set-output` command is deprecated and will be disabled soon. Please upgrade to using Environment Files. For more information see: https://github.blog/changelog/2022-10-11-github-actions-deprecating-save-state-and-set-output-commands/
```


## Fix towncrier flow

We need to update instruction and keep `CHANGES` directory.  Otherwise supporters [don't understand what to do](https://github.com/aio-libs/aiokafka/pull/912#issuecomment-1660290007).


## Verify protocol structs, use names as in spec

[Protocol specification](https://kafka.apache.org/protocol)


## Replace custom `WeakMethod` with standard one

[weakref.WeakMethod](https://docs.python.org/3/library/weakref.html#weakref.WeakMethod)
