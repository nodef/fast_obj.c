# fast_obj

Because the world needs another OBJ loader.
Single header library, should compile without warnings in both C89 or C++.
Much faster (5-10x) than other libraries tested.
By [Richard Knight](https://github.com/thisistherk).

To use:

     fastObjMesh* mesh = fast_obj_read("path/to/objfile.obj");

     ...do stuff with mesh...

     fast_obj_destroy(mesh);

Note that valid indices in the `fastObjMesh::indices` array start from `1`.  A dummy position, normal and
texture coordinate are added to the corresponding `fastObjMesh` arrays at element `0` and then an index
of `0` is used to indicate that attribute is not present at the vertex.  This means that users can avoid
the need to test for non-present data if required as the vertices will still reference a valid entry in
the mesh arrays.

A simple test app is provided to compare speed against [tinyobjloader](https://github.com/syoyo/tinyobjloader) and
check output matches.

### Installation

Run:
```bash
$ npm i fast_obj.c
```

And then include `fast_obj.h` as follows:
```c
#include "node_modules/fast_obj.c/fast_obj.h"
```

You may also want to include `fast_obj.c` as follows:
```c
#ifndef __FAST_OBJ_C__
#define __FAST_OBJ_C__
#include "node_modules/fast_obj.c/fast_obj.c"
#endif
```

This will include both the function declaration and their definitions into a single file.

### Version 1.3

Version 1.3 makes a small change to the API.  Textures are now stored in a separate array on the
`fastObjMesh` structure, and are referenced by index from materials, instead of being referenced
by the material directly.

<br>
<br>


[![ORG](https://img.shields.io/badge/org-nodef-green?logo=Org)](https://nodef.github.io)
![](https://ga-beacon.deno.dev/G-RC63DPBH3P:SH3Eq-NoQ9mwgYeHWxu7cw/github.com/nodef/fast_obj.c)
[![SRC](https://img.shields.io/badge/src-repo-green?logo=Org)](https://github.com/thisistherk/fast_obj)
