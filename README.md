# YOLO_v3

- Programmers Devcourse perception 6th
- Week 12 YOLO v3

## YOLOv3란?
YOLO Offical Website : https://pjreddie.com/darknet/yolo/
AlexAB's Github : https://github.com/AlexeyAB/darknet

- Darknet53이라는 Backbone 사용
    - Feature extract
    - Feature map : 객체를 예측할 수 있음
    - 
- 3단계의 Bounding box로 객체를 예측
- Model configure file
    - .cfg 파일
    - Model architecture, Hyperparameters(Learning mate, steps 등을 설정), Data augmentation, Input resolution 등의 정보를 담고 있음

- 해당 프로젝트에서 Darknet 대신 Pytorch 사용

## Prepare data
- YOLO format
    - Image와 Annotation files가 함께 있음
    - train.list와 eval.list를 사용
- Pascal VOC format
    - Image / Annotation 따로 관리
    - 초심자가 하기 편함

### Annotation labeling format
- YOLO labeling format
    - [Class_index] [x_center] [y_center] [width] [height]
    - x, y, w, h는 [0, 1]로 normalize

### Download Data
- KITTI Dataset
    - KITTI Dataset -> object -> [left color images of object], [training labels of data set] (총 12GB++)
    - label format을 변경해 줘야 한다(KITTI -> YOLO).
        - 제공되었음.


## TODO
- Using Pytorch
- Dataloader
    - 
    - Local 경로의 이미지를 불러와 전처리, Annotation된 파일을 Pytorch에 맞게 Parsing
- Model
    - Yolo v3 모델을 만들어 보기
        - config 파일을 읽어 내용 Parsing
        - Network가 몇 개 Layers로 이루어져 있는지
        - 각각의 convolution layer에는 stride나 padding이 몇으로 설정돼 있고
        - 또는 Batch Nom layer가 있는지, 어떤 Activation Layer을 사용할지
- Train/eval logic
    - Input / Output을 통해 Loss를 구하고, 개선하는 Logic
    - Output과 GT를 비교해 성능을 비교
- Loss
    - 실제로 Deeplearning model을 설정할 때, 원하는 결과를 얻으려면 gt 값과 얼마나 유사한지 판단하는 기준이 되는 Loss function

### 준비물
- 제공된 __kitti_training_annotations_yolo__
    - Labeling 완료된 training data
- __yolov3_kitti.cfg__

## Codes
### Data 저장하기
- Windows : dir /b /s .\Annotations\*.txt > train.txt
    - train.txt 파일의 경로, 확장자를 지워 주자
    - notepad++를 사용하면 편하다.
- testing 폴더도 진행해 주자. YOLO_v3\KITTI\testing>dir /b /s .\JPEGImages\*.png > test.txt
