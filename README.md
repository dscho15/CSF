![csf1](https://github.com/jianboqi/CSF/blob/master/CSFDemo/CSF1.png) ![csf2](https://github.com/jianboqi/CSF/blob/master/CSFDemo/CSF2.png)
# CSF
Airborne LiDAR filtering method based on Cloth Simulation.
This is the code for the article:

W. Zhang, J. Qi*, P. Wan, H. Wang, D. Xie, X. Wang, and G. Yan, “An Easy-to-Use Airborne LiDAR Data Filtering Method Based on Cloth Simulation,” Remote Sens., vol. 8, no. 6, p. 501, 2016.
(http://www.mdpi.com/2072-4292/8/6/501/htm)


**Reading data from txt file:**

If the lidar data is stored in a txt file, it can be imported directly. The expected format is one point per line with `X Y Z` values separated by whitespace.

### How to use CSF in R

Thanks to the nice work of @Jean-Romain, through the collaboration, the CSF has been made as a R package, the details can be found in the [RCSF repository](https://github.com/Jean-Romain/RCSF). This package can be used easily with the [lidR package](https://github.com/Jean-Romain/lidR):

```r
library(lidR)
las  <- readLAS("file.las")
las  <- lasground(las, csf())
```

### How to use CSF in C++
Now, CSF is built by CMake, it produces a static library, which can be used by other c++ programs.
#### linux
To build the library, run:
```bash
mkdir build #or other name
cd build
cmake ..
make
sudo make install
```
or if you want to build the library and the demo executable `csfdemo`

```bash
mkdir build #or other name
cd build
cmake -DBUILD_DEMO=ON ..
make
sudo make install

```

If you want to run the demo executable, update `CSFDemo/params.cfg` so `terr_pointClouds_filepath` points at your input txt file.

#### Windows
You can use CMake GUI to generate visual studio solution file.

### Binary Version
For binary release version, it can be downloaded at: http://ramm.bnu.edu.cn/projects/CSF/download/

Note: This code has been changed a lot since the publication of the corresponding paper. A lot of optimizations have been made. We are still working on it, and wish it could be better.

### Cloudcompare Pulgin
At last, if you are interested in Cloudcompare, there is a good news. our method has been implemented as a Cloudcompare plugin, you can refer to : https://github.com/cloudcompare/trunk

### Related project
A tool named `CSFTools` has been recently released, it is based on CSF, and provides dem/chm generation, normalization. Please refer to: https://github.com/jianboqi/CSFTools

### License
CSF is maintained and developed by Jianbo QI. It is now released under Apache 2.0.
