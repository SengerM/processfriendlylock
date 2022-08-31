# processfriendlylock

A lock that is compatible with multiprocess applications that make use of [`BaseManager`](https://docs.python.org/3/library/multiprocessing.html#multiprocessing.managers.BaseManager) objects. Surprisingly [Python's locks](https://docs.python.org/3/library/multiprocessing.html#multiprocessing.managers.BaseManager) are not compatible with its own `BaseManager` objects, that is why I made this. The locks implemented in this package should also work in a multithread environment.

This package implements the locks as files in the hard drive, so don't expect high speed.

## Installation

```
pip3 install git+https://github.com/SengerM/processfriendlylock
```

## Usage

```Python
from processfriendlylock.CrossProcessLock import CrossProcessNamedLock

lock = CrossProcessNamedLock(Path.home())

with lock('my name'):
	do_something()
```

As seen you have to provide a name for this locks, which will allow you to acquire it only if it is free or if it is already acquired by yourself. Otherwise it will block the execution at that point.

The code in [this link](https://github.com/SengerM/robocold_beta_setup/blob/be5bc3f8ae00821982e1a611b5bb0d708d96e3b1/measuring_scripts/TheSetup.py) can provide further help, it uses a pre-packaged version of this but it is the same code.
