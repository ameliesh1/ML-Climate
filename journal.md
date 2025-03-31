Four Week Plan to Predict Flooding in Different Boroughs in NYC and the Potential Impact on its Residents

**Week 1- Data Gathering**
1. Collect spatial data
2. Collect temporal data
3. Clean Data-the different datasets will have different formats, missing values, and coordinate systems so it needs to be so that everything is cohesive
      a. Standardize Coordinates so everything is based on the same system
      b. Create composite risk indices so that social factors have measurable risk scores (weights)
      c. Incorporate climate change projections over the years into risk models

**Week 2**
1. Begin building machine model using CNNs to process spatial data to detect patterns
      a. Split dataset into Train/Testing (80 percent or 20 percent)
      b. Aim to be able to show SHAP values, feature importance, and partial dependence plots
2. Start to interpret models

**Week 3**
1. Finish building CNN model
2. Cost-benefit analysis of potential interventions
3. Figure out potential improvements/solutions (by metric)

**Week 4**
1. Clean up any code that needs it
2. Write academic paper
      a.Abstract, introduction, data, methods, results, discussion, conclusion/recommendations
3. Have presentation ready

**3/23-3/24**
-Found Spatial and Temporal Datasets and added to the github: Elevation of 5 boroughs, Future floodplains predictions by borough, High tide predictions by borough, Rainfall data

**3/25**
-Began cleaning data

**3/28-3/30**

We made a decision to pivot because our original idea was not working out due to a lack of publicly available data, despite our efforts to find multiple datasets, and we were not entirely sure whether we should approach the problem with transfer learning or find a way to extend the datasets via data augmentation. We therefore continued our search for projects which would have large datasets to work with, and we ultimately decided on an idea which is extremely relevant to current day global warming issues, especially regarding the recent January fires in the Los Angeles area. Our vision is to be able to create a machine learning model that can predict wildfire risk levels based on a dataset of images that are labelled with different risk classifications. The goal would be to create a model that can be utilized in current society to monitor different areas and allow for early detection and intervention in places where wildfires could occur.
      
The first thing we did was look for a dataset to fit our idea and we found a large one that was curated using images from the National Agriculture Imagery Program. Then, we decided generally how we wanted to split our dataset between testing, training, and validation (60%, 20%, 20%) and started our code. We decided to use GoogleColab because it’s easier to use than Github for our group project purposes, and we typically like to work simultaneously and talk to each other while coding. As we progress, we’ll be uploading our code along with our journal entries. We also have our dataset at hand, and we will be adding the link to it shortly. It is very large and we are still in the process of uploading it to Google Drive.
      
So far in our code this weekend we did a basic setup of the base of our project by importing the necessary libraries and resizing the images. We wanted to make sure the images were all the same size so when we code matrices in the neural network later there wouldn’t be errors. Also we augmented the data to hopefully prevent overfitting so that if we were to test our model in a real-world environment it would still succeed because it is actively learning instead of memorizing the training data. After that we set up the dataset class by initializing it and having the model collect data by iterating through the image paths and assigning labels.
The other main goal that we had for this weekend was to try to handle class imbalance before it became a point of bias. We included a weighing system for the classes based on their frequency so that each chunk will have an even mix of categories regardless of how frequent they might occur in the total dataset. This will reduce the chances of our model learning biases when it is fully completed. Additionally we split the dataset into the three sections mentioned earlier with 60% for testing, 20% for training, and 20% for validation.

This coming week we are going to focus on coding our actual convolutional neural network (CNN) which will actually learn patterns by using different factors to predict when a wildfire is more likely to occur based on visual cues using multi-class classification.
