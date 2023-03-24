This demonstrates the error with getting to use iwyu with nixpkgs

```console
$ direnv allow .
$ rm -rf build/
$ cmake -Bbuild -GNinja
$ cmake --build build
```

- Expected: Warning about excess includes.
- Got: No warning

Also tried running it manually, it hits
https://github.com/NixOS/nixpkgs/issues/189753

```console
$ iwyu_tool.py -p build/
/tmp/nixpkgs-iw-yu-error/main.c:1:10: fatal error: 'stdio.h' file not found
#include <stdio.h>
         ^~~~~~~~~

/tmp/nixpkgs-iw-yu-error/main.cpp:1:10: fatal error: 'iostream' file not found
#include <iostream>
         ^~~~~~~~~~
```
