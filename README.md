# Fire-Detection Project Overview
This fire detection is project part our final assignment in the Digital Image Processing course. We are supposed to create a system to detect fires in images. We are allowed to implement various feature extraction and machine learning algorithms, but the only constraint is that deep learning models are not allowed. The code implementation should then be reported in IEEE format. 

# Running The Notebook
You may import and run this notebook in any environment you like, just be sure to change directories of the dataset files and install all the necessary depedencies. 

# Meet The Team:
The team for this project consisted of 4 people: 
- Salman Faiz Hidayat
- Salwa Mumtaazah Darmanastri
- Bambang Abhinawa Pinakasakti
- Rama Andhika Pratama

# The Dataset
The dataset that was used for this project is from the Bilkent University's VisiFire dataset, which is available here: http://signal.ee.bilkent.edu.tr/VisiFire/Demo/SampleClips.html

# Proposed Method 
## Data Labeling
We proposed a multiclass prediction using the XGBoost algorithm. The labels for each class corresponds to the folders in the dataset: 
- AccidentsInaTunnel: Videos displaying a car accident in a tunnel, which makes smokes that may not be fire (labeled 0).
- FireClips: Videos of fire with varying sizes, ranging from barbeque fire to forest fire (labeled 1).
- SmokeFar: Smoke videos recorded from far away (labeled 2).
- SmokeClips: Videos of smoke (labeled 3). 

## The Pipeline
The pipeline goes as follows. Each step is explained in the pdf report:  
1. Enhancement: Applying Gaussian blur and sharpening kernel.
2. Segmentation: Segmenting the fire using adaptive Otsu thresholding.
3. Applying Convex hull to capture the area of fire in the frame.
4. Blob detection to detect the key points in each frame of the video clip.
5. Extracting features such as LBP, applying Gabor filter, optical flow, HSV color features, and color moments.
6. Combining all features into a vector.
One important thing to note is that 

# Result
One discovery that we accidentally made was the fact that the HSV feature was better of omitted than included. Our proposed model without the HSV feature yielded an accuracy score of 0.90, compared to 0.85 when included. We suspect that the performance may have deteriorated because there were too much features to process. 

# Potential Improvements
Feature extraction process could have been simpler to reduce computational overhead and time. Furthermore, the classification report showed that there were some categories with no support vectors. This can potentially be solved by providing more video clips for that category. And regarding the preprocessing steps, it could be better adjusted, especially the fact that there were a lot of parameters to play around with. Lastly, the model could have more practical values if it makes a binary prediction instead (fire or not fire).

