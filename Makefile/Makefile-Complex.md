# Advanced Features of `Makefile`

## Including other Makefiles
We can separate different prerequisites / dependencies in different Makefile(s). But then we must include those Makefile(s) to the main Makefile for it to run correctly. We do this as follows:

```makefile
include file1 file2 file3 $(var_filenames)

# See we can provide file names, 
# variable containing file names
# and also we can use wildcard characters,

include *.mk

# the Above will include all files ending with 
# ".mk" present in the current directory.
```

## may add something

## ( Normal | Order only ) Prerequisite

## Wildcards

