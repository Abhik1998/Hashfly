AR-Drone-Hashfly
=======================

Fire Detection with AR-Drone 2.0 in Python

by Abhik Chakraborty

The main file is firedetection.py.  The rest are testing files.

The goal of this program is to use a AR-Drone 2.0 to find and follow the progress of a forest fire. It uses two fire detection algorithms explained below.  The drone relies on Venthur's Python-ARDrone library and some subsequent forks for the AR-Drone 2.0.

Video decoding is done with the Python library included in OpenCV 2.4.5 and with the latest FFMPEG installed.  SimpleCV is also used for blob detection.

If you are just getting started with AR-Drone 2.0 video decoding, the first step is to install the latest FFMPEG and OpenCV.  The AR-Drone 2.0 sends Parrot's proprietary h264 video feed over tcp on tcp://192.168.1.1:5555.  FFMPEG can simply decode this feed and play it for you. To do this, simply type 'ffplay tcp://192.168.1.1:5555' into the terminal.  OpenCV uses FFMPEG to perform video tasks and therefore, it is simple to import the video directly into OpenCV.  SimpleCV is a frontend tool for OpenCV that makes it easier to perform higher level computer vision tasks.

The RGB color filter is based on a method proposed in "Fire Detection Using Statistical Color Model in Video Sequences" by Turgay Celik, Hasan Demeril, Huseyin Ozkaramanli, Mustafa Uyguroglu.  This method uses the RGB color space and does three comparisons.
The method returns true at any pixel that satisfies:

red > green > blue
red > red threshold (depends on amount of light in image)

This is a filter based on a method proposed in "Fast and Efficient Method for Fire Detection
	Using Image Processing" by Turgay Celik

The LAB filter uses the CIE L*a*b* color space and performs 4 bitwise filters.  The method returns true at any pixel that satisfies:

L* > Lm* (mean of L* values)
a* > am* (mean of a* values)
b* > bm* (mean of b* values)
b* > a*

This program is a work in progress and will soon have autonomous mode for finding fires.

This software is being written for a Fire-drone.ai Hackathon.
