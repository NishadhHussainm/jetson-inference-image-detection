# Jetson Train

![Jetson Train](jetson_train_logo.png)

## Overview

Jetson Train is a project that demonstrates how to train a custom object detection model on an NVIDIA Jetson device using Jetson Inference. This project provides a step-by-step guide and example code to help you get started with training your own models on Jetson.

## Prerequisites

Before you begin, ensure you have the following:

- NVIDIA Jetson device (Jetson Nano, Jetson Xavier NX, etc.)
- JetPack installed on the Jetson device
- Training dataset for your custom object detection task
- Docker installed on the Jetson device (for running Jetson Inference in a container)

## Installation

1. Clone this repository to your Jetson device:

   
   # Update package lists
sudo apt-get update

# Install dependencies
sudo apt-get install git cmake libpython3-dev python3-numpy

# Clone the jetson-inference repository
git clone --recursive https://github.com/dusty-nv/jetson-inference

# Navigate to the jetson-inference directory
cd jetson-inference/

# Create a 'build' directory and navigate into it
mkdir build
cd build

# Run CMake to configure the build
cmake ../

# Navigate back to the main directory
cd ..

# Download pre-trained models
cd tools
./download-models.sh

# Select models for download (3 5 14 16 18 19 24 25 27 29 31 33 along with preselected models)

# Navigate back to the 'build' directory
cd ..
cd build

# Compile the code
make

# Install the compiled code
sudo make install
sudo ldconfig

# Navigate to the 'aarch64/bin' directory
cd aarch64/bin

# List the contents of the directory
ls
ls images

# Run the detection script on an image
./detectnet.py images/peds_0.jpg output_0.jpg

# List camera devices
v4l2-ctl --list-devices

# Note down the camera device to use in Python code, e.g., /dev/video0 or /dev/video1

# List camera formats
v4l2-ctl --device /dev/video0 --list-formats-ext

# Navigate to the home directory
cd ~

# Open a text editor (e.g., notepad) and create a Python script (e.g., my-detection.py) with the provided code

# Save the Python script

# Run the Python script
python my-detection.py

   
