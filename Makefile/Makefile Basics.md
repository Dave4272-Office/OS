# Simple Makefile

## Comments
The syntax of comments in a make file is:

```make
# this is a comment
```

> *Always use comments*

## Rules
All makefile rules are of the form:

```make
target: dependencies
[Tab]recipe
	...
```

1. **target** is usually the name of a file that is generated \
by the rule.

2. **dependencies** are first searched if they are present before executing the rule. If any dependency is missing then its rule will be executed first. And when rule for that dependency is not present `make` will return an error.

3. [Tab] is compulsory before specifying each recipe for that target. And use only the `TAB` for this purpose.

4. The **recipe** in a target are nothing but the command statements required to generate the target. There can be multiple recipe line in a rule.

A make file contains at least one rule and may contain multiple rules.

### Example Makefile v1

```make
# The following is the first rule
# this rule will be executed first
all: main

# This Rule creates the dependency main of all
main: main.o hi.o
	g++ main.o hi.o -o main

# This Rule creates the dependency main.o of main
main.o: main.c main.h
	g++ -c -Wall main.c

# The above rule will not run if main.c and main.h
# is not present in the project directory

# This Rule creates the dependency hi.o of main
main.o: hi.c hi.h
	g++ -c -Wall hi.c

# The above rule will not run if hi.c and hi.h
# is not present in the project directory
```

## Variables
In the above Makefile to change the compiler or compile options or link options we have to change multiple lines. which can get tedious.

To Make it easy we use variables. Variables are of the following form:

```make
var_name = var_string_may contain space
```

And we use the variable like:

```make
$(var_name)
```

The above makefile with variables:

### Example Makefile v2

```make
# Let CC specify the compiler
CC = g++

# Let CFLAGS contain the Compilation Flags
CFLAGS = -c -Wall

# Let OBJ contain list of all final Object Files
OBJ = main.o hi.o

# The following is the first rule
# this rule will be executed first
all: main

# This Rule creates the dependency main of all
main: $(OBJ)
	$(CC) $(OBJ) -o main

# This Rule creates the dependency main.o of main
main.o: main.c main.h
	$(CC) $(CFLAGS) main.c

# The above rule will not run if main.c and main.h
# is not present in the project directory

# This Rule creates the dependency hi.o of main
hi.o: hi.c hi.h
	$(CC) $(CFLAGS) hi.c

# The above rule will not run if hi.c and hi.h
# is not present in the project directory
```

## Ignoring Certain Recipies
`make` has an implicit rule to update an `.o` file using `cc -c` corresponding to `.c` file.
as such recipies and dependencies of such `.o` and `.c` can be omitted.

### Example Makefile v2 minimized (if using cc)
Assume in the following we are using the cc compiler

```make
# Let CC specify the compiler
# CC = cc NOT REQUIRED

# Let CFLAGS contain the Compilation Flags
# CFLAGS = -c NOT REQUIRED

# Let OBJ contain list of all final Object Files
OBJ = main.o hi.o

# The following is the first rule
# this rule will be executed first
all: main

# This Rule creates the dependency main of all
main: $(OBJ)
	cc $(OBJ) -o main

# The recipe of the rules compressed
main.o: main.h
hi.o: hi.h
```

## Rules for cleaning the directory
We can specify rules for cleaning the working directory as follows

> Assuming `main` to be the final executable
> and `OBJ` variable to contain the list of all objects

```make
clean:
	rm main $(OBJ)
```

> *But so that the make interpreter doesn't get confused with an actual file*
> *`clean` we would write the clean rule in the following way*

```make
.PHONY : clean
clean :
	-rm main $(OBJ)
```

> *Always specify the clean rule at the end of the makefile*

The `clean` rule only runs when `make clean` is executed.

Our Makefile now looks s follows:

### Example Makefile v3

```make
# Let CC specify the compiler
CC = g++

# Let CFLAGS contain the Compilation Flags
CFLAGS = -c -Wall

# Let OBJ contain list of all final Object Files
OBJ = main.o hi.o

# The following is the first rule
# this rule will be executed first
all: main

# This Rule creates the dependency main of all
main: $(OBJ)
	$(CC) $(OBJ) -o main

# This Rule creates the dependency main.o of main
main.o: main.c main.h
	$(CC) $(CFLAGS) main.c

# This Rule creates the dependency hi.o of main
hi.o: hi.c hi.h
	$(CC) $(CFLAGS) hi.c

.PHONY : clean
clean :
	-rm main $(OBJ)
```
