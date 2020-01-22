
##################################################################################################

DATA ACCESS FORM:

Please fill out this form that asks for your name, a valid email address and the name of the institution you are affiliated with, to gain access to the data and model weights:

https://docs.google.com/forms/d/1FggY3gRfDUxH8D4hCH-OHwEIHqa2tSdFXwobvM27Qh4/edit

Thank you for your interest. The download link will be sent to your email once the form is completed. 

Please note: The data available through this link are of RGB images, each of shape [64 X 64 X 3]. If a higher resolution dataset is required, please address your request to: 

soumiks@iastate.edu (while cc'ing: sghosal@media.mit.edu)

Users are welcome to create "Issues" within this repository if they face any problems regarding execution and/or deployment of the trained model on their own data-sets or on the shared data: https://github.com/SCSLabISU/xPLNet/issues

##################################################################################################

CITATION:

If you use this dataset and/or the methods proposed in our research please cite our PNAS paper available at:
http://www.pnas.org/content/115/18/4613

Bibtex:

@article {Ghosal4613,
	author = {Ghosal, Sambuddha and Blystone, David and Singh, Asheesh K. and Ganapathysubramanian, Baskar and Singh, Arti and Sarkar, Soumik},
	title = {An explainable deep machine vision framework for plant stress phenotyping},
	volume = {115},
	number = {18},
	pages = {4613--4618},
	year = {2018},
	doi = {10.1073/pnas.1716999115},
	publisher = {National Academy of Sciences},
	issn = {0027-8424},
	URL = {http://www.pnas.org/content/115/18/4613},
	eprint = {http://www.pnas.org/content/115/18/4613.full.pdf},
	journal = {Proceedings of the National Academy of Sciences}
}

##################################################################################################

THE FOLLOWING DESCRIBES THE MODEL ARCHITECTURE AND HYPER-PARAMETERS (use the seed # provided to reproduce the results from the paper):

seed = 1337 (use numpy.random.seed(seed))

Arch 1:
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
conv2d_1 (Conv2D)            (None, 128, 62, 62)       3584      
_________________________________________________________________
batch_normalization_1 (Batch (None, 128, 62, 62)       248       
_________________________________________________________________
conv2d_2 (Conv2D)            (None, 128, 60, 60)       147584    
_________________________________________________________________
max_pooling2d_1 (MaxPooling2 (None, 128, 30, 30)       0         
_________________________________________________________________
batch_normalization_2 (Batch (None, 128, 30, 30)       120       
_________________________________________________________________
conv2d_3 (Conv2D)            (None, 128, 28, 28)       147584    
_________________________________________________________________
max_pooling2d_2 (MaxPooling2 (None, 128, 14, 14)       0         
_________________________________________________________________
batch_normalization_3 (Batch (None, 128, 14, 14)       56        
_________________________________________________________________
conv2d_4 (Conv2D)            (None, 128, 12, 12)       147584    
_________________________________________________________________
max_pooling2d_3 (MaxPooling2 (None, 128, 6, 6)         0         
_________________________________________________________________
batch_normalization_4 (Batch (None, 128, 6, 6)         24        
_________________________________________________________________
conv2d_5 (Conv2D)            (None, 128, 4, 4)         147584    
_________________________________________________________________
max_pooling2d_4 (MaxPooling2 (None, 128, 2, 2)         0         
_________________________________________________________________
flatten_1 (Flatten)          (None, 512)               0         
_________________________________________________________________
dropout_1 (Dropout)          (None, 512)               0         
_________________________________________________________________
dense_1 (Dense)              (None, 500)               256500    
_________________________________________________________________
dropout_2 (Dropout)          (None, 500)               0         
_________________________________________________________________
dense_2 (Dense)              (None, 100)               50100     
_________________________________________________________________
dropout_3 (Dropout)          (None, 100)               0         
_________________________________________________________________
dense_3 (Dense)              (None, 9)                 909       
=================================================================
Total params: 901,877
Trainable params: 901,653
Non-trainable params: 224
_________________________________________________________________

OPTIMIZER USED: Adam (lr = 0.001; the default lr from "Adam: A Method for Stochastic Optimization" by Kingma et al.)
BATCH_SIZE for Training: 60
Epochs = 150 (90s per epoch)

INPUT SHAPE: (3, 64, 64) [channels first]
INPUT PRE-PROCESSING: Input to the network must be normalized by the maximum value of the input image channels before being fed to the trained network for online/offline classification. 
FRONTEND: Keras
BACKEND: Theano

GPU Used: NVIDIA GeForce GTX TITAN X (12207 MB of dedicated GPU memory) 
CUDA 8.0 (cuDNN 5.1)

Training Samples = 59184 (validation split = 0.1)
Test Samples = 6576

Test Accuracy = 94.13%


