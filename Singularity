BootStrap: shub
From: willgpaik/centos7_aci

%setup
  
%files

%environment
    PATH="$PATH:/opt/sw/anaconda3/bin/"
    export PATH

%runscript
    source /opt/sw/anaconda3/etc/profile.d/conda.sh
    source activate deformetrica
    exec "$@"

%post
    # Install Anaconda
    mkdir -p /opt/sw/
    cd /opt/sw/
    wget https://repo.anaconda.com/archive/Anaconda3-2018.12-Linux-x86_64.sh
    bash Anaconda3-2018.12-Linux-x86_64.sh -b -p /opt/sw/anaconda3
    source /opt/sw/anaconda3/etc/profile.d/conda.sh
    export PATH=$PATH:/opt/sw/anaconda3/bin/
    
    # Update conda
    conda update -y conda
    conda update -y anaconda

    conda create -y -n deformetrica && source activate deformetrica
    conda install -y -c pytorch -c conda-forge -c anaconda -c aramislab deformetrica
    conda update -y deformetrica
    
    cd /opt/sw/
    rm Anaconda3-2018.12-Linux-x86_64.sh
    
    
