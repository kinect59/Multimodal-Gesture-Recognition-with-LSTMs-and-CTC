# Multimodal-Gesture-Recognition-with-LSTMs-and-CTC
An end-to-end system that performs temporal recognition of gesture sequences using speech and skeletal input. The model combines two LSTM networks with a CTC output layer that spot and classify gestures from two continuous streams.

We used keras and tensorflow to build our networks.

This project was built for the ChaLearn 2013 dataset. We trained and tested the model using the dataset of the challenge. The data can be downloaded here. http://sunai.uoc.edu/chalearn/#tabs-2 

This model achieves 85% accuracy on the test set of the ChaLearn 2013 challenge.

In order to train the models provided here you need to preprocess the data:
1) MFCC features need to be extracted from the audio .wav files. We used 13 MFCC features as well as the first and second order derivatives (total 39 features). We used the HTK toolkit to extract the features. Here we just provide the configuration file for HCopy (the feature extraction tool for HTK). If you want to use HTK for this purpose you can find it here http://htk.eng.cam.ac.uk/

2) Once the MFCC features are extracted just put the training data all in one big csv file along with the labels (same for the validation and test data) and you are ready to train the speech lstm network. 

3) For the skeletal features you should provide the joint positions for each file in one csv file each and run the following scripts:

	a) extract_activity_feats.py

	b) gather_skeletal.py
	
	c) skeletal_feature_extraction.py

4) Now you are ready to train the skeletal lstm network.

5) Once both networks are trained you can train the multimodal fusion network.

6) Use the sequence_decoding.py script to evaluate the trained model with test data.

The training of the complete system takes approximately 80 hours in an nvidia 1060 gtx.

Dependencies:

1) numpy

2) pandas

3) tensorflow

4) keras

5) sklearn

6) scipy
