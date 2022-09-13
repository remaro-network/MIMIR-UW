# Welcome to MIMIR-UW!:octopus:

Here you will find all the relevant information regarding the dataset introduced in [our paper(TODO)]()


      
 ## Dataset link
 You can access MIMIR-UW from [the following link(TODO)]()
 
 ## Dataset structure
Thereafter the data tree is presented. For the sake of brevity, we only show the nested structured under one of the tracks for one of the sequences, that is, under track0 for the SeaFloor sequence. Similarly, we only show the nested structure under one of the cameras. Note that the structure is the same for all cameras and sequences. 
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

## Data recorder

You can use the settings file for AirSim provided in this repo by creating a symlink as follows:

	```
	ln -s ~/MIMIR-UW/airsim_data_generator/settings.json ~/Documents/AirSim/settings.json
	```
