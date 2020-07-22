# photo-mining-and-classification
The aim of the project is to create a classifier that manages to classify, with the best possible performance, images into three categories: buildings, sculptures, paintings.

## DATA
The dataset consists of 110 images belonging to the 'paintings' category, 102 to the 'sculptures' category and 103 to the 'buildings' category. The images that make up the dataset were obtained using the Flickr API: social media that allows members to share personal photographs. (code in:\FLICKR\download_images.py).

Some views on the information of the photos in the dataset are generated by thecode in: \FLICKR\download_images.py).

The dataset was then necessarily divided into two parts: "training set", containing 70% of the images of each category and "test set" which contains 30%. The training set is used by classifier models in the training phase, the test set, instead, in the performance evaluation phase.

## REPRESENTATION OF DATA
The data representation model used is the Bag of Visual Words (BOVW): construction of a "dictionary of visual words" useful for describing images. This dictionary is created by extracting local features from the images of the training set using Daisy Computation, which returns grids of descriptors extracted from the images in the form of three-dimensional tensors.
The “step” parameter of the daisy function indicates the distance between the descriptor sampling points; therefore determines the number of features extracted.
For the purposes of the project both classifiers will be trained using the representation of BOVW data with feature extraction using the parameter of the daisy function "step = 4" (more features will be extracted.
A clustering algorithm (K-Means) is then used on the extracted features to obtain a predetermined number of "visual words".
Once a "visual words" histogram has been created, which contains the number of occurrences of each visual word within each image, the TF-IDF (Term Frequency Inverse Document Frequency) normalization method is used. This process is important because the scale of the values ​​of each representation depends on the number of local features extracted from the image. The TF-IDF method gives a value of different importance to each word, eliminating too frequent words from the vocabulary that do not allow us to discriminate between images.

## ALGORITHMS
Three different classifier models were used:
1. KNN: Algorithm whereby each sample of the test set is represented in the same space as the features of the training set; the class to be assigned is decided considering the class to which the k elements of the closest training set belong, considering the one that appears several times in the set of k elements.
7 models with different K values ​​were trained: k [1,13] with odd k.
2. Multinomial logistic regression: Built using the one-vs-all paradigm, according to which, in this case, 3 logistic classifiers are trained and each of whom discriminates a given class from all the others.
3. Naive Bayes classifier: It uses Bayes' theorem, and is based on the fact that all the features are not related to each other (Naive Bayes Assumption). It calculates the probability of belonging to a class and the final decision is identified in the class that obtains the highest probability value.
