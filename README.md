# SVHN Recognition
[![license](https://img.shields.io/github/license/Genius-Society/svhn_recognition.svg)](https://github.com/Genius-Society/svhn_recognition/blob/master/LICENSE)
[![hf](https://img.shields.io/badge/HuggingFace-SVHN-ffd21e.svg)](https://huggingface.co/collections/Genius-Society/svhn-67bc30924b9d3615a6df0b3b)
[![ms](https://img.shields.io/badge/ModelScope-SVHN-624aff.svg)](https://www.modelscope.cn/collections/SVHN-68df87fc64904a)

This project is a PyTorch implementation that uses deep CNN to recognize multi-digit numbers using the SVHN dataset derived from Google Street View house numbers (SVHN), each picture contains a set of numbers from 0 to 9, the model is tested to have 89% accuracy.

## Original dataset
[Street View House Number](http://ufldl.stanford.edu/housenumbers/SVHN) Dateset, sourced from Google Street View house numbers, is provided in Format 1 (Full Numbers), which includes three compressed files: _train.tar.gz_, _test.tar.gz_, and _extra.tar.gz_. Here, _train.tar.gz_ constitutes the training dataset, while _test.tar.gz_ serves as the testing dataset. It is important to note that _extra.tar.gz_ is an additional dataset that is not recommended for use. Within both _train.tar.gz_ and _test.tar.gz_, the following components are included:
1. A collection of PNG images, each depicting a house number.
2. A file named _digitStruct.mat_, which contains the house number corresponding to each image along with the positional information for each individual digit.
3. A file named _see_bboxes.m_, provided solely as an auxiliary tool for processing within the Matlab environment, which can be disregarded.

## Tasks
### Network Design and Training
Develop a neural network that is trained using the data provided in _train.tar.gz_ and subsequently evaluated on the data contained in _test.tar.gz_.

### Testing Constraints
During the testing phase, the positional information contained within the _test.tar.gz/digitStruct.mat_ file must not be used as input. The network must be capable of accurately recognizing the house number in each test image without relying on the provided positional metadata.

### Report Submission
Prepare a comprehensive report that includes:
- A detailed description of the network architecture and the hyperparameters employed.
- An explanation of the training methodology and the optimization techniques used.
- Training curves that illustrate the progression of the training process.
- The recognition accuracy achieved on the testing dataset.

This formulation is intended to guide the development and evaluation of a system for automated recognition of house numbers using the SVHN dataset under the specified constraints.

# Report
The report docs are [here](./docs).

## Environment
```bash
conda create -n py311 python=3.11 -y
conda activate py311
pip install -r requirements.txt
```

## Usage
1. Clone the source code:
```bash
git clone git@github.com:Genius-Society/svhn_recognition.git
cd svhn_recognition
```
2. Run `python train.py`

## Params
<table>
    <tr>
        <th>Steps</th>
        <th>GPU</th>
        <th>Batch Size</th>
        <th>Learning Rate</th>
        <th>Patience</th>
        <th>Decay Step</th>
        <th>Decay Rate</th>
        <th>Accuracy</th>
    </tr>
    <tr>
        <td>122000</td>
        <td>GTX 1080 Ti</td>
        <td>512</td>
        <td>0.01</td>
        <td>100</td>
        <td>625</td>
        <td>0.9</td>
        <td>89.21%</td>
    </tr>
</table>

## Training curve
![](./docs/loss.png)

## Reference
- [Multi-digit Number Recognition from Street View Imagery using Deep Convolutional Neural Networks](http://arxiv.org/pdf/1312.6082.pdf)