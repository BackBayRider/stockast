# Stockast
## Stock Market Forecasting using Parallel Monte-Carlo Simulations and Machine Learning

### Requirements
(Steps 3 & 4 required only if you're missing the file "gnuplot-iostream.h")
  1. gcc version 6.3.0 or higher
    a. UBUNTU: (Requires root privileges) (eg: on an Ubuntu laptop)  
        sudo add-apt-repository ppa:ubuntu-toolchain-r/test  
        sudo apt update  
        sudo apt install gcc-6  
        sudo apt install g++-6  
        sudo update-alternatives --instal /usr/bin/gcc gcc /usr/bin/gcc-6 60 --slave /usr/bin/g++ /usr/bin/g++-6  
    b. OTHERS: (Without root privileges. Also, add the last 3 instruction lines to the end of \~/.bashrc) (eg: eg: on a remote machine via ssh)  
        wget https://ftp.gnu.org/gnu/gcc/gcc-6.3.0/gcc-6.3.0.tar.gz  
        tar -xvzf gcc-6.3.0.tar.gz  
        cd gcc-6.3.0  
        ./contrib/download_prerequisites  
        cd ..  
        mkdir gcc-build && cd gcc-build  
        ../gcc-6.3.0/configure --disable-multilib -v --prefix=path/to/gcc-6.3.0  
        make  
        make install  
        export PATH=~/gcc-6.3.0/bin/:$PATH  
        export LD_LIBRARY_PATH=path/to/gcc-6.3.0/lib:$LD_LIBRARY_PATH  
        export LD_LIBRARY_PATH=path/to/gcc-6.3.0/lib64:$LD_LIBRARY_PATH  
  2. Boost 1.64.0 or higher  
    a. UBUNTU: (Requires root privilieges)  
        sudo apt-get update  
        sudo apt-get install libboost-all-dev  
    b. OTHERS: (Without root privileges. Add the last instruction line to end of ~/.bashrc) (eg: on a remote machine via ssh)  
        wget https://dl.bintray.com/boostorg/release/1.64.0/source/boost_1_64_0.tar.gz  
        tar -xvzf boost_1_64_0.tar.gz  
        mkdir boost-build  
        cd boost_1_64_0  
        ./bootstrap.sh --prefix=/path/to/boost-build  
        ./b2 install  
        export LD_LIBRARY_PATH=/path/to/boost-build/lib:$LD_LIBRARY_PATH  
  3. Git  
        sudo apt-get update  
        sudo apt-get install git  
  4. gnuplot-iostream  
        git clone https://github.com/dstahlke/gnuplot-iostream.git  
        Then copy "gnuplot-iostream.h" to run dir  

### Compile Instructions
(Local): g++ stockast.cpp -o stockast -lboost_iostreams -lboost_system -lboost_filesystem -fopenmp  
(Remote): g++ stockast.cpp -o stockast -I /path/to/boost-build/include -L /path/to/boost-build/lib -lboost_iostreams -lboost_system -lboost_filesystem -fopenmp  

### Run Instructions (0 for no plot & 1 for plot)
  ./stockast 0  
  ./stockast 1  

### Requirements to launch machine_learning_rnn.py
  Python 2 or 3  
  numpy  
  pandas  
  scikit-learn  
  TensorFlow - 1.0.0  
  Scikit-Learn  

### General info
The file "data.csv" contains the original stock-price returns taken from the market.  
The file "ml_data.csv" contains the machine-learning predicted stock-price values for the 3 hours.  
The file "opt.csv" contains the output (most likely outcome) price-vector from our code.  
The script "profiling.sh" runs the parallel code from 1 to max.no. of threads and displays walltimes for each while suppressing any plots (i.e. ./stockast 0 option
