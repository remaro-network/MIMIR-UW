# Welcome to MIMIR-UW!:octopus:

Here you will find all the relevant information regarding the dataset introduced in [our paper(TODO)]()


| Simulated underwater robot    |  3 cameras x 3 sensors | 4 environments |
:-------------------------:|:-------------------------:|:-------------------------:
![](https://github.com/remaro-network/MIMIR-UW/blob/main/media/MMGA.png?raw=true)  |  ![](https://github.com/remaro-network/MIMIR-UW/blob/main/media/MIMIR-cameras.gif?raw=true) |  ![](https://github.com/remaro-network/MIMIR-UW/blob/main/media/MIMIR-4envs.gif?raw=true)

## Acknowledgements

<a href="https://remaro.eu/">
    <img height="60" alt="REMARO Logo" src="https://remaro.eu/wp-content/uploads/2020/09/remaro1-right-1024.png">
</a>

This work is part of the Reliable AI for Marine Robotics (REMARO) Project. For more info, please visit: <a href="https://remaro.eu/">https://remaro.eu/

<br>

<a href="https://research-and-innovation.ec.europa.eu/funding/funding-opportunities/funding-programmes-and-open-calls/horizon-2020_en">
    <img align="left" height="60" alt="EU Flag" src="https://remaro.eu/wp-content/uploads/2020/09/flag_yellow_low.jpg">
</a>

This project has received funding from the European Union's Horizon 2020 research and innovation programme under the Marie Skłodowska-Curie grant agreement No. 956200.

 ## Dataset link
 You can download MIMIR-UW from [the following link(TODO)]()
 
 
 ## The four underwater environments in MIMIR

|    |   |
:-------------------------:|:-------------------------:
![](https://github.com/remaro-network/MIMIR-UW/blob/main/media/MIMIR-oceanfloor.gif?raw=true)  |  ![](https://github.com/remaro-network/MIMIR-UW/blob/main/media/MIMIR-seafloor.gif?raw=true) |  
![](https://github.com/remaro-network/MIMIR-UW/blob/main/media/MIMIR-seaflooralgae.gif?raw=true)  |  ![](https://github.com/remaro-network/MIMIR-UW/blob/main/media/MIMIR-sandpipe.gif?raw=true) |  


 ## Dataset structure
The data tree is shown below. For the sake of brevity, we only show the nested structured under one of the tracks for one of the sequences, that is, under track0 for the SeaFloor sequence. Similarly, we only show the nested structure under one of the cameras. Note that the structure is the same for all cameras and sequences. 
```
MIMIR-UW
├── SeaFloor
│   ├── segmentation.json
│   ├── settings.json
│   └── auv0
│   │   ├── track0
│   │   │   ├── imu0
│   │   │   │   └── data.csv
│   │   │   ├── pose_groundtruth
│   │   │   │   └── data.csv
│   │   │   ├── rgb
│   │   │   │   ├── cam0
│   │   │   │   │   ├── data
│   │   │   │   │   │   ├── <filename0>.png
│   │   │   │   │   │   ├── ...
│   │   │   │   │   │   └── <filenameN>.png
│   │   │   │   │   ├── data.csv
│   │   │   │   │   └── sensor.yaml
│   │   │   │   ├── cam1
│   │   │   │   └── cam2
│   │   │   ├── segmentation
│   │   │   │   ├── cam0
│   │   │   │   │   ├── data
│   │   │   │   │   │   ├── <filename0>.png
│   │   │   │   │   │   ├── ...
│   │   │   │   │   │   └── <filenameN>.png
│   │   │   │   │   ├── data.csv
│   │   │   │   │   └── sensor.yaml
│   │   │   │   ├── cam1
│   │   │   │   └── cam2
│   │   │   └── depth
│   │   │   │   ├── cam0
│   │   │   │   │   ├── data
│   │   │   │   │   │   ├── <filename0>.exr
│   │   │   │   │   │   ├── ...
│   │   │   │   │   │   ├── <filenameN>.exr
│   │   │   │   │   ├── data.csv
│   │   │   │   │   └── sensor.yaml
│   │   │   │   ├── cam1
│   │   │   │   └── cam2
│   │   ├── track1
│   │   └── track2
├── SeaFloor_Algae
│   ├── track0
│   ├── track1
│   └── track2
├── OceanFloor
│   ├── track0_light
│   ├── track0_dark
│   └── track1_light
├── SandPipe
│   └── track0_light
│   └── track0_dark
└── README.md
```

## Data format
We follow a dataset format similar to the [ASL format proposed by EuRoC](https://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets). We provide calibration files for all available sensors, with temporally aligned ground truth and measurements.
The calibration files are provided as a sensor.yaml file. For the camera, the data is comprised as follows:

```
{
    "sensor_type": "front_left",
    "comment": "rgb",
    "T_BS": [
        [0.9659258262890682, -0.0, -0.25881904510252074, 0.45],
        [0.0, 1.0, -0.0, -0.06],
        [0.25881904510252074, 0.0, 0.9659258262890682, 0.0],
        [0.0, 0.0, 0.0, 1.0]
    ],
    "rate_hz": 30,
    "resolution": [
        720,
        540
    ],
    "camera_model": "pinhole",
    "intrinsics": [
        [252.07470703125, 0.0, 360.0],
        [0.0, 252.07470703125, 270.0],
        [0.0, 0.0, 1.0]
    ],
    "distortion_model": "radial-tangential",
    "distortion_coefficients": [
        0.0,
        0.0,
        0.0,
        0.0,
        0.0
    ]
}
```
And for the IMU:

```
{
    "sensor_type": "imu0",
    "T_BS": [
        [1.0, 0.0, 0.0, 0.0],
        [0.0, 1.0, 0.0, 0.0],
        [0.0, 0.0, 1.0, 0.0],
        [0.0, 0.0, 0.0, 1.0]
    ],
    "rate_hz": 210,
    "angular_random_walk": 0.3,
    "giro_bias_stability_tau": 500,
    "giro_bias_stability": 4.6,
    "velocity_random_walk": 0.24,
    "accel_bias_stability": 36,
    "accel_bias_stability_tau": 800
}
```

With `T_BS` the transform between body and sensor frame.

## Dataset evaluation
In our paper, we evaluate the performance of ORB-SLAM3 and DSO in MIMIR-UW. If you wish to run the experiments in your own computer, you can find forks for both repositories under [evaluation/SLAM](https://github.com/remaro-network/MIMIR-UW/tree/main/evaluation/SLAM).
These forks provide all the files required by each repository, plus script files to easily run the algorithms on MIMIR-UW.

## Data recorder

You can use the settings file for AirSim provided in this repo by creating a symlink as follows:

	```
	ln -s ~/MIMIR-UW/SeaFloor/settings.json ~/Documents/AirSim/settings.json
	```
