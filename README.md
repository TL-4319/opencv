# OpenCV: Open Source Computer Vision Library with E-Con sys patch

This is a fork of OpenCV 4.7.0 with the patches from E-Con System to provide API to their cameras

This was tested on Jetson Orin with Jetpack 5.1.2

## Install dependencies

You need to remove any pre-installed OpenCV on the system
```
sudo apt remove libopencv-dev
```

Then install the neccessary dependencies per E-Con System documentation

```
sudo apt install build-essential make cmake cmake-qt-gui g++
sudo apt install libv4l-dev
sudo apt install libglew-dev
sudo apt install libgtk2.0-dev
sudo apt install libudev-dev
sudo apt install libavformat-dev libavutil-dev libswscale-dev libavcodec-dev libavcodec-ffmpeg-extra56 libavformat-ffmpeg56 libavutil-ffmpeg54 libswscale-ffmpeg3 libdc1394-*
sudo apt install libeigen3-dev
sudo apt install pkg-config
sudo apt install gfortran
sudo apt install openexr
sudo apt install libatlas-base-dev
sudo apt install libtbb2
sudo apt install libopenexr-dev
```

## Build and install
From within this OpenCV directory

```
mkdir release
cd release
cmake ..  -D BUILD_TIFF=ON -D WITH_CUDA=OFF -D WITH_OPENGL=OFF -D WITH_OPENCL=OFF -D WITH_IPP=OFF -D WITH_TBB=OFF -D BUILD_TBB=OFF -D WITH_EIGEN=OFF -D WITH_V4L=ON -D WITH_VTK=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D WITH_GSTREAMER=OFF -D CMAKE_BUILD_TYPE=RELEASE -D BUILD_opencv_world=ON -D OPENCV_GENERATE_PKGCONFIG=YES -D WITH_GENERATE_PKGCONFIG=YES -D CMAKE_INSTALL_PREFIX=/usr/local

sudo make -j4
sudo make install
```

Additionally, the path to this OpenCV need to be configured.

```
sudo cp opencv.conf /etc/ld.so.conf.d/
sudo ldconfig -v
```



