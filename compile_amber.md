## Instructions to compile AMBER14 on Hyak

1) Unpack Amber14.tar.bz2 and AmberTools14.tar.bz2

```bash
tar xvfj AmberTools14.tar.bz2
tar xvfj Amber14.tar.bz2
```

2) Set environment path
```bash
export AMBERHOME=/path_to_amber14/Amber14
```
3) Configure Amber14 and patch plumed

```bash
module load icc_15.0.3-impi_5.0.3
plumed patch -p (choose amber14 option)
cd $AMBERHOME
./configure intel
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
