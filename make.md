# `make` Utility
Normally a project contains multiple no. of files, moreover each file can be of different format or language. As such all different files will need to be properly compiled, linked, packed for the project to be successfully compiled and executed.

Now suppose a project has 5-6 files, it can be compiled by using 10 commands manually one by one.

But suppose a project has got 1000's of modules and each of the module containing 1000's of files, to compile this project, it may require a bunch of commands. Even if someone manually typed these commands once to compile the project, What will happen when one (or multiple) file(s) have be changed? It's not possible to type all those commands manually more than once, So, one is the most number of times you want to do these things.

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
5.  Call a specific target:`make target`                               

6. Call a specific target, executing 4 jobs at a time in parallel: `make -j4 target`

7. Use a specific Makefile: `make --file file`

8. Execute make from another directory: `make --directory directory`

9. Force making of a target, even if source files are unchanged: `make --always-make target`

# Next
## [Makefile](Makefile\Makefile-Basics.md)
