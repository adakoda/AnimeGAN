# AnimeGAN   

A Tensorflow implementation of AnimeGAN for fast photo animation !        [日本語](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/doc/Japanese_README.md)  
The paper can be accessed [here](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/doc/Chen2020_Chapter_AnimeGAN.pdf) or on the [website](https://link.springer.com/chapter/10.1007/978-981-15-5577-0_18).  
  
**Online access**:  Be grateful to [@TonyLianLong](https://github.com/TonyLianLong/AnimeGAN.js) for developing an online access project, you can implement photo animation through a browser without installing anything, [click here to have a try](https://animegan.js.org/).  
  
**Good news**:  tensorflow-1.15.0 is compatible with the code of this repository. In this version, you can run this code without any modification. [The premise is that the CUDA and cudnn corresponding to the tf version are correctly installed](https://tensorflow.google.cn/install/source#gpu). Maybe the versions between tf-1.8.0 and tf-1.15.0 are also supported and compatible with this repository, but I didn’t make too many extra attempts.  

  
-----  
This is the Open source of the paper <AnimeGAN: a novel lightweight GAN for photo animation>, which uses the GAN framwork to transform real-world photos into anime images.  
  
**Some suggestions:**   
1. since the real photos in the training set are all landscape photos, if you want to stylize the photos with people as the main body, you may as well add at least 3000 photos of people in the training set and retrain to obtain a new model.  
2. In order to obtain a better face animation effect, when using 2 images as data pairs for training, it is suggested that the faces in the photos and the faces in the anime style data should be consistent in terms of gender as much as possible.  
3. The generated stylized images will be affected by the overall brightness and tone of the style data, so try not to select the anime images of night as the style data, and it is necessary to make an exposure compensation for the overall style data to promote the consistency of brightness and darkness of the entire style data.  

**News:**  AnimeGAN+ will be expected to be released this summer.(TBD)  

___  

## Requirements  
- python 3.6  
- tensorflow-gpu 
   - tensorflow-gpu 1.8.0  (ubuntu, GPU 1080Ti or Titan xp, cuda 9.0, cudnn 7.1.3)  
   - tensorflow-gpu 1.15.0 (ubuntu, GPU 2080Ti, cuda 10.0.130, cudnn 7.6.0)  
- opencv  
- tqdm  
- numpy  
- glob  
- argparse  
  
## Usage  
### 1. Download vgg19 or Pretrained model  
> [vgg19.npy](https://github.com/TachibanaYoshino/AnimeGAN/releases/tag/vgg16%2F19.npy)  
  
> [Pretrained model](https://github.com/TachibanaYoshino/AnimeGAN/releases/tag/Haoyao-style_V1.0)  

### 2. Download dataset  
> [Link](https://github.com/TachibanaYoshino/AnimeGAN/releases/tag/dataset-1)  

### 3. Do edge_smooth  
  eg. `python edge_smooth.py --dataset Hayao --img_size 256`  
  
### 3. Train  
  eg. `python main.py --phase train --dataset Hayao --epoch 101 --init_epoch 1`  
  
### 4. Test  
  eg. `python main.py --phase test --dataset Hayao`  
  or `python test.py --checkpoint_dir checkpoint/AnimeGAN_Hayao_lsgan_300_300_1_3_10 --test_dir dataset/test/real --style_name H`  
  
____  
## Results  
:blush:  pictures from the paper 'AnimeGAN: a novel lightweight GAN for photo animation'  
  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/doc/sota.png)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/doc/e2.png)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/doc/e3.png)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/doc/e4.png)  
  
:heart_eyes:  Photo  to  Hayao  Style  
  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(37).jpg)![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(37).jpg)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(1).jpg)![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(1).jpg)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(20).jpg) ![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(20).jpg)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(21).jpg) ![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(21).jpg)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(22).jpg) ![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(22).jpg)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(23).jpg) ![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(23).jpg)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(24).jpg) ![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(24).jpg)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(46).jpg) ![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(46).jpg)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(30).jpg) ![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(30).jpg)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(28).jpg) ![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(28).jpg)  
![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo/1%20(38).jpg) ![](https://github.com/TachibanaYoshino/AnimeGAN/blob/master/result/Hayao/photo_result/1%20(38).jpg)  
____  
## Acknowledgment  
This code is based on the [CartoonGAN-Tensorflow](https://github.com/taki0112/CartoonGAN-Tensorflow/blob/master/CartoonGAN.py) and [Anime-Sketch-Coloring-with-Swish-Gated-Residual-UNet](https://github.com/pradeeplam/Anime-Sketch-Coloring-with-Swish-Gated-Residual-UNet). Thanks to the contributors of this project.  

