# pytorch-cifar10-fp16
Train with FP16, let's see if you get faster training.
Thanks FastAI for the pytorchFP16 training util codes.

FP16@res18.. 10sec/epoch

FP32@res18.. 15sec/epoch

with RTX2080ti.

## Usage

```
git clone https://github.com/kentaroy47/pytorch-cifar10-fp16.git
cd pytorch-cifar10-fp16
export CUDA_VISIBLE_DEVICES=0

# train by resnet18
python train_cifar10.py --fp16 # for fp16 training
python train_cifar10.py # for fp32 training

# train by resnet50
python train_cifar10.py --fp16 --arch res50 # for fp16 training
python train_cifar10.py --arch res50 # for fp32 training

```
