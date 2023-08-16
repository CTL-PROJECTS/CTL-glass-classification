General information about the CTL course available at https://ctl.polyphys.mat.ethz.ch/

# :wave: PROJECT glass classification

Within this project we try to apply a classification method on real materials science data provided by the [UCI machine learning repository](http://archive.ics.uci.edu/ml/index.php). One of the available datasets was motivated by criminological investigation. It deals with the study of classification of types of glass. At the scene of the crime, the glass left can be used as evidence, if it is correctly identified! The training data (file: glass.data) is available for download within the [Data Folder](http://archive.ics.uci.edu/ml/datasets/Glass+Identification). The file glass.data contains a comma-separated matrix with N rows and 11 columns. Each of the N rows carries information about a single successful detection of a type of glass. While columns 2-10 are the measured attributes, (integer-valued) column 11 encodes the glass type (1,2,..,7) as follows:  

1. Id number: 1 to 214
2. RI: refractive index
3. Na: Sodium (unit measurement: weight percent in corresponding oxide, as are attributes 4-10)
4. Mg: Magnesium
5. Al: Aluminum
6. Si: Silicon
7. K: Potassium
8. Ca: Calcium
9. Ba: Barium
10. Fe: Iron
11. Type of glass: (class attribute)
-- 1 building_windows_float_processed
-- 2 building_windows_non_float_processed
-- 3 vehicle_windows_float_processed
-- 4 vehicle_windows_non_float_processed (none in this database)
-- 5 containers
-- 6 tableware
-- 7 headlamps

Starting from this 'training' set of N different measurements, this module returns the best estimate for the glass type of a 'test' glass for which the 9 attributes have been determined. The module can also be called with more than a one test dataset, a set of datasets, and then returns the set of recognized types. The goal is to correctly and quickly identify glass types from test attributes. This module may make use of existing libraries such as tensorflow (python) or fitensemble (matlab). 

This ascii file is required to run the module:

1. glass.data



The structure of your final code could be as follows, so that it can be used from both the command line (the command line argument is then the filename of the test data) or from within python code. 

    ...
    def load_training_data():
    ...

    N,X,y = load_training_data()
    
    if len(sys.argv)-1==1:
        y_result = recognition(str(sys.argv[1]))
    else:
        T = 5
        y_selected = create_test_data(N,X,y,T)
        y_result = recognition('X-test.txt')
        # task: compare y_selected with y_result 
    
## def load_training_data() 

1. read glass.data into an array DATA (see [here](https://github.com/mkmat/ETH-Computational-Thinking-Labs#language) for information on how to read and save arrays from file) 
2. Save columns 2 to 10 of the array DATA in array X 
3. Save column 11 of the array DATA in array y
4. Save X in train-X.txt
5. Save y in train-y.txt
4. Denote with N the number of rows of DATA
5. Return N,X,y

## def create_test_data(N,X,y,T)

1. load the training data
2. randomly select T < N rows
3. Write the selected rows of X into a file test-X.txt
4. Return test_y (the selected rows of y)

## def recognition(Xtestfile)

1. load_training_data
2. read the content of the file Xtestfile (call it Xtest) and determine its number of rows (T).
3. For each of the T rows of Xtest, suggest a glass type (an integer), and save this array of integers (denoted as y_result) in a file test-y-test.dat. 
3. Return y_result

## task

Calculate and report the difference between y_selected and y_result. This self test is also possible if the test data was generated using the training data (as done in this project). We may test your code using test data that is not contained in the training data.
      
## Hints

If you want to use [tensorflow](https://www.tensorflow.org/) to solve this problem, note that tensorflow vs2 or higher may be required to run in python 3.8 or higher. To still use tensorflow compatible with python 3.7, say, you can create a new conda environment for python 3.7 and use it in vscode as described [in the conda section of our CTL-README.md](https://github.com/mkmat/ETH-Computational-Thinking-Labs/blob/main/README.md#conda). 

## Further ..

The software you have developed here can be applied to [other data sets](http://archive.ics.uci.edu/ml/index.php) basically without change. You can also generate your own dataset, e.g., from a set of images, if you save the greyscale information (floating point number in [0,1]) of each pixel in a single row of your matrix X. 

