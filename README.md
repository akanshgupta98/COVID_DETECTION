# COVID_DETECTION
In this project binary classification and multi-class classification has been performed for detecting covid and normal x_ray scans. 
TOOLS/Libraries USED: Google Colab, Pytorch, Numpy, Matplotlib.

### Dataset Description
The dataset used for this purpose is: COVID-19 Radiography Database
from kaggle. LINK: https://www.kaggle.com/tawsifurrahman/covid19-radiography-database.
It contains 3 types of images. 
1. COVID
2. PNUEMONIA
3. NORMAL

The samples for COVID are very less as compared to other classes and when the experiment was performed with less data, it could not detect differences between COVID
and other classes. To overcome that data augmentation has been performed.

### Data Augmentation
The dataset contains only 300 images of COVID X_ray scans and other 2 classes contain around 1300 images. So this is a problem of highly imbalanced dataset.
To overcome this, data augmentation is done. First the data is randomly split into train and test sets. The training images contain 175 images of COVID. 
3 types of operations have been performed. 
1. The first set of data is horizontally flipped with a probablity of 50%. i.e. an image has 50% chance of being horizontally flipped. After this, Random Rotation of
the image is performed with 150 degrees.
2. The second set of data is vertically flipped with a probablity of 50%. i.e. an image has 50% chance of being vertically flipped. After this, Random Rotation of
the image is performed with 40 degrees.

Till now, 175 images have been augmented 2 times, resulting in around 300 images. Now all this is clubbed (augmented data 2 sets + original data) and it contains 522
images. Now Final transformation is performed.

3. The third set is horizontally and vertically flipped with probability of 70% and 30% respectively. After this random parts of images are erased with a probablility
of 30% and scaled accordingly so that the part erased is not very big else it would create a trouble and would make the learning difficult.

After all this, now the classes for training were balanced.

### Training

CNN architecture was created after several experiments, and dropout layers were also included to avoid overfitting problem. CNN architecture with its dimensions can 
be seen in code with comments. It was very easy to differentiate between normal and covid and after appropriate CNN architecture, it was able to learn the differences
and hence resulted in great Accuracy. TRAINING: 99% TESTING: 95 %. The detection with all 3 classes, NORMAL,PNEUMONIA,COVID and till now only 80% accuracy is obtained
for testing due to overfitting, hence working on it to fix and make it work. 

In this project, the main learning was to deal with imbalanced data, and hence perform augmentation. 
