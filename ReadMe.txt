Goal: Given a set of images captured from multiple views, this code will compute the scene’s 3D reconstructions.

The serial implementation of structure-from-motion (sfm) is borrowed from the opencv-contrib.

Installation

	SfM Dependencies Installation

		sudo apt-get install libeigen3-dev libgflags-dev libgoogle-glog-dev
		# CMake
		sudo apt-get install cmake
		# google-glog + gflags
		sudo apt-get install libgoogle-glog-dev

		# BLAS & LAPACK
		sudo apt-get install libatlas-base-dev
		# Eigen3
		sudo apt-get install libeigen3-dev
		# SuiteSparse and CXSparse (optional)
		# - If you want to build Ceres as a *static* library (the default)
		#   you can use the SuiteSparse package in the main Ubuntu package
		#   repository:
		sudo apt-get install libsuitesparse-dev
		# - However, if you want to build Ceres as a *shared* library, you must
		#   add the following PPA:
		sudo add-apt-repository ppa:bzindovic/suitesparse-bugfix-1319687
		sudo apt-get update
		sudo apt-get install libsuitesparse-dev
		
	Install Ceres
		git clone https://ceres-solver.googlesource.com/ceres-solver
		cd ceres-solver
		mkdir build && cd build
		cmake ..
		make -jX #where X jobs will run in parallel
		make test
		sudo make install
		parallel_sfm Installation

		cd ~/<my_directory>
		git clone https://github.com/KSheth96/parallel_sfm.git
		cd <path-of-the-downloaded-folder>/build
		cmake ..
		make -j8 #where 8 jobs will run in parallel

		
	OpenCV Installation

		sudo apt-get install build-essential
		sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
		sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev

		cd ~/<my_working _directory>
		git clone https://github.com/opencv/opencv.git
		git clone https://github.com/opencv/opencv_contrib.git
		
		Now, delete the sfm folder from opencv_contrib folder and then install opencv with opencv-contrib

		cmake [<some optional parameters>] <path to the OpenCV source directory>
		For example:

		cd ~/opencv
		mkdir release
		cd release
		cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=<path to oencv_contrib/modules> <path to opencv source code>
		make -j8 ,where 8 jobs will run in parallel
		sudo make install
		
#Execute parallel implementation
		cd <path-of-the-downloaded-folder>/sfm_parallel_CUDA/build
		cmake ..
		make -j8 #where 8 jobs will run in parallel
		./foo  <path-of-the-downloaded-folder>/sfm_parallel_CUDA/samples/data/images/dataset_files.txt 350 240 360
		
#Execute serial implementation
		cd <path-of-the-downloaded-folder>/sfm_serial/build
		cmake ..
		make -j8 #where 8 jobs will run in parallel
		./foo  <path-of-the-downloaded-folder>/sfm_serial/samples/data/images/dataset_files.txt 350 240 360





