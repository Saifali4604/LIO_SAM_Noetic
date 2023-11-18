# LIO-SAM
<p align='center'>
    <img src="./config/doc/demo.gif" alt="drawing" width="800"/>
</p>

## Dependency
  ```
  sudo apt-get install -y ros-noetic-navigation
  sudo apt-get install -y ros-noetic-robot-localization
  sudo apt-get install -y ros-noetic-robot-state-publisher
  sudo add-apt-repository ppa:borglab/gtsam-release-4.2
  sudo apt update
  sudo apt install libgtsam-dev libgtsam-unstable-dev
  ```

## Install

Use the following commands to download and compile the package.

```
cd ~/catkin_ws/src
git clone https://github.com/TixiaoShan/LIO-SAM.git
cd ..
catkin_make
```
## Run the package

1. Run the launch file:
```
roslaunch lio_sam run.launch
```

2. Play existing bag files: download the datasets from below drive link
```
rosbag play your-bag.bag -r 3
```
## Sample datasets

  * Download some sample datasets to test the functionality of the package. The datasets below are configured to run using the default settings:
    - **Walking dataset:** [[Google Drive](https://drive.google.com/drive/folders/1gJHwfdHCRdjP7vuT556pv8atqrCJPbUq?usp=sharing)]
    - **Park dataset:** [[Google Drive](https://drive.google.com/drive/folders/1gJHwfdHCRdjP7vuT556pv8atqrCJPbUq?usp=sharing)]
    - **Garden dataset:** [[Google Drive](https://drive.google.com/drive/folders/1gJHwfdHCRdjP7vuT556pv8atqrCJPbUq?usp=sharing)]

  * The datasets below need the parameters to be configured. In these datasets, the point cloud topic is "points_raw." The IMU topic is "imu_correct," which gives the IMU data in ROS REP105 standard. Because no IMU transformation is needed for this dataset, the following configurations need to be changed to run this dataset successfully:
    - The "imuTopic" parameter in "config/params.yaml" needs to be set to "imu_correct".
    - The "extrinsicRot" and "extrinsicRPY" in "config/params.yaml" needs to be set as identity matrices.
      - **Rotation dataset:** [[Google Drive](https://drive.google.com/drive/folders/1gJHwfdHCRdjP7vuT556pv8atqrCJPbUq?usp=sharing)]
      - **Campus dataset (large):** [[Google Drive](https://drive.google.com/drive/folders/1gJHwfdHCRdjP7vuT556pv8atqrCJPbUq?usp=sharing)]
      - **Campus dataset (small):** [[Google Drive](https://drive.google.com/drive/folders/1gJHwfdHCRdjP7vuT556pv8atqrCJPbUq?usp=sharing)]

  * Ouster (OS1-128) dataset. No extrinsics need to be changed for this dataset if you are using the default settings. Please follow the Ouster notes below to configure the package to run with Ouster data. A video of the dataset can be found on [YouTube](https://youtu.be/O7fKgZQzkEo):
    - **Rooftop dataset:** [[Google Drive](https://drive.google.com/drive/folders/1gJHwfdHCRdjP7vuT556pv8atqrCJPbUq?usp=sharing)]

  * Livox Horizon dataset. Please refer to the following notes section for paramater changes.
    - **Livox Horizon:** [[Google Drive](https://drive.google.com/drive/folders/1gJHwfdHCRdjP7vuT556pv8atqrCJPbUq?usp=sharing)]

  * KITTI dataset. The extrinsics can be found in the Notes KITTI section below. To generate more bags using other KITTI raw data, you can use the python script provided in "config/doc/kitti2bag".
    - **2011_09_30_drive_0028:** [[Google Drive](https://drive.google.com/drive/folders/1gJHwfdHCRdjP7vuT556pv8atqrCJPbUq?usp=sharing)]
