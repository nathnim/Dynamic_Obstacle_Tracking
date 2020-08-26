# Yolov5 + Deep Sort with PyTorch

## Introduction

This repository contains a moded version of PyTorch YOLOv5 (https://github.com/ultralytics/yolov5). It filters out every detection that is not a person. The detections of persons are then passed to a Deep Sort algorithm (https://github.com/ZQPei/deep_sort_pytorch) which tracks the persons. The reason behind the fact that it just tracks persons is that the deep association metric is trained on a person ONLY datatset.

For more detailed information about the algorithms and their corresponding lisences used in this project access their official github implementations.

## Description

The implementation is based on two papers:

- Simple Online and Realtime Tracking with a Deep Association Metric
https://arxiv.org/abs/1703.07402
- YOLOv4: Optimal Speed and Accuracy of Object Detection
https://arxiv.org/pdf/2004.10934.pdf

## Requirements

Python 3.7 or later with all requirements.txt dependencies installed, including torch >= 1.5. To install run:

`pip install -U -r requirements.txt`


## Before you run the tracker

Github block pushes of files larger than 100 MB. Hence you need to download two different weights: the ones for yolo and the ones for deep sort.

- download the yolov5 weight from https://drive.google.com/drive/folders/1Drs_Aiu7xx6S-ix95f9kNsA6ueKRpN2J and place the downlaoded `.pt` file under `yolov5/weights/`
- download the deep sort weights from https://drive.google.com/drive/folders/1xhG0kRH1EX5B9_Iz8gQJb7UNnn_riXi6. Place ckpt.t7 file under`deep_sort/deep_sort/deep/checkpoint/`

## Tracking

`track.py` runs tracking on any video source:

example:  

```bash
python3 track.py --weights yolov5/weights/yolov5x.pt --source ...
```

- Video:  `--source file.mp4`
- Webcam:  `--source 0`
- RTSP stream:  `--source rtsp://170.93.143.139/rtplive/470011e600ef003a004ee33696235daa`
- HTTP stream:  `--source http://wmccpinetop.axiscam.net/mjpg/video.mjpg`

## Other information

Further work: Predict trajectories for tracked objects.

