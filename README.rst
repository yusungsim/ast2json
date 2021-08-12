Introduction and Usage
===========

This is a fork of [YoloSwagTeam/ast2json](https://github.com/YoloSwagTeam/ast2json),
which is modified for personal use. The main differnces are as follows.

1. Instead of packaging it as pip package as original, user can just clone this package
   in their own python package and use it.

   ```zsh
   ├── some_other_file_u_want_to_use.py
   ├── ast2json
   │   ├── __init__.py
   │   ├── ast2json.py
   │   ├── py2
   │   │   └── __init__.py
   │   ├── py3
   │   │   ├── __init__.py
   │   │   └── __pycache__
   │   │       └── __init__.cpython-39.pyc
   │   └── types.py
   ```  

   ```py
   # some_other_file_u_want_to_use.py
   from ast2json import ast2json, str2json
   ...
   ```

2. Additional support for Ellipsis constant. Ellipsis is an constant used for
   Python's list slice.

   ```py
   arr = some_list()
   arr[..., 0:4] # think of it as `arr[Ellipsis, 0:4]`
   ```

   Original ast2json did not support Ellipsis constant, thus raising exception on
   encountering such code. This version supports parsing the Ellipsis and dumps
   as JSON. It parses Ellipsis object as following JSON.

   ```json
   {
      "_type": "Ellipsis",
      "value": null
   }
   ```

License
======

Refer to `ast2json.py` for original credits of the source code.
