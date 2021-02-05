# Automatic-Colorization
Encoder Decoder based automatic colorization model.Solution to [IMGCOL](https://www.aicrowd.com/challenges/ai-blitz-5/problems/imgcol) Dataset is given [here](https://www.kaggle.com/darthgera/colorization)
## Model
We follow this [SIGGRAPH Paper](https://richzhang.github.io/InteractiveColorization/). The model is basically an encoder decoder architecture. We perform regression on the values of `a and b` channel. The model also incorporates sparse user inputs into the colorization aspect. 
![model.PNG](https://github.com/darthgera123/Automatic-Colorization/blob/main/model.PNG)
In the given model,the Local Hints uses the user input and tries to predict a color statistic. The Global Hints section tries to do the same but the user input here is global image color histogram. These are incorporated into the network. This is the classification part.  
This network has been pretrained on imagenet dataset.  

## Loss
MSELoss is typically good enough for image regression. However we are dealing with a multimodal problem, i.e a grayscale input can have multiple output. For eg a same tshirt can be green as well as red. In these situations MSE can penalize very heavily leading to suboptimal results. The paper works around it using SmoothL1Loss or Huber Loss to tackle this problem. It is a robust estimator and doesnt penalize multimodal outputs as harshly.

## Results
![results](https://github.com/darthgera123/Automatic-Colorization/blob/main/results.png)
