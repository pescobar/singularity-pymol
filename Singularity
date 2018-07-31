BootStrap: docker
From: ubuntu:18.04

%runscript
   pymol "$@"

%post
    
    export PYMON_VERSION="2.2.0"

    # install build dependencies for PyMOL
    apt-get update
    apt-get -y install build-essential python-dev python-pmw libglew-dev \
      freeglut3-dev libpng-dev libfreetype6-dev libxml2-dev \
        libmsgpack-dev python-pyqt5.qtopengl libglm-dev curl
    apt-get clean

    # download pymol code
    cd /usr/local/src
    curl -sSL -O https://github.com/schrodinger/pymol-open-source/archive/v2.2.0.tar.gz
    tar xf v${PYMON_VERSION}.tar.gz
    cd pymol-open-source-${PYMON_VERSION}
    python setup.py build install


%environment
    export LANG=en_US.UTF-8
    export LANGUAGE=en_US:en
    export LC_ALL=en_US.UTF-8
    export XDG_RUNTIME_DIR=""

%apphelp PyMOL
    "PyMOL version 2.2.0"

%apprun PyMOL
    pymol
