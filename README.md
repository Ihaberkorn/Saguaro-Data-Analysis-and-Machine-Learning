# Saguaro Data Analysis and Machine Learning
In this project, I randomly sampled 30 images of saguaros each year from the past 10 years and marked the amount of buds and stems on each. This was done in order to determine if there is a significant difference between the means of the amount of buds for each year. The stems were marked as well to determine the spread of buds over each saguaro. After this analysis, I used the markings I did to train two machine learning models to detect buds and stems in images, allowing me to increase the sample size and get more accurate results. 
## Data Collection
To get the data I needed for this project, I downloaded information on saguaros from [iNaturalist](https://www.inaturalist.org/) as a csv file: [observations-74601.csv](observations-746071.csv). I then put the data into a pandas dataframe and graphed the counts of saguaros each year to determine how many years I should sample from. After deciding 2026-2016 was the optimal range, I randomly sampled 30 saguaros from each of those years and downloaded each of them, putting them in separate folders. This can all be seen in [Saguaro_images.ipynb](Saguaro_images.ipynb). 
## Marking Images
To mark the images, I used the software [LabelImg](https://github.com/HumanSignal/labelImg) to draw boxes around each bud and stem (stems in progress as of 06/18/26). I chose to use the YOLO format which saves the coordinates of each box in a text file that can then be used to train a machine learning program. As I did this, I logged the amount of buds and stems in an excel spreadsheet which I later used to analyze the data: [Saguaro Bud Counts - Sheet1.csv](
## Analyzing Data
## Machine Learning
In progress as of 06/18/26
