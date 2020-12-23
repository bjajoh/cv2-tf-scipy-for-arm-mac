# cv2-tf-scipy-for-arm-mac
Installation guide for native tensor flow, opencv and scipy with all relevant tools.


```
cmake -DCMAKE_BUILD_TYPE=Release \
-DPYTHON3_EXECUTABLE=`which python3` \
-DPYTHON3_NUMPY_INCLUDE_DIR=/Users/bjarnejohannsen/miniforge3/envs/python38/lib/python3.8/site-packages/numpy/core \
-DPYTHON3_INCLUDE_DIR=/Users/bjarnejohannsen/miniforge3/envs/python38/include \
-DBUILD_opencv_python2=OFF \
-DBUILD_opencv_python3=ON \
-DCMAKE_INSTALL_PREFIX=/usr/local \
../opencv
```
