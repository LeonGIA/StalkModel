# StalkModel
# CREDIT GOES TO EVAN JURAS WHO HOSTED THE ORIGINAL CODE.
# WE HAVE MODIFIED IT TO SUPPORT OUR NEEDS.


This repository contains a live detection model used to detection and track corn stalks.

NOTE: The basis for this model originates from a Jupyter Notebook project on Google Colab found here: https://colab.research.google.com/github/EdjeElectronics/TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi/blob/master/Train_TFLite2_Object_Detction_Model.ipynb#scrollTo=fF8ysCfYKgTP


We adapted the Notebook project to one of our own personal devices as the Google-provided computing resources was not sufficient for the project's needs. The images were annotated with the LabelImg software.


NOTE: The file sizes for the images the model was trained on in addition to the training checkpoints/data were too large to upload to GitHub. They can be provided upon request.


Running the detection model:

NOTE: We recommend installing Anaconda and creating a virtual python environment 

1.) In the Anaconda prompt, navigate to the StalkModel directory and create an environment with the following command

	conda create --name <environment_name> python=3.9
	
2.) Activate the environment with

	conda activate <environment_name>
	
3.) Now we will install the necessary TensorFlow packages

	pip install tensorflow opencv-python protobuf==3.20.*

4.) Run the model

	python TFLite_detection_image.py --modeldir=custom_model_lite --imagedir='DIRECTORY_OF_IMAGES_TO_DETECT
	
NOTE: The python program executes image by image. Any coordinate data is lost when the next image is processed.

NOTE: The following are a list of possible parameters for the detection program

	--modeldir
		The directory of the detection model
	
	--graph
		Name of the .tflite file in the model's directory (ONLY IF THE NAME IS NOT "detect.tflite")
	
	--labels
		Name of the labelmap file in the model's directory (ONLY IF THE NAME IS NOT "labelmap.txt")
		
	--threshold
		The confidence threshold for displaying a detected object. The default value is 0.6 (60%)
		
	--image
		Use if you want to run the detection on a single image. Otherwise, use imagedir for an entire directory
		
	--imagedir
		The directory containing the images you want to run the detection model on
		
	--save_results
		The directory you want to save the annonated detection images to
		
	--noshow_results
		Prevents the rendering of the results for viewing. Should only be used if save_results is in use
		
	--edgetpu
		Outdated, not needed
		
		
NOTE: If you are training the model and encounter the following error

	error: Can't find libdevice directory ${CUDA_DIR}/nvvm/libdevice
	
The following issue tracker can be used to resolve IT

	https://github.com/tensorflow/tensorflow/issues/57055
