2024/04/10 13:37
Status: #idea
Tags: [[Convolutional Neural Networks]]

# Convolutional Neural Networks Proof of Concept



*Import required libraries*

```python
import tensorflow as tf
from keras.preprocessing.image import ImageData Generator
```

*Training data preprocessing - Keras preprocessing library*

```python
training_datagen = ImageDataGenerator(rescale=1/255, shear_range=0.2,zoom_range=0.2, horizontal_flip=True)

training_set=training_datagen.flow_from_directory('dataset/training_set', target_size=(64,64), batch_size=32, class_mode='binary')

```

*Create your test datagen*

```python

%% we remove the preprocessing steps for test set because we only need to test the model %%

test_datagen = ImageDataGenerator(rescale=1/255)

test_set=training_datagen.flow_from_directory('dataset/test_set', target_size=(64,64), batch_size=32, class_mode='binary')
```


*Develop CNN model*

```python

cnn = tf.keras.models.Sequential()

%% one layer of conv and pooling %%
cnn.add(tf.keras.layers.Conv2D(filters=32, kernel_size=3, activation='relu', input_shape=[64,64,3]))
cnn.add(tf.keras.layers.MaxPool2D(pool_size=2, strides=2))

%% one layer of conv and pooling %%
cnn.add(tf.keras.layers.Conv2D(filters=32, kernel_size=3, activation='relu'))
cnn.add(tf.keras.layers.MaxPool2D(pool_size=2, strides=2))

%% flatten the layers %%
cnn.add(tf.keras.layers.Flatten())

%% add neurons %%
cnn.add(tf.keras.layers.Dense(units=128, activation='relu'))

%% final dense layers %%
cnn.add(tf.keras.layers.Dense(units=1, activation='sigmoid'))


%% compile network %%

cnn.compile(optimize='adam', loss='binary_crossentropy', metrics=['accuracy'])

%% pass training set and test set %%

cnn.fit(x=training_set, validation_data=test_set, epochs=25)



```

*save model to JSON*




---
# References
