# `make` Utility
Normally a project contains multiple no of files, moreover each file can be of different format or language. As such all different files will need to be properly compiled, linked, packed for the project to be successfully compiled and executed.

Now suppose a project has 5-6 files, it can be compiled by using 10 commands manually one by one.

But suppose a project has got 1000's of modules each module containing 1000's of files, to compile this project, it may require millions of commands. Even if someone manually types these commands once to compile the project, What will happen when one(or multiple) file(s) will be changed. It's not possible to type all those commands manually more than once, even once will be more than what's possible.

To overcome this challange we use the `make` utility.

## How to use `make`
We use `make` as follows:
> Note : For the `make` utility to work we need to write a `Makefile` (`Makefile` will be discussed later).

1.  To compile the project we use `make` or generally we use `make all` OR `make build`.
    -   needs a rule named `all` OR `build` in the `Makefile`.
2.  If a module is named say for example `edit` we compile it selectively using `make edit`.
    -   needs a rule named `edit` in the `Makefile`.
3.  To clean the project directory we use `make clean`.
    -   needs a \'Phony\' rule named `clean` in the `Makefile`.
4.  To install the software project we use `make install`.
    -   needs a \'Phony\' rule named `install` in the `Makefile`.

# Next
## [Makefile](Makefile/Makefile-Basics.md)
