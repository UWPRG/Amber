## Instructions to compile AMBER14 on MOX

1a) Manually Load Scripts for ICC_17

```bash
. /sw/intel-201703/compilers_and_libraries/linux/bin/compilervars.sh intel64
. /sw/intel-201703/compilers_and_libraries/linux/mpi/bin64/mpivars.sh
 export LM_LICENSE_FILE=28518@mgmt4.hyak.local
```

1b) Unpack Amber14.tar.bz2 and AmberTools14.tar.bz2

```bash
tar xvfj AmberTools14.tar.bz2
tar xvfj Amber14.tar.bz2
```

2) Set environment path
```bash
cd amber14
export AMBERHOME=`pwd`
```
3) Configure Amber14

```bash

cd $AMBERHOME
./configure intel (for serial)
./configure -intelmpi intel (for parallel)
```
4) Setup environment
```bash
source amber.sh
```
store the following line in environment script/include in pbs scripts
```bash
source /path_to_amber14/amber14/amber.sh
```

5) Install
```bash
make install
```
6) Include the following lines in any pbs file.
```bash
export AMBERHOME=/path_to_amber14/amber14
export PATH="${PATH}:${AMBERHOME}/bin"
source /path_to_amber14/amber14/amber.sh
```

7) Test (optional)
```bash
make test
```
