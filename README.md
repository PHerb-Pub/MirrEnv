# Benchmarking Visual SLAM Methods in Mirror Environments
## MirrEnv Dataset Description

The Mirror Enivronments (MirrEnv) dataset is made up of RGBD image sequences with groundtruth camera localisation data.
Three sizes of mirrors were used (13 x 18cm, 21 x 30cm and a rounded mirror within 40 x 50cm), where some sequence had the mirror visible, covered or with the mirror removed from the scene entirely (7 variations in total).
Each of these 7 mirror presence varieties was combined with 7 precalculated robot arm trajectories, giving a total of 49 sequences in total.
Binary masks for the mirror region are provided for every 10th frame of sequences containing mirrors.
Mirror presence in these sequences has been analysed and disucssed further in the paper.

![picture alt](http://via.placeholder.com/200x150 "Title is optional")

An Intel RealSense D435i RGBD camera was calibrated and attached to the end-effector (EEF) of a KUKA IIWA 14R820 manipulator arm.
The transformation between the camera position and the EEF position was determined through Hand-Eye calibration. This calibration data is also available as a part of the dataset.
More details on the calibration process ad experimental setup are discussed in the paper.



## MirrEnv Dataset Structure

Each sequence is labelled as `Trj_X1_X2_X3_X4`, where `X1` is the numerical index across all 49 sequences; `X2` is the trajectory name; `X3` indicates the mirror size; `X4` indicates if the mirror is visible (W) or covered (C). If there is no mirror, then `X3` and `X4` are replaced with `No_Mirror`.

`Trj_X1_X2_X3_X4`  
|----`calib`  
|&emsp;|----`images`  
|&emsp;|&emsp;|----`depth`  
|&emsp;|&emsp;|&emsp;|----`timestamp.png` (16-bit greyscale image, 1280x720)  
|&emsp;|&emsp;|&emsp;|----`......`  
|&emsp;|&emsp;|----`rgb`  
|&emsp;|&emsp;|&emsp;|----`timestamp.png` (24-bit rgb image, 1280x720)  
|&emsp;|&emsp;|&emsp;|----`......`  
|&emsp;|&emsp;|----`rs_intrinsics.xml`  
|&emsp;|----`poses`  
|&emsp;|&emsp;|----`timestamp.txt` (4x4 rigid body transformation)  
|&emsp;|&emsp;|----`......`  
|&emsp;|----`calib_X.txt`  
|&emsp;|----`DepthFactor.txt`  
|&emsp;|----`CalibPoseDiagram.pdf`  
|&emsp;|----`XAndreff.pdf` (error in the estimation of transformation X by particular method)  
|&emsp;|----`XDan.pdf`  
|&emsp;|----`XMeas.pdf` (TODO: check definition)  
|&emsp;|----`XPark.pdf`  
|&emsp;|----`XTsai.pdf`  
|&emsp;   
|----`trj`  
|&emsp;|----`images`  
|&emsp;|&emsp;|----`depth`  
|&emsp;|&emsp;|&emsp;|----`timestamp.png` (16-bit greyscale image, 640x480)  
|&emsp;|&emsp;|&emsp;|----`......`  
|&emsp;|&emsp;|----`rgb`  
|&emsp;|&emsp;|&emsp;|----`timestamp.png` (24-bit rgb image, 640x480)  
|&emsp;|&emsp;|&emsp;|----`......`  
|&emsp;|&emsp;|----`masks`  (only available in sequences containing mirrors, ie. X4 = W)  
|&emsp;|&emsp;|&emsp;|----`timestamp.png` (8-bit binary image, 640x480)  
|&emsp;|&emsp;|&emsp;|----`......`  
|&emsp;|&emsp;|----`c_names.txt` (filenames of rgb frames)  
|&emsp;|&emsp;|----`d_names.txt` (filesnames of depth frames)  
|&emsp;|&emsp;|----`depth.mp4` (video of depth frames)  
|&emsp;|&emsp;|----`rgb.avi` (video of rgb frames)  
|&emsp;|&emsp;|----`t_cap_start.txt` (timestamp for beginning of recording of image sequence)  
|&emsp;|----`poses`  
|&emsp;|&emsp;|----`poses.txt` (EEF position relative to robot arm base, XYZEuler format) TODO: check definition  
|&emsp;|&emsp;|----`Qposes.txt` (Camera position relative to robot arm base, XYZEuler format) TODO: check definition  
|&emsp;|----`capture_exit.txt` (empty file used for triggering recording thread to terminate)  
|&emsp;|----`TrjPlanVis.avi` (MATLAB visualisation of robot motion control)  
  
  


## Publication

Link to Paper

Link to Dataset
