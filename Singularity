BootStrap: docker
From: centos:7

%runscript
   #"I can put here whatever I want to happen by default when the user runs the container"
   pymol

%post
    yum install -y curl bzip2
    # System dependencies for PyMOL
    yum install -y libGL libGLU qt5-qtbase-gui

    # download and install miniconda2
    if [ ! -x "/opt/miniconda2/bin/conda" ]; then
      curl -sSL -O https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
      bash Miniconda2-latest-Linux-x86_64.sh -p /opt/miniconda2 -b
      rm -fr Miniconda2-latest-Linux-x86_64.sh
    fi

    # use conda to install some bioinfo tools
    export PATH=/opt/miniconda2/bin:$PATH
    conda install --yes -c schrodinger pymol=2.2.0

%environment
    export LANG=en_US.UTF-8
    export LANGUAGE=en_US:en
    export LC_ALL=en_US.UTF-8
    export PATH=/opt/miniconda2/bin:$PATH

%apphelp PyMOL
    "PyMOL version 2.2.0"

%apprun PyMOL
    /opt/miniconda2/bin/pymol
