# OpenCV, Tensorflow, Conda and Scipy (Python3) for ARM based Mac (M1)

Installation guide for native opencv, tensorflow and scipy with all relevant tools.

# CMake
Install CMake by building it from source:
```shell
git clone https://github.com/Kitware/CMake.git
./bootstrap && make && sudo make install
```

# Conda

Install miniconda for ARM: [Miniforge3-MacOSX-arm64.sh](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-arm64.sh)

Create and activate a Python 3.8 eviroment in order to be able to use tensorflow later:
```shell
conda create --name python38 python=3.8
conda activate python38
```

# Scipy

Install your packages from conda-forge:
e.g. (opencv and tensorflow are not availble)
```shell
conda install -c conda-forge scipy
conda install -c conda-forge pandas
conda install -c conda-forge numpy
conda install -c conda-forge matplotlib
conda install -c conda-forge jupyter-lab
conda install -c conda-forge skikit-learn
```

# OpenCV

Clone the opencv source code.
```shell
cd ~
git clone https://github.com/opencv/opencv.git
git clone https://github.com/opencv/opencv_contrib.git
```

create a seperate build folder.
```
mkdir build_opencv
cd build_opencv
```

Copy all the .h files from the /Users/USER/miniforge3/envs/python38/include directory into the /Users/USER/miniforge3/envs/python38/include/python3.8 directory (copying the contents of both into another directory and setting that as the path would also work) so that all the .h files are in the same folder visible to the compiler. https://stackoverflow.com/questions/36814673/installing-opencv-in-anaconda3-python-h-no-such-file-or-directory

Remeber to change the User Name accordingly.

```shell
cmake -DCMAKE_BUILD_TYPE=Release \
-DBUILD_opencv_python2=OFF \
-DBUILD_opencv_python3=ON \
-DPYTHON3_EXECUTABLE=`which python3` \
-DPYTHON3_INCLUDE_DIR=~/miniforge3/envs/python38/include/python3.8 \
-DPYTHON3_PACKAGES_PATH=~/miniforge3/envs/python38/lib/python3.8 \
-DPYTHON3_NUMPY_INCLUDE_DIR=~/miniforge3/envs/python38/lib/python3.8/site-packages/numpy/core \
-DCMAKE_INSTALL_PREFIX=/usr/local \
-DOPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
-DOPENCV_ENABLE_NONFREE=ON \
../opencv
```

```
make -j7
sudo make install
```

OpenCV and all installed packages should now be available in Python!

# Tensorflow
Use the custom TF2 version from Apple with this [guide](https://github.com/mwidjaja1/DSOnMacARM): and take care to correctly replace the install file with this [Pull Request](https://github.com/apple/tensorflow_macos/pull/63).
