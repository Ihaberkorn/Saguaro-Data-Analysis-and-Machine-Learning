# Saguaro Data Analysis and Machine Learning (in progress)
In this project, I randomly sampled 30 images of saguaros each year from the past 10 years and marked the amount of buds and stems on each. This was done in order to determine if there is a significant difference between the means of the amount of buds for each year. The stems were marked as well to determine the spread of buds over each saguaro. After this analysis, I used the markings I did to train two machine learning models to detect buds and stems in images, allowing me to increase the sample size and get more accurate results. 
## Data Collection
To get the data I needed for this project, I downloaded information on saguaros from [iNaturalist](https://www.inaturalist.org/) as a csv file: [observations-746071.csv](observations-746071.csv). I then put the data into a pandas dataframe and graphed the counts of saguaros each year to determine how many years I should sample from. After deciding 2026-2016 was the optimal range, I randomly sampled 30 saguaros from each of those years and downloaded each of them, putting them in separate folders. This can all be seen in [Saguaro_images.ipynb](Saguaro_images.ipynb). 
## Marking Images
To mark the images, I used the software [LabelImg](https://github.com/HumanSignal/labelImg) to draw boxes around each bud and stem (stems in progress as of 06/18/26). I chose to use the YOLO format which saves the coordinates of each box in a text file that can then be used to train a machine learning program. Here is an example of what a labeled saguaro looks like in this software:

<p align="center">
<img width="307" height="432" alt="image" src="https://github.com/user-attachments/assets/8717f07c-f0cf-43af-9cb5-275923f9ab26" />
</p>

The larger boxes being the stems and the smaller boxes being the buds. As I did this, I logged the amount of buds and stems in an excel spreadsheet which I later used to analyze the data: [saguaro-bud-stem-per-year.csv](saguaro-bud-stem-per-year.csv) (only buds are complete so far). 
## Analyzing Bud Data
To analyze and graph the data, I put my buds and stems excel spreadsheet into a pandas dataframe (currently only with buds). First, I graphed the data, looking at the average buds per year as well as the standard error for each year: 

<p align="center">
<img width="562" height="455" alt="download" src="https://github.com/user-attachments/assets/c491a459-0935-4a28-92c1-db119a81bd79" />
</p>

The data had fairly high standard errors with fairly different means and a seemingly significant decrease of buds in 2022. Initially, I wanted to an anova test on the data but after testing for normality and homogeneity of variances, it was clear an anova test would not be valid and I had to try a non parametric test. I chose the kruskal wallis test which gave me a p-value of 0.0004, showing that there is a significant difference in at least some of the years. I then did a dunns test on the data which only showed a significant difference between the years 2022 and 2016 with a p-value of 0.001 and the years 2022 and 2020 with a p-value of 0.002. This illustrates that, overall, there was not a significant difference between the means of buds each year. This can be seen in [saguaro_bud_counts.ipynb](saguaro_bud_counts.ipynb).
## Machine Learning
In progress as of 06/18/26
