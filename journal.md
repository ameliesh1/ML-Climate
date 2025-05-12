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
      
The first thing we did was look for a dataset to fit our idea and we found a large one that was curated using images from the National Agriculture Imagery Program. Then, we decided generally how we wanted to split our dataset between testing, training, and validation (60%, 20%, 20%) and started our code. We decided to use GoogleColab because it’s easier to use than Github for our group project purposes, and we typically like to work simultaneously and talk to each other while coding. As we progress, we’ll be uploading our code along with our journal entries. We also have our dataset at hand; it is about 91000 images and we uploaded it to Google Drive with the following link: https://drive.google.com/drive/folders/1vYohRNltMjUj_0d8l8rHvczlkTph7RGX?usp=sharing.
      
So far in our code this weekend we did a basic setup of the base of our project by importing the necessary libraries and resizing the images. We wanted to make sure the images were all the same size so when we code matrices in the neural network later there wouldn’t be errors. Also we augmented the data to hopefully prevent overfitting so that if we were to test our model in a real-world environment it would still succeed because it is actively learning instead of memorizing the training data. After that we set up the dataset class by initializing it and having the model collect data by iterating through the image paths and assigning labels.

The other main goal that we had for this weekend was to try to handle class imbalance before it became a point of bias. We included a weighing system for the classes based on their frequency so that each chunk will have an even mix of categories regardless of how frequent they might occur in the total dataset. This will reduce the chances of our model learning biases when it is fully completed. Additionally we split the dataset into the three sections mentioned earlier with 60% for testing, 20% for training, and 20% for validation.

This coming week we are going to focus on coding our actual convolutional neural network (CNN) which will actually learn patterns by using different factors to predict when a wildfire is more likely to occur based on visual cues using multi-class classification.

**4/10**
We updated our code to begin training a neural network on the data, however we ran out of GPU while attempting the training. While we believe the training process is working, it is very slow due to the vast amount of data that we need to process. We are now splitting the dataset to cut down on computation time, and hope to be able to run our project just using CPU.

**4/18**
We will spend the weekend updating our code and have the updates in by Sunday evening, we plan on getting the ML to run and having basic statistics on the success of our project.

**Week of 4/13**
The last week and a half we’ve been working on our code mainly to get the loss to work correctly. Then, it was functioning correctly, however our dataset was so large that the GPU usage would reach its limit. So we decided to solve that by adding code to split our dataset in half in order to optimize the usage of our GPU. In doing so we made sure that the classifications and images stayed balanced as well. That solved our initial problem, but now we have an additional problem where our last batch never finishes and the program just gets stuck. We’re not sure exactly why it’s not working properly as of yet, but the next step is to modify the code to drop the last batch so the rest of the program runs and we can get the rest of our results and create some visuals in order to show our data. Additionally, we are running another code based on CPU, just to be able to compare the results and potentially the energy impact as well. So far, as expected, it takes much longer for the CPU to run.

**Week of 4/20**
Over the past week we’ve made significant progress in finishing our project by making our code a lot more efficient, enabling us to save a lot of GPU memory, solving our largest issue. To help with this we used mixed precision training, reduced batch sizes, and gradient accumulation over multiple iterations before updating weights in order to simulate larger batches. Making these changes in our code allowed us to significantly lower our memory usage and runtime of our code without sacrificing the accuracy of our results. Before, we had to split our dataset in half so it could fully run properly, yet with our new model we are able to train it on the full dataset without any issues. We also modified our code by including additional augmentation including rotations, flips, and zooms so that we could artificially present our model with more difficult options, so that it would perform better in the long run. We also made sure the loss function was weighed so that the model paid extra attention to misclassifications in more underrepresented classes in hopes that it would help it learn to make less errors. Both of these changes were made so the overall accuracy of each risk class would increase, and the results we have been seeing have been promising. Another adjustment we made was reducing our original learning rate because we were occasionally experiencing some losses because of not a number values and changing this helped the model’s training become more stable. As of right now to completely run our code on 10 epochs, it takes an average of 2 hours and 30 minutes, whereas before it took about three hours to run one epoch on half the dataset. We also completed the project presentation that is to be shown in class over the next two weeks. Our next steps will be to try to raise our training to be on 15 or 20 epochs, and to test different versions of running the code to see if there are changes in accuracy. A couple of tests could possibly include running on CPU versus GPU, running on half the dataset versus the full dataset, and calculating the energy consumption for these and comparing them. We are also going to begin to dig deeper into the writing of our research paper, but overall our project is looking pretty promising.

**Week of 5/4**
Switched from working on Google Colab to running on local GPU; Worked on paper

**Week of 5/4**
Spent the entire week testing different combinations and trying to reduce runtime for our project. Tried different epoch numbers until our kernel would die. Also tried different learning rates and different layers
