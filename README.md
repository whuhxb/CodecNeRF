# CodecNeRF: Toward Fast Encoding and Decoding, Compact, and High-quality Novel-view Synthesis


### AAAI 2025
[[`arXiv`](https://arxiv.org/abs/2404.04913)]
[[`Project Page`](https://gynjn.github.io/CodecNeRF/)]

This repository contains code for "CodecNeRF: Toward Fast Encoding and Decoding, Compact, and High-quality Novel-view Synthesis".

Clone the repository:
```
git clone https://github.com/Gynjn/CodecNeRF.git
```

## Setting up Environment

### Install required packages (CUDA 11.8 example)
```
conda create -n codecnerf python=3.10 -y
conda activate codecnerf
pip install torch torchvision --index-url https://download.pytorch.org/whl/cu118
pip install git+https://github.com/NVlabs/tiny-cuda-nn/#subdirectory=bindings/torch
pip install opencv-python imageio imageio-ffmpeg timm configargparse einops dahuffman vector-quantize-pytorch compressai scipy torchmetrics matplotlib loralib pandas gdown transformers jaxtyping tensorboard tensorboardX lpips
pip install -U xformers --index-url https://download.pytorch.org/whl/cu118
```

# Run example
Download the pretrained model weights from https://huggingface.co/anonymous-submit/submission/tree/main place them to checkpoints folder.

Run finetune (ec means W/ entropy coding).
  ```
  python finetune.py --config configs/finetune.txt
  python finetune_ec.py --config configs/finetune_ec.txt
  ```
  If you want to perform entropy coding on tensor and MLP both, then
  ```
  python finetune_ec_weight.py --config configs/finetune_ec_weight.txt
  ```

We provide a few examples in the configuration folder:

  `data_path`, choices = ['camera', 'cake'];
    
  `lrate_mlp`, learning rate of MLP LoRA;

  `lrate_feat`, learning rate of feature map;

  `trank`, tensor decomposition rank;

  `lrank`, MLP LoRA rank;

  `alpha`, MLP LoRA alpha;

  `N_samples`, the number of point in uniform sampling;

  `N_importance`, the number of point in importance sampling;

More options refer to the `opt.py`.

## Citing CodecNeRF

```
@article{kang2024codecnerf,
  title={CodecNeRF: Toward Fast Encoding and Decoding, Compact, and High-quality Novel-view Synthesis},
  author={Kang, Gyeongjin and Lee, Younggeun and Park, Eunbyung},
  journal={arXiv preprint arXiv:2404.04913},
  year={2024}
}
```
