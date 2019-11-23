# Implicit Rules of `make`

***Add Table of Contents***

## C Programs

```makefile
n.o: n.c
    $(CC) $(CPPFLAGS) $(CFLAGS) -c
```

## C++ Programs

```makefile
n.o: n.cc
    $(CXX) $(CPPFLAGS) $(CXXFLAGS) -c

n.o: n.cpp
    $(CXX) $(CPPFLAGS) $(CXXFLAGS) -c

n.o: n.C
    $(CXX) $(CPPFLAGS) $(CXXFLAGS) -c
```
> Suggested to use `.cc` instead of `.C`

## Assembling & Pre-Processing Assembler Programs

```makefile
n.o: n.s
    $(AS) $(ASFLAGS)

n.s: n.S
    $(CPP) $(CPPFLAGS)
```

## Linking Single Object Files (Complete Later)

```makefile
n: n.o
    $(CC) $(LDFLAGS) n.o $(LOADLIBES) $(LDLIBS)
```

## Yacc for C Programs

```makefile
n.c: n.y
    $(YACC) $(YFLAGS)
```

## Lex for C Programs

```makefile
n.c: n.l
    $(LEX) $(LFLAGS)
```

## Lint Libraries for C, Yacc, Lex Programs

```makefile
n.ln: n.c
    $(LINT) $(LINTFLAGS) $(CPPFLAGS) -i
```

# To be Continued and Made into Table if possible