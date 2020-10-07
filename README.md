# Webcam-Image-Classifier-in-the-Rock-Paper-Scissors-Lizard-Spock

 The file rpsls.html will render a live stream of the webcam, a button to start the inference, a button to end the inference and the output results.
 It will also initialize everything you need to start capturing from the webcam and converting that data to tensors, which then will be used to train the network.
 The script webcam.js has been open sourced by Google as a library that manages the webcam in the browser and in particular for capturing images to tensors.  
 The script index.js  initialize the webcam with it , load the JSON model from the hosted URL and load it into an object and get one of the output layers from the pretrained mobilenet.The layer conv_pw_13_relu is selected and everything above that will freeze. A new model was created and took as input the selected layer. 
 The script rpsls.js loads the dataset class. As we add new examples to the dataset, we keep track of their labels. The examples is the prediction for the image from the truncated MobileNet. The labei is the values 0, 1, 2, 3 or 4 for rock, paper, scrissors, lizard, spook accordingly. Then, the labels are encoded using one-hot encoding for the training.
 
The architecture of the model is as follows:  
Flattened Output from the the MobileNet that we created earlier by truncated the MobileNet  
A 100-unit hidden dense layer with Relu activation function  
A 3-unit dense layer with Softmax  activation function     

The model is compiled with the Adam Optimizer and categoricalCrossentropy as it is trained for multiple classes. 
The model takes the dataset (x's and y's) training for 10 epochs. On each batch the loss will be logged out.  

We took five different samples: rock, paper, scissors, lizard, Spock to classify the gestures that was feed to the webcam.
The procedure was as follows:
1. Capturing the Samples
2. Encoded the for training
3. Training the neural network with the transfered features from the MobileNet
4. Get prediction
5. Evaluate the prediction and update UI
6. Clean up
 
 Rock Paper Scissors Lizard Spock from the TV Show “The Big Bang Theory” . More information: https://the-big-bang-theory.com/rock-paper-scissors-lizard-spock/. 
