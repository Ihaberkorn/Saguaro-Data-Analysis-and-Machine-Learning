# Saguaro Data Analysis and Machine Learning (in progress)
In this project, 30 images of saguaros were sampled each year in the month of May between 2016 and 2026 to determine if there is a significant difference between the means of the amount of buds for each year. The month of May was chosen because it is the peak flowering month for saguaros. In each image, the amount of buds and stems were marked and counted in order to graph and analyze the data. The stems were marked as well to determine the spread of buds over each saguaro. After this analysis, I used the markings I did to train two machine learning models to detect buds and stems in images, allowing me to increase the sample size and get more accurate results. 
## Data Collection
To get the data needed for this project, information on saguaros in May was downloaded from [iNaturalist](https://www.inaturalist.org/) as a csv file: [observations-746071.csv](observations-746071.csv). This data was then put into a pandas dataframe and graphed by the counts of saguaros each year to determine how many years should be sampled from. After deciding 2026-2016 was the optimal range, 30 saguaros were randomly sampled from each of those years and their images were downloaded into separate folders. This can all be seen in [Saguaro_images.ipynb](Saguaro_images.ipynb). 
## Marking Images
To mark the images, the software [LabelImg](https://github.com/HumanSignal/labelImg) was used to draw boxes around each bud and stem (stems in progress as of 06/18/26). This was done in the YOLO format which saves the coordinates of each box in a text file that can then be used to train a machine learning program. Here is an example of what a labeled saguaro looks like in this software:

<p align="center">
<img width="307" height="432" alt="image" src="https://github.com/user-attachments/assets/8717f07c-f0cf-43af-9cb5-275923f9ab26" />
</p>

The larger boxes being the stems and the smaller boxes being the buds. As this was done this, the amount of buds and stems were logged in separate excel spreadsheets which were later used to analyze the data: [saguaro-bud-stem-per-year.csv](saguaro-bud-stem-per-year.csv). However, due to the randomness of the images, many of the images were difficult to correctly mark, likely causing inaccuracy in the results. For example: 

<p align="center">
<img width="1097" height="450" alt="image" src="https://github.com/user-attachments/assets/290ec97d-0bc6-4911-b066-24ce38a4fb32" />
</p>

Many images, such as the one above, were blurry and taken far away from the saguaros. This made it so that, even if there were buds on the saguaros, it was impossible to actually see or mark them in the photo, consequently marking more stems than buds. 
## Analyzing Bud Data
To analyze and graph the data, the [buds excel spreadsheet]('Saguaro Bud Counts - Sheet1.csv') was put into a pandas dataframe. First, the data was graphed, looking at the average buds per year as well as the standard error for each year: 

<p align="center">
<img width="562" height="455" alt="download" src="https://github.com/user-attachments/assets/c491a459-0935-4a28-92c1-db119a81bd79" />
</p>

The data had fairly high standard errors with fairly different means and a seemingly significant decrease of buds in 2022. Initially, an anova test seemed to be the best option to use on the data but after testing for normality and homogeneity of variances, it was clear an anova test would not be valid and a non parametric test must be used. The best option was the kruskal wallis test which gave me a p-value of 0.0004, showing that there is a significant difference in at least some of the years. After this, a dunns test was done on the data which only showed a significant difference between the years 2022 and 2016 with a p-value of 0.001 and the years 2022 and 2020 with a p-value of 0.002. This illustrates that, overall, there was not a significant difference between the means of buds each year. This can be seen in [saguaro_bud_counts.ipynb](saguaro_bud_counts.ipynb).

The reason that a significant difference was not seen between most of the years is likely due to the bias created from the blurry photos mentioned before. The amount of buds each year in these photos could not be correctly counted due to these photos. This is why it is important to also mark and count the number of stems each year so that the amount of buds can be controlled to the amount of stems in each image. 
## Analyzing Stem Data With Bud Data
To analyze the stem data, the stems excel spreadsheet was also put into a pandas dataframe where the data was graphed by year. 

<p align="center">
    
</p>
## Machine Learning
In progress as of 06/26/26
