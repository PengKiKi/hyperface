# Hyper Face #
[Hyper Face](https://arxiv.org/abs/1603.01249) implementation which predicts face/non-face, landmarks, pose and gender simultaneously.

This is NOT official implementation.

## Features ##
* `Chainer` implementation
* Image viewer on web browsers

## Testing Environments ##
### Ubuntu 14.04 ###
* Python 2.7
* Chainer 1.14.0
* OpenCV 2.4.9
* Flask 0.11.1
* Flask_SocketIO 2.4

### Arch Linux ###
* Python 3.5
* Chainer 1.14.0
* OpenCV 3.1.0
* Flask 0.10.1
* Flask_SocketIO 2.2

## Configuration ##
Important variables are configured by `config.json`.
set `gpu` positive number to use GPU, port numbers of web servers and so on.

## Train ##

### Prepare ###
Download [AFLW Dataset](https://lrs.icg.tugraz.at/research/aflw/) and [AlexNet Caffe Model](https://github.com/BVLC/caffe/tree/master/models/bvlc_alexnet), expand them and set `aflw_sqlite_path`, `aflw_imgdir_path`, and `alexnet_caffemodel_path` in `config.json`

### Pretrain with Face_RCNN model ###
```bash
python ./scripts/train.py --pretrain
```
Open `http://localhost:8888/`, `http://localhost:8889/` and `http://localhost:8890/` with your web browser to see loss graphs, network weights and predictions.
Port numbers are configured by `config.json`.

### Main train ###
```bash
python ./scripts/train.py --pretrainedmodel result_pretrain/model_epoch_40
```
Use arbitrary epoch number instead of 40.

## Test ##
```
python ./scripts/use_on_test.py --model result/model_epoch_190 
```
Open `http://localhost:8891/` to see predictions.

### Result on AFLW test images ###
<img src="https://raw.githubusercontent.com/takiyu/hyperface/master/screenshots/face.png">
<img src="https://raw.githubusercontent.com/takiyu/hyperface/master/screenshots/nonface.png">