# Machine-Learning
Face Recognition by using Linear Discriminant Analysis
-The main aim of this project is to learn about principal component analysis(PCA), Linear Discriminant analysis(LDA) and finding which one of them is giving better accuracy for face recognition.
-----------------------------------------------
Developed in : Python
-----------------------------------------------
Run:
-----------------------------------------------
-Open the given .ipynb file 'LDA_Face.ipynb' using Jupyter Notebook.Add the input data folder to the directory where .ipynb file is located.Run the code cell by cell to print the output images.
---------------------------------------------
Required packages:
------------------------------------------------
-opencv-python  -  For reading the images 
-numpy 	       -  For easy computations
-matplotlib       -  For displaying the graphs
-math            -  For mathematical computations
-----------------------------------------------
Input images:
-All input images are stored in a file named 'face_data' which contains face images of 40 persons and 10 images/person.
- More information about resources of input taken is given in readme file of face_data folder.
---------------------------------------------------------------
Data distribution :
-size of Data =  400 images
-size of Train Data =  240 images (60%)
-size of Test Data =  160 images (40%)
-From every person folder I am taking 6 images in trainData and remaining 4 images in testData and I am storing classlevel (Here person number) of every image in trainClass and testClass.

Steps:
-Convert the read input data to np.array to do calculations easily.
-Calculate mean for each class and subtract mean from each face image which gives mean zero face data.
- A function to find euclidean distance which we will use later.
Function for PCA:
- We will find covariance matrix of the zero face data.
- We will find eigenvalues and eigen vectors of this covariance matrix.
- To choose best directions we will sort the eigenvalues in the descending order and decide a k value, which represents the number of selected eigenvectors to extract k directions. On the basis of k value we can generate the Feature vector.
- project the each mean aligned face to the generated feature vector to get eigen faces.
-For generating signature of each face, we project each mean aligned face to the eigenfaces obtained.
Finding accuaracy of PCA:
- We will select K eigen faces and corresponding signatures of train images.
- We will find the signatures for all test images by projecting mean zero face data (test images) to eigenfaces then we will get the projected test face (test_samples).
-Now we will find the class level of every test image by calculating euclidean distance  from a test image to all train images and counting how many images are predicted correctly.
- Note accuracy at different k values.
LDA:
-In LDA,If the sample size is less than the dimension it will leads to singularity in within class matrix, and we cannot calculate the inverse of this. This problem is called the small sample size problem (SSS). For avoiding this problem we have to first use the PCA  to reduce the dimension and then we can use the LDA on the projected faces of PCA.
- I have applied PCA and selected best 240 features in 10302 features. Data reduced from 240*10302 to 240*240.
- Calculated the within class scatter matrix (SW)  and between class scatter matrix (SB).
- We will find the criterion function and eigenvalues and eigen vectors of criterion function.
Finding accuaracy of LDA:
- We will select best m principal components based on eigen values.
- Generate fisher faces (FF) by projecting the projected faces (training data) by the matrix obtained in previous step.
- Generate projected fisher faces(PFT) for test images too.
- Similarly as we did in PCA, now we will find the class level of every test image by calculating euclidean distance  from a test image to all train images and counting how many images are predicted correctly.
- Note accuracy at different m values.
--------------------------------------
End Result:
--------------------------------------
- Plot the graph for obtained accuracies at different k and m values.
- My model gives best performance at K = 106 with accuracy 90% for PCA
- My model gives best performance at M =  67 with accuracy 76.25% for LDA
-I have observed that PCA suits better for face recognition than LDA
