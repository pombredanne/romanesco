Cardoon
=======

A flexible, simple script execution engine.

It has scripting support for Python and R, automatic type conversion, and URI serialization.

Get Started
===========

Get it:
```
git clone https://github.com/arborworkflows/cardoon.git
cd cardoon
```

Test it:
```
python -m unittest -v tests.table_test
python -m unittest -v tests.tree_test
```

Some things not working? You can install a few things so they do.
For example, install [MongoDB](http://www.mongodb.org/) and [R](http://www.r-project.org/),
in addition to their Python bindings:
```
pip install pymongo rpy2  # may need sudo
```
You'll need to get a MongoDB server listening on localhost by running `mongod`.

In R, you'll need to install some stuff too, currently just the `ape` package:
```
install.packages("ape")
```

Some things depend on VTK Python bindings. Cardoon uses some features from
cutting-edge VTK,
so you'll likely need to build it from scratch (takes ~30 minutes).
First get [CMake](http://www.cmake.org/), then do the following:
```
git clone git://vtk.org/VTK.git
cd VTK
mkdir build
cd build
cmake .. -DVTK_WRAP_PYTHON:BOOL=ON -DBUILD_TESTING:BOOL=OFF
make
export PYTHONPATH=`pwd`/Wrapping/Python:`pwd`/lib
python -c "import vtk"  # should work without an error
````

Want to run things remotely? On the server:
```
python -m cardoon
```

On the client:
```
python clients/client.py
```