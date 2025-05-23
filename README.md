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
- `/home/digital_heritage/Desktop/Photo-SLAM/scripts/view_rgbd` this is the path where the already saved ply file of the PHOTO-SLAM is being viewed so give the path  **Photo-SLAM/scripts** is being installed  make modifications in the following function `launch_viewer_after_realized()`
- For running the ORB_SLAM3 make the path changes respective to your installation of ORB_SLAM3 in the `run_orbslam` 
- For running the PHOTO_SLAM make the path changes respective to your installation of PHOTO_SLAM in the `run_photoslam`

**Files to Modify:**
- `debugger.py`
- `user.py`




### ORB_SLAM3 Path

Here change the paths of the Folder where you want to save the frames.jpg and pointcloud.jpg, 


**Files to Modify:**

- `Viewer.cc` in `ORB_SLAM3/src` modify the path in the function `Run()`
- `/home/digital_heritage/Digital-Heritage/ORB_SLAM3/Linux/frames/pointcloud.jpg` to the path where you are saving the pointcloud.jpg
- `/home/digital_heritage/Digital-Heritage/ORB_SLAM3/Linux/frames/frame.jpg` to the path where you are saving the frame.jpg
  

For Map saving location make modifications as per your requirements in the following file in `ORB_SLAM3`  there are two maps are being saved `temp.ply and ref_temp.ply` so to make the changes make the canges in the following file.

**Files to Modify:**
- `System.cc` and in the function `void System::SavePointCloud(const string &filename)`
- `/home/digital_heritage/Digital-Heritage/ORB_SLAM3/Maps/` to the folder path where the Point cloud is being saved


After all this changes make build once again for the ORBSLAM3 :
- Setup ORBSLAM3 in Jetson -> [Link to Setup Instructions](ORB_SLAM3/setupInstructions.md)


### PHOTO-SLAM


```bash
cd Photo-SLAM/
chmod +x ./build.sh
./build.sh

```



## 4. Final Execution:

For running the python appilication the following command are required  

``` bash
cd ORB_SLAM3/Linux/App # go to the App directory
python3 app.py
```

- There is toggle button where you can select the `debugger mode` and `user mode`.
- Now based on your mode another interface is being opened
- Select the SLam Process with the help of Menu option in the right top corner. By default `Dense Map` is being selected
- Click on `Start` Button for starting the slam process
- Click on `Stop` Button for Stopping the slam process
- A dialog box will appear if you stop or click back button when the slam process is started for saving or delecting the map that is being created upto now
- Click on `Show Features` Button for viewing the what key frames are being considered in the ORB_SLAM and Photo_SLAM
- Click on `Load MAP` Button for viewing the already saved map
- Click on `Left` and `Right` Buttons for transforming the map that is created by the ORB_SLAM and for the Photo_SLAM you can able to interact with the Point cloud with the help of mouse or dragging in touch screen
- Click on `View Logs` Button for viewing the Logs of the SLAM Process the option is present only in the **Debugger Mode** only
- CLick on `Back` Button for comming back to **Mode selection**




      

