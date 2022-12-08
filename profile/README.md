# ReadMe

## Purpose of project

While studying about autonomous driving, we wanted to track and detect specific objects (car, person, object, etc.) based on actual dataset that measured the surrounding environment through camera and rider sensor

## Paper

[Joint Multi-Object Detection and Tracking with Camera-LiDAR Fusion for Autonomous Driving](https://arxiv.org/abs/2108.04602)

## Paper overview

The system architecture of JMODT:

![img_JMODT](https://github.com/Advanced-Topics-in-Software-Team-4/.github/blob/main/profile/img/img_JMODT.png)

- RPN takes calibrated sensor data from paired frames as input and generates regions of interest (RoI) and multi-modal features of the region proposals.
- The parallel detection and correlation networks use the RoI and proposal features to generate detection results, Re-ID affinities and start-end probabilities.
- The Re-ID affinities are further refined via the motion prediction and match score ranking modules.
- The mixedinteger programming module performs comprehensive data association based on the detection results and computed affinities.
- The association results are further managed to achieve continuous tracks despite object occlusions and reappearances.

## Reasons for selecting this paper

In object recognition and tracking, it is more effective to use two sensors in combination than to use only a camera or lidar. In addition, the JDT method is more suitable than the TBD method for tracking multiple objects based on fusion sensors, so the paper was selected.

## How to run

1. Set virtual environment (default: conda must be installed):

```bash
conda create -n project_name python=3.8
```

2. Run virtual environment:

```bash
conda activate project_name
```

3. Install Pythorch:

```bash
conda install torch==1.9.0
```

4. Install CUDA:

```bash
conda install cudatoolkit==11.1
```

5. Install other required Python packages:

```bash
pip install -r requirements.txt
```

6. Build and install the required CUDA modules via PyTorch and the CUDA toolkit:

```bash
python setup.py develop
```

7. Prepare dataset (you can download in [here](https://www.cvlibs.net/datasets/kitti/eval_tracking.php))    

```
JMODT
├── data
    ├── tracking
        ├──training
        │  ├──calib & velodyne & label_02 & image_02
        ├──testing
           ├──calib & velodyne & image_02
```

8. Generate the detection results:

```bash
python tools/kitti_converter.py --data_root ${DATA_ROOT}
```

9. Modify code
> - Modify the code by referring to the [issue](https://github.com/Kemo-Huang/JMODT/issues)
> - Change ephocs in JMODT/jmodt/config.py

10. Training (you can download pretrained model in [here](https://drive.google.com/file/d/1HtQnGiMuhku1rs0hCn95F0UQ40wzmmE0/view). we use batch-size = 4)    

```bash
python tools/train.py --data_root ${DATA_ROOT} --ckpt ${PRETRAINED_MODEL} --batch_size ${BATCH_SIZE} --output_dir ${OUTPUT}
```

11. Testing

```bash
python tools/eval.py --data_root ${DATA_ROOT} --det_output ${DETECTION_OUTPUT} --ckpt ${CKPT}
```

## Result


## Member

> Kim eunsu - kimeunsu1210  
Nam SeungHyeon - namsh1125  
Park TaeHyun - Taehyuny  
Yoon Jueun - 001021

## Project progress

[link](https://www.notion.so/0d3057e468ac43ba8eab58767a4d34fb)
