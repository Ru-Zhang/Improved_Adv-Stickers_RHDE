# Improvement of Adversarial Stickers
In this repository, we provide the code based on the paper [Adversarial Stickers: A Stealthy Attack Method in the Physical World](https://ieeexplore.ieee.org/abstract/document/9779913) which proposes an attack method to embed a sticker into a face image. 

## Preparation

### Environment Settings:
Install conda, and create a new environment with Python 3.8.11.
`conda create -n adv_sticker python=3.8.11`
`conda activate adv_sticker`
`pip install -r requirements.txt`

### Data Preparation：
+ face
Please download the dataset ([LFW](https://drive.google.com/file/d/0B7EVK8r0v71pZDFOOGxhbm1oakE/view?usp=share_link&resourcekey=0-OvdR0Gk5lY7a8r5FjKIYhA), place it in ```./datasets/``` and rename the directory to ```lfw_images```.

The directory structure example is:
```
datasets
-datasets name
 --person 1
   ---pic001
   ---pic002
   ---pic003  
```
+ stickers
Prepare the pre-defined stickers and place them in ```./stickers/```.

### Model Preparation：
Tool model ([FaceNet](https://github.com/timesler/facenet-pytorch) should be placed in ```./models/```. If the model is replaced, ```./utils/predict.py``` should be changed as needed.

### Other Necessary Tools:
+ Python tools for [3D face](https://github.com/YadiraF/face3d/tree/master/face3d). The tool has included in the repository.

*Due to the limit of big file size, we cannot upload the BFM model and Shape predictor for face landmarks. Please download them from the following links and place them in right path.*
+ BFM Data (https://drive.google.com/file/d/1sTNEi7MGMe-azOkAtc5bg6QuEwFI1XvT/view?usp=share_link). Please download it and then place it in ```./BFM/```.
+ Shape predictor for face landmarks ([68](https://github.com/r4onlyrishabh/facial-detection/tree/master/dataset), [81](https://github.com/codeniko/shape_predictor_81_face_landmarks)). Please place them in root directory which is same as the file ```attack_single.py```.

## Attack
Hyperparameter settings: ```./utils/config.py```

Running this command for attacking a single image:
```
python attack_single.py
```

Successfully attacked images will be saved in ```./results_img/```

# References

## Paper
Adversarial Stickers: A Stealthy Attack Method in the Physical World [Adversarial Stickers: A Stealthy Attack Method in the Physical World](https://ieeexplore.ieee.org/abstract/document/9779913) (TPAMI 2022)

## Code
+ [Adv-Stickers](https://github.com/jinyugy21/Adv-Stickers_RHDE)
+ [Face3D](https://github.com/yfeng95/face3d/tree/master/face3d)
+ [FaceNet](https://github.com/timesler/facenet-pytorch)