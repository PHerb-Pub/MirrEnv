# Benchmarking Visual SLAM Methods in Mirror Environments
## MirrEnv Dataset Description

The Mirror Enivronments (MirrEnv) dataset is made up of RGBD image sequences with groundtruth camera localisation data.
Three sizes of mirrors were used (small, medium, large), where some sequences had the mirror visible, covered by green card, or had the mirror removed from the scene entirely (7 variations in total).
Each of these 7 mirror presence varieties was combined with 7 pre-calculated robot arm trajectories, giving a total of 49 sequences in total.
Binary masks for the mirror region are provided for every 10th frame of sequences containing mirrors.
Mirror presence in these sequences has been analysed and disucssed further in the paper (see [publication](#publication)).

![picture alt](site_assets/types%20of%20sequences.png "Types of image sequences with different mirror presence.")

An Intel RealSense D435i RGBD camera was calibrated and attached to the end-effector (EEF) of a KUKA IIWA 14R820 manipulator arm.
The transformation between the camera position and the EEF position was determined through Hand-Eye calibration. This calibration data is also available as a part of the dataset.


## MirrEnv Dataset Structure

The dataset structure follows the general structure of the TUM RGBD dataset.

Each sequence is labelled as `Trj_X1_X2_X3_X4`, where `X1` is the numerical index across all 49 sequences; `X2` is the trajectory name; `X3` indicates the mirror size; `X4` indicates if the mirror is visible (W) or covered (C). If there is no mirror, then `X3` and `X4` are replaced with `No_Mirror`.

The RGB frames and depth frames have slightly differing timestamps. During experiments they were associated together using the `associate.py` python script available from the [TUM RGBD dataset tools](https://cvg.cit.tum.de/data/datasets/rgbd-dataset/tools)

`Trj_X1_X2_X3_X4`  
|----`calib`  
|&emsp;|----`images`  
|&emsp;|&emsp;|----`depth`  
|&emsp;|&emsp;|&emsp;|----`#timestamp#.png` (16-bit greyscale image, 1280x720)  
|&emsp;|&emsp;|&emsp;|----`......`  
|&emsp;|&emsp;|----`rgb`  
|&emsp;|&emsp;|&emsp;|----`#timestamp#.png` (24-bit rgb image, 1280x720)  
|&emsp;|&emsp;|&emsp;|----`......`  
|&emsp;|&emsp;|----`rs_intrinsics.xml`  
|&emsp;|----`poses`  
|&emsp;|&emsp;|----`#timestamp#.txt` (4x4 rigid body transformation relative tor robot base)  
|&emsp;|&emsp;|----`......`  
|&emsp;|----`calib_X.txt`  
|&emsp;|----`DepthFactor.txt`  
|&emsp;   
|----`trj`  
|&emsp;|----`images`  
|&emsp;|&emsp;|----`depth`  
|&emsp;|&emsp;|&emsp;|----`#timestamp#.png` (16-bit greyscale image, 640x480)  
|&emsp;|&emsp;|&emsp;|----`......`  
|&emsp;|&emsp;|----`rgb`  
|&emsp;|&emsp;|&emsp;|----`#timestamp#.png` (24-bit rgb image, 640x480)  
|&emsp;|&emsp;|&emsp;|----`......`  
|&emsp;|&emsp;|----`masks`  (only available in sequences containing mirrors, ie. X4 = W)  
|&emsp;|&emsp;|&emsp;|----`#timestamp#.png` (8-bit binary image, 640x480)  
|&emsp;|&emsp;|&emsp;|----`......`  
|&emsp;|&emsp;|----`c_names.txt` (filenames of rgb frames - timestamp in seconds since Unix epoch)  
|&emsp;|&emsp;|----`d_names.txt` (filesnames of depth frames - timestamp in seconds since Unix epoch)  
|&emsp;|&emsp;|----`depth.mp4` (original video of depth frames)  
|&emsp;|&emsp;|----`rgb.avi` (original video of rgb frames)   
|&emsp;|----`poses`  
|&emsp;|&emsp;|----`Qposes.txt` (Camera pose relative to the base of the robot base, XYZ position in metres and unit quaternion pose)
  
  


## Publication

Link to Paper

Link to Dataset
