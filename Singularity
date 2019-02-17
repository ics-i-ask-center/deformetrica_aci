BootStrap: shub
From: willgpaik/centos7_aci

%setup
  
%files

%environment
#    export PATH LD_LIBRARY_PATH CPATH CUDA_HOME
#    LD_PRELOAD="/opt/eod/lib/libopentextdlfaker.so.3:/opt/eod/lib/libopentextglfaker.so.3 \
#        :/opt/eod/lib64/libopentextdlfaker.so.3:/opt/eod/lib64/libopentextglfaker.so.3"
#    export LD_PRELOAD
PATH="$PATH:/opt/sw/anaconda3/bin/"
export PATH

%runscript
  exec /opt/sw/anaconda3/envs/deformetrica/bin/deformetrica ""$@"


%post
    # Install Anaconda
    mkdir -p /opt/sw/
    cd /opt/sw/
    wget https://repo.anaconda.com/archive/Anaconda3-2018.12-Linux-x86_64.sh
    bash Anaconda3-2018.12-Linux-x86_64.sh -b -p /opt/sw/anaconda3
    ln -s /opt/sw/anaconda3/etc/profile.d/conda.sh /.singularity.d/env/conda.sh
    chmod a+x /.singularity.d/env/conda.sh
#    echo "source /opt/sw/anaconda3/etc/profile.d/conda.sh" >> ~/.bashrc
    source /opt/sw/anaconda3/etc/profile.d/conda.sh
    export PATH=$PATH:/opt/sw/anaconda3/bin/
    
    # Update conda
#    conda update -n base -c defaults conda
    conda update -y conda
    conda update -y anaconda

    conda create -y -n deformetrica && source activate deformetrica
    conda install -y -c pytorch -c conda-forge -c anaconda -c aramislab deformetrica
    conda update -y deformetrica
#    echo "conda activate deformetrica" >> ~/.bashrc
    
#    # Download requires libraries for EoD:
#    cd /opt/sw/
#    svn export https://github.com/willgpaik/MorphoGraphX_aci.git/trunk/eod_graphics_libraries
#    mv eod_graphics_libraries eod

    cd /opt/sw/
    rm Anaconda3-2018.12-Linux-x86_64.sh
    
    
