# C code - Find unused functions

minimal tools to find unused functions from C code

## Required:

- GCC 4.x
- nm (any version)
- find :)

## Use:

  - add CFLAGS:
```
  -ffunction-sections -fdata-sections
```
  - add LDFLAGS:
```
  -Wl,-gc-sections
```
  - (optionals) add to source files:
  
```
#include "find-unused-function.h"
```

and add prefix you export functions: FUNINLINE or FUNEXPORT (Required find-unused-function.h)
to Makefile, and make source

example:

```
 FUNINLINE int fun1(..) { .. }
 FUNEXPORT int fun2(..) { .. }
```

after run:
    
```
   find-unused-function.sh <path/compiled-name.bin> <path/object-dir/*.o> [<path/source-dir/*.c *.h>]
```
good idea, create link:

```
   ln -s /usr/bin/find-unused-function.sh /usr/bin/fuf
```
Result produce files:

```
   path/object-dir/DebugSymbol/symbols.*
```

