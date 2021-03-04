# OSS-test1-cribsheet
Cribsheet for exam 1 of OSS

# Table of contents:

[General Open source and random things](#OSS)

[Git](#Git)

[Documentation](#Documentation)

[Licenses](#Lisence)

[Build Systems](#Build)

# OSS

TODO:

## OSS development

## Random things:

**Regex rules:**


# Git
TODO:

## Some git commands:

**git add:**
**git commit:**
**git pull:**
**git checkout:**
**git branch:**
**git push:**
**git log:**
**git status:**
**git diff:**
**git tag:**
**git rebase:**
**git merge:**


# Documentation
TODO:

## Markdown

**basic markdown**
```
# title
# subtitle

insert picture: ![](~/Path/To/image.png)

hyperlink:

list:

1. item 1
2. item 2

```

## Latex

## Github wiki

# License

**Criteria for OSI License**

  1. TODO
  2. TODO
  3. TODO
  4. TODO

**Open source vs Public domain**

**Open source vs Open Core**

**License and characteristics:**

* **MIT:**
  * characteristics:
    * TODO
  * How it affects project:
    * Use:
    * Creation:
    * Distribution:

* **BSD:**
  * characteristics:
    * TODO
  * How it affects project:
    * Use:
    * Creation:
    * Distribution:

* **GPL:**
  * characteristics:
    * TODO
  * How it affects project:
    * Use:
    * Creation:
    * Distribution:

* **LGPL:**
  * characteristics:
    * TODO
  * How it affects project:
    * Use:
    * Creation:
    * Distribution:

* **AGPL:**
  * characteristics:
    * TODO
  * How it affects project:
    * Use:
    * Creation:
    * Distribution:

* **Mozilla**
  * characteristics:
    * TODO
  * How it affects project:
    * Use:
    * Creation:
    * Distribution:

* **Apache:**
  * characteristics:
    * TODO
  * How it affects project:
    * Use:
    * Creation:
    * Distribution:

# Build



## Compiling Libraries

### Object Files

Object files are an intermediate step in compilation. They are *mostly* machine code, but have additional symbols used by the linker when linking to external libraries. 

```bash
cc -c source.c -o object.o
```

### Shared Libraries

Shared libraries are linked **at runtime**

Note: Shared libraries must be compiled as **address independent** objects (`-fPIC`)

```bash
cc -fPIC -c source1.c -o object1.o
cc -fPIC -c source2.c -o object2.o
...
cc -shared -o libshared.so object1.o object2.o ...
cc object.o libshared.so -o binary_out -Wl,-rpath='$ORIGIN'
```



### Static Libraries

Static libraries are linked **at compile time**

```bash
ar qc libstatic.a object1.o object2.o ...
cc object.o libstatic.a -o binary_out
```



## Make

A `Makefile` expresses **targets**, **dependencies**, and **commands**

```makefile
all: hi1 hi2
hi1: hi1.o libhello.so
        cc hi1.o libhello.so -o hi1 -Wl,-rpath='$$ORIGIN'
hi2: hi2.o libhello.so
        cc hi2.o libhello.so -o hi2 -Wl,-rpath='$$ORIGIN'
hi1.o: hi1.c
        cc -c hi1.c -o hi1.o
hi2.o: hi2.c
        cc -c hi2.c -o hi2.o
libhello.so: hello1.o hello2.o
        cc -shared -o libhello.so hello1.o hello2.o
hello1.o: hello1.c
        cc -fPIC -c hello1.c -o hello1.o
hello2.o: hello2.c
        cc -fPIC -c hello2.c -o hello2.o
```

* `all` is a **target**
  * `all` is the default target when the command `make` is ran. I _think_ the `all` target is required for all Makefiles.
* `hi1` and `hi2` are **dependencies** of `all`
  * dependencies can be
    1. targets (eg. `hi1`, `hi2`)
    2. explicitly defined files (eg. `hello1.c`, `hello2.c`)
       - changing an explicitly defined dependency **will** force the target to be rebuilt when `make` is re-ran
    3. implicitly defined files (eg. `hello1.h`, `hello2.h`)
       - changing an implicitly defined dependency **will not** force the target to be rebuilt when `make` is re-ran
* `cc hi1.o libhello.so -o hi1 -Wl,-rpath='$$ORIGIN'` is a **command**



## Cmake

AHHHHHHHH

## Regex
Run through this tutorial as a refresher: https://regexone.com/
