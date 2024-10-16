<div align="center">
  <img src="pictures/log.png" width="600"/> 
	
[![Stars](https://img.shields.io/github/stars/LINTAO5835/Datasets)](
https://github.com/LINTAO5835/Datasets)
[![Open issue](https://img.shields.io/github/issues/LINTAO5835/Datasets)](
https://github.com/LINTAO5835/Datasets/issues)

</div>


> [<img src="pictures/log.png" height="20" width="80"/>](https://github.com/LINTAO5835/Datasets) [**CGADNet**](https://github.com/LINTAO5835/Datasets)
> 
> [<img src="https://raw.githubusercontent.com/ultralytics/assets/main/im/banner-yolo-vision-2023.png" height="20" width="80"/>](https://github.com/ultralytics/ultralytics) [**YOLOv8**](https://github.com/ultralytics/ultralytics)
>
> [<img src="https://github.com/open-mmlab/mmdetection/blob/main/docs/zh_cn/_static/image/mmdet-logo.png?raw=true" height="20" width="80"/>](https://github.com/open-mmlab/mmdetection) [**MMdetection**](https://github.com/ultralytics/ultralytics)


# **Abstract**

In the context of edge environments with constrained resources, realizing real-time and
robust crosswalk and guide arrow detection poses a significant challenge for autonomous driving
systems. This paper proposes a crosswalk and guide arrow detection network (CGADNet), a
lightweight visual neural network derived from YOLOv8. Specifically designed for the swift and
accurate detection of crosswalks and guide arrows within the field of view of the vehicle, the
CGADNet can seamlessly be implemented on the Jetson Orin Nano device to achieve real-time
processing. In this study, we incorporated a novel C2f_Van module based on VanillaBlock, employed
depth-separable convolution to reduce the parameters efficiently, utilized partial convolution (PConv)
for lightweight FasterDetect, and utilized a bounding box regression loss with a dynamic focusing
mechanism—WIoUv3—to enhance the detection performance. In complex scenarios, the proposed
method in the stability of the mAP@0.5 was maintained, resulting in a 4.1% improvement in the
mAP@0.5:0.95. The network parameters, floating point operations (FLOPs), and weights were
reduced by 63.81%, 70.07%, and 63.11%, respectively. Ultimately, a detection speed of 50.35 FPS was
achieved on the Jetson Orin Nano. This research provides practical methodologies for deploying
crosswalk and guide arrow detection networks on edge computing devices.

![CGADNet](pictures/yolov8.png)

## Contributions

- **In this study, we adopted the minimalist design concept and used VanillaBlock to build
an innovative C2f_Van module, effectively reducing the complexity of the model. To
reduce the network parameters, deep separable convolutional networks were designed
to achieve lightweight models.**
- **To reduce the computation of the network and improve the detection speed of the
model, a PConv-based fast detection header called FasterDetect was designed to
replace the detection header in the Yolov8 network. Such a mechanism makes it easy
for models to be deployed and run on edge computing devices. In addition, a boundary
box regression loss (WIoUv3) function based on a dynamic non-monotone focusing
mechanism was designed to improve the recognition accuracy and generalization
ability of the model.**
- **Through collection and meticulous annotation, the CADG database for the detection
of crosswalks and guidance arrows on urban roads was made. The dataset contains
24,560 high-resolution images of crosswalks and directional arrows on urban roads
in real, complex scenarios, including rain, fog, night, dim light, and broken sidewalk
markings. Through data training in different scenarios, the adaptability of the model
to complex environment detection was realized.**



## 数据集
![Datasets](pictures/datasets.png)
The trainsets contains  24560 images, includes training and verification set, and the file structure format is YOLOv5 likes:
```
LINTAO5835
-----------------------------------------------------------------------------------------------------
|			COCO:			 |			YOLO:			    |
-----------------------------------------------------------------------------------------------------
| |--LT_coco_datasets24560		    	 | |--LT_yolo_datasets24560			    |
|  --|--annotations  # All Annotations	    	 |   --|--train		# Training		    |
|     --train.json				 |	--|--images	# Trainning Images	    |
|     --val.json				 |	   -- xxx.jpg				    |
|     --test.json				 |	   -- ...				    |
|  --|--train	     # Training Images	    	 |	--|--labels	# Trainning Labels	    |
|     -- xxx.jpg				 |	   -- xxx.txt				    |
|     -- ...					 |	   -- ...				    |
|  --|--val	     # Corresponding Validation  |   --|--val		# Corresponding Validation  |
|  --|--test	     # Corresponding Testing	 |   --|--test		# Corresponding Testing	    |
|----------------------------------------------------------------------------------------------------
```
<table>
	<tr align="center">
		<th>类型</th>
		<th colspan="2">train & val</th>
        	<th>test</th>
        	<th>password</th>
	</tr>
	<tr align="center">
		<th>COCO</th>
		<td colspan="2"><a href="https://www.alipan.com/s/xifh3FSzhHv">Google Drive</a> | <a href="https://www.alipan.com/s/xifh3FSzhHv">ADrive </a></td>
        	<td rowspan="2">--</td>
        	<td rowspan="2">ltcvi638</td>
    	</tr>
    	<tr align="center">
		<th>YOLO</th>
  		<td colspan="2"><a href="https://www.alipan.com/s/xifh3FSzhHv">Google Drive</a> | <a href="https://www.alipan.com/s/xifh3FSzhHv">ADrive </a></td>
    	</tr>
</table>

## 模型

![Visualization](pictures/Visualization.png)

<table>
	<tr align="center">
		<th>Model</th>
		<th>mAP@0.5</th>
		<th>mAP@0.5:0.95</th>
        	<th>FPS</th>
        	<th>Params</th>
	 	<th>PLOPs</th>
 		<th>Weights</th>
		<th>Download</th>
	</tr>
	<tr align="center">
		<th>YOLOv8</th>
		<th>98.3</th>
		<th>69.0</th>
        	<th>43.82</th>
        	<th>11.13</th>
	 	<th>28.4</th>
 		<th>22.5</th>
		<td rowspan="2"><a href="https://www.alipan.com/s/xifh3FSzhHv">Google Drive</a> | <a href="https://www.alipan.com/s/xifh3FSzhHv">ADrive </a></td>
    	</tr>
    	<tr align="center">
		<th>CADNet</th>
		<th>98.3</th>
		<th>73.1</th>
        	<th>50.35</th>
        	<th>4.03</th>
	 	<th>8.5</th>
 		<th>8.3</th>
    	</tr>
</table>

## 致谢
CGADNet是一款由LINTAO共同参与贡献的开源项目。我们感谢所有为项目提供算法复现和新功能支持的贡献者，以及提供宝贵反馈的用户。 我们希望这个工具箱和基准测试可以为社区提供灵活的代码工具，供用户复现已有算法并开发自己的新模型，从而不断为开源社区提供贡献。


## 引用
如果你在研究中使用了CGADnet的数据集，请参考如下 bibtex 引用 CADNet。

```latex

@Article{app14209445,
AUTHOR = {Wang, Guangxing and Lin, Tao and Dong, Xiwei and Wang, Longchun and Leng, Qingming and Shin, Seong-Yoon},
TITLE = {CGADNet: A Lightweight, Real-Time, and Robust Crosswalk and Guide Arrow Detection Network for Complex Scenes},
JOURNAL = {Applied Sciences},
VOLUME = {14},
YEAR = {2024},
NUMBER = {20},
ARTICLE-NUMBER = {9445},
URL = {https://www.mdpi.com/2076-3417/14/20/9445},
ISSN = {2076-3417},
ABSTRACT = {In the context of edge environments with constrained resources, realizing real-time and robust crosswalk and guide arrow detection poses a significant challenge for autonomous driving systems. This paper proposes a crosswalk and guide arrow detection network (CGADNet), a lightweight visual neural network derived from YOLOv8. Specifically designed for the swift and accurate detection of crosswalks and guide arrows within the field of view of the vehicle, the CGADNet can seamlessly be implemented on the Jetson Orin Nano device to achieve real-time processing. In this study, we incorporated a novel C2f_Van module based on VanillaBlock, employed depth-separable convolution to reduce the parameters efficiently, utilized partial convolution (PConv) for lightweight FasterDetect, and utilized a bounding box regression loss with a dynamic focusing mechanism—WIoUv3—to enhance the detection performance. In complex scenarios, the proposed method in the stability of the mAP@0.5 was maintained, resulting in a 4.1% improvement in the mAP@0.5:0.95. The network parameters, floating point operations (FLOPs), and weights were reduced by 63.81%, 70.07%, and 63.11%, respectively. Ultimately, a detection speed of 50.35 FPS was achieved on the Jetson Orin Nano. This research provides practical methodologies for deploying crosswalk and guide arrow detection networks on edge computing devices.},
DOI = {10.3390/app14209445}
}
```
