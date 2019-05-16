# Training Cifar-10 with FP16 (half) precision @Pytorch
Train with FP16, let's see if you get faster training.

## why FP16?
- smaller GPU memory

- faster training

Thanks FastAI for the pytorchFP16 training util codes.

Tensorcoreを使うことで演算速度がFP32に対する大幅な高速化が（スペック的に）期待できる。

どれくらい早くなるか、Pytorchでどう書けばFP16が使えるかなど記述する。

## Qiita article
https://qiita.com/arutema47/items/d9e097f00b0b4934d07a

こちらにより詳しい解説があります。

## Training speed with FP16 and FP32

### resnet 18
FP16@res18.. 10sec/epoch batch = 128

FP16@res18.. 8sec/epoch batch = 512

FP32@res18.. 15sec/epoch batch = 128

almost 2x speed up.

### resnet 50

FP16@res50.. 27sec/epoch batch = 512

FP32@res50.. 61sec/epoch batch = 512

2x speed up.

with RTX2080ti.

Note that Ampere cores are required for efficient FP16 training.

You should play around with minibatch size for best performance.

TensorCores are used to boost up the training speed!!

## Usage

```
git clone https://github.com/kentaroy47/pytorch-cifar10-fp16.git
cd pytorch-cifar10-fp16
export CUDA_VISIBLE_DEVICES=0

# train by resnet18
python train_cifar10.py --fp16 # for fp16 training
python train_cifar10.py # for fp32 training

# train by resnet50
python train_cifar10.py --fp16 --net res50 # for fp16 training
python train_cifar10.py --net res50 # for fp32 training

```
