# CDAL-OW-DFA

This folder contains the implementation of the OW-DFA experiments.

Our implementation is based on the Pytorch version code of [CPL](https://github.com/TencentYoutuResearch/OpenWorld-DeepFakeAttribution).


## Dataset

- Prepare Deepfake Detection datasets

  |     Dataset     |                                 Paper                                 |                                                 Link                                                  |
  | :-------------: | :-------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------: |
  | FaceForensics++ |     FaceForensics++: Learning to Detect Manipulated Facial Images     |      [Paper](https://arxiv.org/abs/1901.08971) [Code](https://github.com/ondyari/FaceForensics)       |
  |    Celeb-DF     |  Celeb-DF: A Large-scale Challenging Dataset for DeepFake Forensics   | [Paper](https://arxiv.org/abs/1909.12962) [Code](https://github.com/yuezunli/celeb-deepfakeforensics) |
  |   ForgeryNet    | ForgeryNet: A Versatile Benchmark for Comprehensive Forgery Analysis  | [Paper](https://arxiv.org/abs/2103.05630) [Home](https://yinanhe.github.io/projects/forgerynet.html)  |
  |      DFFD       |             On the Detection of Digital Face Manipulation             |     [Paper](https://arxiv.org/abs/1910.01717) [Home](https://cvlab.cse.msu.edu/project-ffd.html)      |
  |   ForgeryNIR    | ForgeryNIR: Deep Face Forgery and Detection in Near-Infrared Scenario |  [Paper](https://ieeexplore.ieee.org/document/9693897) [Code](https://github.com/AEP-WYK/forgerynir)  |
  |      DF^3       | GLFF: Global and Local Feature Fusion for AI-synthesized Image Detection |  [Paper](https://arxiv.org/abs/2211.08615) [Code](https://github.com/littlejuyan/GLFF)  |

- Download dataset and unzip data under the directory of `/Datasets/deepfakes_detection_datasets/`
- Process dataset with script `scripts/preprocess/create_academic_meta.ipynb`, and you will get the following structure:

  ```bash
  data/release
  ├── AttributeManipulation
  │   ├── FaceAPP
  │   │   └── DFFD
  │   ├── MaskGAN
  │   │   └── ForgeryNet
  │   ├── SC-FEGAN
  │   │   └── ForgeryNet
  │   ├── StarGAN
  │   │   └── DFFD
  │   └── StarGAN2
  │       └── ForgeryNet
  ├── EntireFaceSyncthesis
  │   ├── CycleGAN
  │   │   └── ForgeryNIR
  │   ├── PGGAN
  │   │   └── DFFD
  │   ├── StyleGAN
  │   │   └── DFFD
  │   └── StyleGAN2
  │       ├── ForgeryNet
  │       └── ForgeryNIR
  ├── ExpressionTransfer
  │   ├── ATVG-Net
  │   │   └── ForgeryNet
  │   ├── Face2Face
  │   │   └── faceforensics
  │   ├── FOMM
  │   │   └── ForgeryNet
  │   ├── NeuralTextures
  │   │   └── faceforensics
  │   └── Talking-Head-Video
  │       └── ForgeryNet
  ├── IdentitySwap
  │   ├── DeepFaceLab
  │   │   └── ForgeryNet
  │   ├── Deepfakes
  │   │   └── faceforensics
  │   ├── FaceShifter
  │   │   └── ForgeryNet
  │   ├── FaceSwap
  │   │   └── faceforensics
  │   └── FSGAN
  │       └── ForgeryNet
  ├── RealFace
  │   └── Real
  │       ├── CelebDF
  │       └── faceforensics
  ├── meta_data
  │   ├── Protocol1_openset_fake_large_merge_meta.csv
  │   ├── Protocol1_openset_fake_val_merge_meta.csv
  │   ├── Protocol2_openset_real_fake_large_merge_meta.csv
  │   └── Protocol2_openset_real_fake_val_merge_meta.csv
  └── shape_predictor_68_face_landmarks.dat
  ```


## Prerequisites
```bash
conda create --name owdfa python=3.9 -y
pip3 install -r requirements.txt
wandb offline
```

## Training
  - Run the following code:
  ```
  python train.py -c configs/train.yaml
  ```
## Testing

  - Run the following code:
  ```
  python eval.py -c configs/eval.yaml
  ```
