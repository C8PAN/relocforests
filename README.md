# relocforests
Scene Coordinate Regression Forests for Camera Relocalization in RGB-D Images.

## Usage
### Dependencies
* Cmake
* Opencv
* Eigen

### Building
Set an environment variable for Eigen: `EIGEN_DIR=/path/to/eigen/include`.

Build like any other cmake project.

```
cd relocforests
mkdir build
cd build

# UNIX Makefile
cmake ..

# Mac OSX
cmake -G "Xcode" ..

# Microsoft Windows
cmake -G "Visual Studio 14" ..
cmake -G "Visual Studio 14 Win64" ..
...
```

# Usage of Example Application

The example application takes input frames and poses from the [TUM RGBD datasets](http://vision.in.tum.de/data/datasets/rgbd-dataset),
and requires that your create an [association file](http://vision.in.tum.de/data/datasets/rgbd-dataset/tools) to associate the RGB, Depth, and pose information.
Instructions for this process can be found [here](https://github.com/tum-vision/fastfusion).

```
# Training
# depeding on your setup this could take upwards of 10 minutes to train
$ ./relocforests_example ~/data/rgbd_dataset_freiburg1_desk/ train desk1.rf 

# Testing
# test the forest we created with a different dataset
$ ./relocforests_example ~/data/rgbd_dataset_freiburg1_desk2/ test desk1.rf 
```


## Citations
```
@Inprceedings {export:184826,
author       = {Jamie Shotton and Ben Glocker and Christopher Zach and Shahram Izadi and Antonio
                Criminisi and Andrew Fitzgibbon},
booktitle    = {Proc. Computer Vision and Pattern Recognition (CVPR)},
month        = {June},
publisher    = {IEEE},
title        = {Scene Coordinate Regression Forests for Camera Relocalization in RGB-D Images},
url          = {http://research.microsoft.com/apps/pubs/default.aspx?id=184826},
year         = {2013},
} 
```

```
@software{brooks16,
author        = {Conner Brooks},
title         = {C++ Implementation of SCORE Forests for Camera Relocalization},
howpublished  = {\url{https://github.com/isue/relocforests}},
year          = {2016}
}
```

This implementation uses a modified version of [MeanShift++](https://github.com/mattnedrich/MeanShift_cpp), as well as an [implementation of the Kabsch algorithm](https://github.com/oleg-alexandrov/projects/blob/master/eigen/Kabsch.cpp).

