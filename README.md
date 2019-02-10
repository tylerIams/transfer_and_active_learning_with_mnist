# Transfer and Active Learning with MNIST
This repository uses the Keras package's MNIST dataset to practice transfer and active learning.
To perform transfer learning I performed the following steps:
  - Separated the images of digits 0-4 and 5-9 into two groups
  - Created a two layer neural net classification model on digits 0-4 to over 99% accuracy on a test set.
  - Used this model's intermediate layer output to featurize each of the images in the 5-9 group.
  - Exported this data for Active Learning.

To perform active learning I performed the following steps:
  - Sampled 200 random images to serve as my "labeled" set, and left the rest as my unlabeled set.
  - Created a ridge regression model with these 200 images.
  - Used the model to predict the classes of each of the unlabeled images.  I then "labeled" (by adding to my "labeled" set) the 100 predictions with the lowest prediction probabilities.
  - I retrained my model with the larger "labeled" set, and repeated the prediction/probability based selection/retraining steps 150 times.
  - I simultaneously trained a separate ridge regression model with a random sample of 5-9 images of the same size as my labeled set at each iteration, for a control.
  
Finally, I have created a single plot that reprsents the accuracy of each model at predicting each featurized image's class with one group using active learning, and the other group using "passive" or "random" learning.  It can be seen that the active learning group performs markedly better. 
