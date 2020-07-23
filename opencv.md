# opencv

1. library

   ```bash
   sudo apt-get install build-essential
   
   sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
   
   sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
   
   sudo apt-get install –assume-yes libopencv-dev libdc1394-22 libdc1394-22-dev libjpeg-dev libpng12-dev libtiff5-dev libjasper-dev libavcodec-dev libavformat-dev libswscale-dev libxine2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libv4l-dev libtbb-dev libqt4-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev x264 v4l-utils unzip
   
   sudo apt-get install ffmpeg libopencv-dev libgtk-3-dev python-numpy python3-numpy libdc1394-22 libdc1394-22-dev libjpeg-dev libpng12-dev libtiff5-dev libjasper-dev libavcodec-dev libavformat-dev libswscale-dev libxine2-dev libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libv4l-dev libtbb-dev qtbase5-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev
   ```

2. cmake

   ```bash
   cmake -D CMAKE_BUILD_TYPE=DEBUG -D WITH_CUDA=ON -D CUDA_GENERATION=Auto -D ENABLE_FAST_MATH=1 -D WITH_CUBLAS=1 -D WITH_CUDNN=0N -D WITH_OPENCL=ON -D INSTALL_PYTHON_EXAMPLES=ON -D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib/modules -D BUILD_EXAMPLES=ON -D WITH_NVCUVID=OFF ..
   ```

# opencv 2

1. library
``` bash
sudo apt-get install build-essential cmake unzip pkg-config git libjpeg-dev libpng-dev libtiff-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev libgtk-3-dev libatlas-base-dev gfortran python3-dev

sudo apt-get install libavresample-dev 
sudo apt-get install libgstreamer-plugins-base1.0-dev 
sudo apt-get install libdc1394-22-dev

```
   
2. cmake
```
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D INSTALL_PYTHON_EXAMPLES=ON -D INSTALL_C_EXAMPLES=OFF -D OPENCV_ENABLE_NONFREE=ON -D WITH_CUDA=ON -D WITH_CUDNN=ON -D OPENCV_DNN_CUDA=ON -D ENABLE_FAST_MATH=1 -D CUDA_FAST_MATH=1 -D CUDA_ARCH_BIN=7.5 -D WITH_CUBLAS=1 -D HAVE_opencv_python3=ON -D BUILD_EXAMPLES=ON -D OPENCV_EXTRA_MODULES_PATH=/home/deke/lib/opencv_contrib-4.2.0/modules/ ..
```
***Note: change the CUDA_ARCH_BIN variable***

3. make
problem: *fatal error: boostdesc_bgm.i: No such file or directory*
solve: down the file by yourself
file link: [xfeature2d_vgg](https://github.com/opencv/opencv_3rdparty/tree/contrib_xfeatures2d_vgg_20160317) and [xfeature2d_boostdesc](https://github.com/opencv/opencv_3rdparty/tree/contrib_xfeatures2d_boostdesc_20161012)
4. sudo make install

