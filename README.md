# Lis patch for K computer  
This patchfile adds two Targets(K_shared, K_mpi_shared) in configure.  
## How to compile and install with MPI  
1.  Login to login node.  
2.  Get lis-2.0.6.K.patch and lis-2.0.6.zip.  
3.  Apply patchfile.  
4.  Use compute node. '`pjsub --interact`'  
5.  Run `./configure` with each options.  
6.  Run `make`.  
7.  Run '`make check`'.
8.  Run '`make install`'.
```  
wget https://raw.githubusercontent.com/RIKEN-AICS/Lis/master/lis-2.0.6.K.patch
wget http://www.ssisc.org/lis/dl/lis-2.0.6.zip
unzip lis-2.0.6.zip
cd lis-2.0.6
patch -p1 < ../lis-2.0.6.K.patch
pjsub --interact -L node=1 -L elapse=1:0:0
source /work/system/Env_base
./configure TARGET="K_mpi_shared" \
                  --enable-fortran \
                  --enable-f90 \
                  --enable-omp \
                  --enable-saamg \
                  --enable-shared \
                  --enable-mpi \
                  --prefix=/install/dir \
                  --build=sparc64-unknown-linux-gnu
make -j 4 all
make check
make install
```  

## How to compile and install without MPI  
If MPI is unnecessary, remove '--enable-mpi' and use TARGET="K_shared".  
1.  Login to login node.  
2.  Get lis-2.0.6.K.patch and lis-2.0.6.zip.  
3.  Apply patchfile.  
4.  Use compute node. '`pjsub --interact`'  
5.  Run `./configure` with each options.  
6.  Run `make`.  
7.  Run '`make check`'.
8.  Run '`make install`'.
```  
wget https://raw.githubusercontent.com/RIKEN-AICS/Lis/master/lis-2.0.6.K.patch
wget http://www.ssisc.org/lis/dl/lis-2.0.6.zip
unzip lis-2.0.6.zip
cd lis-2.0.6
patch -p1 < ../lis-2.0.6.K.patch
pjsub --interact -L node=1 -L elapse=1:0:0
source /work/system/Env_base
./configure TARGET="K_shared" \
                  --enable-fortran \
                  --enable-f90 \
                  --enable-omp \
                  --enable-saamg \
                  --enable-shared \
                  --prefix=/install/dir \
                  --build=sparc64-unknown-linux-gnu
make -j 4 all
make check
make install
```  

