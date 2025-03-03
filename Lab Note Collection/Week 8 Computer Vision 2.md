# Week 8: Computer Vision 2

---------------
#### :dizzy: **Lab Date :** March 3, 5
#### :alarm_clock: **Due Date :** 2:00 pm March 19   
#### :pencil: Every group member must be present for every check point.
-------------------

## Task List
> [!CAUTION]
> Pi's Fan will run in full speed. Ensure no objects nearby the fan.

------------------
## 3. Deep Vision Workflow — Fashion MNIST

In this task, we will try the deep-learning-based computer vision. We will go thru the procedures step by step.

We will use **PyTorch** + **Torchvision** as deep vision framework. They are already installed when you installed ```Ultralytics``` 

We will try on a simple dataset -- **Fashion MNIST**.

* Dataset description: https://www.kaggle.com/datasets/zalando-research/fashionmnist
* PyTorch training details: https://pytorch.org/tutorials/beginner/introyt/trainingyt.html

----------------------

- [ ] **Prepare Training Data**

Use ```torchvision.datasets``` to download Fashion MNIST data to your local disk.

https://pytorch.org/vision/0.21/generated/torchvision.datasets.FashionMNIST.html

- [ ] **Check the Data**

Open your file folder to double check. You should have 8 files in 4 different names (4 compressed .gz, 4 raw ubyte). They are:
* training set images
* training set labels
* testing set images
* testing set labels

Start a new .py, use ```torchvision.datasets``` to load downloaded dataset. Then use ```matplotlib``` to display some images and their labels.

<img src="Pic/Figure_1.png" height="500"> 

- [ ] **Train Neural Network**
> [!TIP]
> The training can be done in your own laptop or any Cloud platform (such as Google Colab) for speeding up.
> 
Start over a new .py. Use ```torch.nn``` to create a neural network. Then train the neural network in the Pi.

* Remember to do ```torch.device("cpu")``` for Pi, not ```gpu```
* Record your training time. expect to be >20 minutes.
* Save the trained model in your local disk.

```shell
>>> %Run -c $EDITOR_CONTENT
Epoch 1/10, Loss: 0.5135, Time: 135.63 sec
Epoch 2/10, Loss: 0.3023, Time: 131.29 sec
Epoch 3/10, Loss: 0.2528, Time: 130.57 sec
Epoch 4/10, Loss: 0.2234, Time: 165.76 sec
Epoch 5/10, Loss: 0.2018, Time: 163.32 sec
Epoch 6/10, Loss: 0.1779, Time: 146.26 sec
Epoch 7/10, Loss: 0.1628, Time: 157.00 sec
Epoch 8/10, Loss: 0.1448, Time: 161.22 sec
Epoch 9/10, Loss: 0.1313, Time: 162.27 sec
Epoch 10/10, Loss: 0.1145, Time: 162.21 sec
Total training time: 1515.51 sec
Model trained and saved as /home/cao/Downloads/fashion_mnist_optimized.pth
```

- [ ] **Inference with Real Image**

* Place a fashion item before a background. There are 10 accepted item types. They can be found in previous [kaggle hyperlink](https://www.kaggle.com/datasets/zalando-research/fashionmnist).

* Take a photo of it. Ensure clean background and high contrast between item and background. (I used my phone to take picture)

* Preprocess images to convert them to the same style as Fashion MNIST images. (I used my photo-edit app to crop and filter. Then I upload the image to ChatGPT and ask it to generate code that: "use opencv to preprocess the uploaded image for Fashion MNIST dataset. Ensure clear edge and good contrast." )

* Then, start over a new .py file. Use your previously trained neural networks and perform inference on the images. Also record the inference time.

* Does it predict the correct label?

| **Raw Image** |**Preprocessed then Perform Prediction** |
|---------|---------|
| <img src="Pic/1000028901.jpg" height="350"> | <img src="Pic/Figure_2.png" height="400"> |

```shell
>>> %Run caopredict.py
Predicted Class: Bag
Inference Time: 0.0048 seconds
```

🎉 **Check Point 3**

------------------
## 4. Real-Time Deep Vision for Embedded System  — MobileNet

In the first task, when you run YOLO in Pi5, it runs slowly. 

Let's narrow down the scope, instead of finding multiple objects on an image (YOLO), we now just try a figure out a single object.

In this task, we introduce a fast method for such task: **MobileNet** , this works well for embedded systems

You can access a **pretrained MobileNetV2 model in PyTorch**, https://pytorch.org/vision/main/models/generated/torchvision.models.mobilenet_v2.html

It is trained on **ImageNet-1K dataset**: https://en.wikipedia.org/wiki/ImageNet#ImageNet-1K 

Such pre-trained MobileNetV2 can predict 1000 different objects: 

* Standard naming: https://github.com/pytorch/hub/blob/master/imagenet_classes.txt ; 
* Alternative American-styled naming: https://github.com/anishathalye/imagenet-simple-labels 

#### References

- Sandler, Mark, et al. ["MobileNetV2: Inverted Residuals and Linear Bottlenecks."](https://arxiv.org/abs/1801.04381) *CVPR*, 2018.

-----------------------

Your task is to implement a **real-time object detector** in Pi. In detail:

- [ ] **Use Pre-trained MobileNetV2**

  It is in PyTorch: ```from torchvision.models import MobileNet_V2_Weights```

- [ ] **Stream**

  Use the Pi's USB camera. Stream the real-time video and prediction result in your Pi. Again, if ```cv2.imshow``` not working, use ```flask``` package instead and display the stream on Pi's browser.

- [ ] **FPS**

  Display the real-time frame rate (FPS).

----------
Here are 2 screenshots of my running (This is using ```flask``` package and display in a browser):

| **Screenshot 1** |**Screenshot 2** |
|---------|---------|
| <img src="Pic/bottlepic.png" height="400"> | <img src="Pic/playerpic.png" height="400"> |

🎉 **Check Point 4**


---
