###########################
Numpy Windows wheel builder
###########################

Build numpy wheels with MSVC and pre-built ATLAS binaries.

See ``appveyor.yml`` for the build process as applied on Appveyor.

If you are doing the build manually:

* Make a virtualenv to work in, and activate it;
* ``pip install -r requirements.txt``;
* To build a wheel with old-style Windows platform tags (more compatible with
  old versions of pip), do ``pip install wheel==0.26``;
* Clone the numpy github repo, checkout the version you want to build, and
  run the build script::

    git clone https://github.com/numpy/numpy.git
    cd numpy
    git checkout v1.11.0
    python ..\build_numpy.py

This should build you a numpy wheel with the ATLAS binary packaged inside.  It
will be in the ``dist`` subdirectory of the numpy source tree.

The ``appveyor.yml`` script uploades the wheels to a Rackspace container at:

* http://58688808cd85529d4031-38dee5dca2544308e91131f21428d924.r12.cf2.rackcdn.com
* https://84c1a9a06db6836f5a98-38dee5dca2544308e91131f21428d924.ssl.cf2.rackcdn.com

The contents via the HTTPS URL seems to get updated more slowly than via the
HTTP URL, so if you need the binaries quickly, prefer the HTTP URL.

Also, the Rackspace CDN takes some time to update, so leave at least 15
minutes after the end of a build, before fetching the built binary from the
Rackspace URLs above.

ATLAS libraries built laboriously on a dedicated machine with Clint Whaley's
help.

``lib`` and ``exp`` files generated by MSVC ``lib.exe`` tool, as described
here:
http://stackoverflow.com/questions/9946322/how-to-generate-an-import-library-lib-file-from-a-dll
