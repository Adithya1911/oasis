# Linux Application for Digital Heritage Project

- As this project is an demonstration of the Integrating SLAM on the Wearable Edge devices and using it for navigation in door and outdoor environments.

- The Linux Application requires following thing for running other than the dependencies of the Photo-SLAM and ORB-SLAM


- Since we are using the GTK for creating the python application

## 1. Install Dependencies

```bash

sudo apt update
sudo apt install -y python3-gi python3-gi-cairo gir1.2-gtk-3.0 gir1.2-glib-2.0 gir1.2-gdkpixbuf-2.0
pip3 install open3d numpy 
sudo apt install -y wmctrl

```


## 2. PHOTO-SLAM

For installing the PHOTO-SLAM we need the following dependencies are as follows 
 
```bash
# For normal installation 

sudo apt install libeigen3-dev libboost-all-dev libjsoncpp-dev libopengl-dev mesa-utils libglfw3-dev libglm-dev

```


For Conda installation
Install the CMAKE of the version 3.26.4

```bash
conda install -c conda-forge cmake=3.26.4
conda install -c conda-forge  eigen boost  jsoncpp  glfw  glm  libglu  libglvnd  libx11
```


Photo-slam Requires the Opencv which is supported by the cuda for installing that use the following references to install them

-**Video Reference** [Open cv installation with cuda support](https://www.youtube.com/watch?v=art0-99fFa8)
-**Github Reference** [Nano Build Opencv](https://github.com/mdegans/nano_build_opencv)


## 3. Path Modifications

### Linux Application Path Configuration

By default, the application saves images of current frames and point cloud data in the following directory:`ORB_SLAM3/Linux/frames/`

**Change the following paths :**
- `/home/digital_heritage/Digital-Heritage/ORB_SLAM3/Linux/frames/pointcloud.jpg` to the path where you are saving the pointcloud.jpg
- `/home/digital_heritage/Digital-Heritage/ORB_SLAM3/Linux/frames/frame.jpg` to the path where you are saving the frame.jpg
- `/home/digital_heritage/Digital-Heritage/ORB_SLAM3/Maps/` to the foldere path where the Point cloud is being saved

To modify these paths, update the following files:


**Files to Modify:**
- `debugger.py`
- `user.py`

### ORB_SLAM3 Path



      

