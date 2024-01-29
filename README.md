# Convolutional Neural Networks (RNNs) for a Time Series problem
In this repository to can find a deep learning problem solved. Target is to predict the number of bikes per hour rented in Washington D.C., given some info shuch as season of the year, if it is a working day, etc.

To achieve it, several neural networks models have been built, with different architectures, using Keras (Tensorflow in the background).

## Study of the data

### Correlation between numeric attributes
In the Figure you can see a diagonal correlation mattrix of the numeric attributes of the dataset.

![image](https://github.com/jorgerebe/RNNs-Bike-Sharing-Prediction/assets/48808378/1f2563d7-63d8-49c6-a2d1-4a3e77109879)


### Study of the variable to predict

In the Jupyter Notebook and in the pdf you can see a little study of the variable to predict (number of rented bikes, the variable 'cnt'), including measures of central tendency, variability and distribution, inlcuding some graphs and plots.

## Data Preprocessing

In the next Figure, you can see the data before processing the data, and in the next, you can see the data processed. After that, there are explanations about the steps taken to process the data.

No processed Data:
![image](https://github.com/jorgerebe/RNNs-Bike-Sharing-Prediction/assets/48808378/e37ee0d8-1ad7-4735-94a6-0b3480abb122)
Processed Data:
![image](https://github.com/jorgerebe/RNNs-Bike-Sharing-Prediction/assets/48808378/881ddc6c-4993-4810-98c1-41d206385ae4)


### Attribute Selection

Attributes 'instant', 'dteday', 'casual', 'registered', 'atemp', 'yr' and 'weekday' were removed. 

- 'instant' is just an id

- 'dteday' is not useful for our problem, it is just a date that could be used to look for info that has happened that could influence on the number of rented bikes.

- 'casual' and 'registered' summed are equal to 'cnt', the variable we want to predict.

- 'atemp' is the feeling temperature, so only 'temp' will be kept.

- 'yr' and 'weekday' are also removed due to its poor correlation with the variable to predict ('cnt')


### Categorical Values Treatment

Attribute 'season' and attribute 'weathersit' go through OneHotEncoder, so dimensionality is increased by 6 (4 possible values for each attribute, minus the original attributes).

### Train-Validation-Test Split

Once the data has ben processed, data is splitted in two sets: 2/3 for training, and 1/3 for test. When training, 20% of the training set will be used as validation set.

## Training the Models

### Hyperparameters selection

There are a lot of hyperparameters, whose value can be optimized. In this work optimum values have been searched for the following hyperparameters:

- Number of LSTM units
- Number of LSTM layers
- Learning Rate
- Dropout Rate

### Callbacks

Callbacks were used to prevent overfitting when training the model. In this work, EarlyStopping and ReduceLROnPlateau were used.

### Models Trained

Different RNNs models have been trained, such as LSTM with only 1 layer, LSTM with the window method, various LSTM layers, LSTM with memory, various layers of LSTM with memory and a basic one GRU layer.

You can see more details in the Jupyter Notebook,where you can see the results of the training and how the models were built and trained.


## Testing the Models

In the Table you can see the results of the previously trained models against the test set. More details on the Jupyter Notebook.

![image](https://github.com/jorgerebe/RNNs-Bike-Sharing-Prediction/assets/48808378/3b74d905-1b17-4926-b8a5-05f53be4d669)
