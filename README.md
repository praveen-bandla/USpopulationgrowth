# US Population Growth Rate at a County Level (1970-2020)

Population growth in the US over the course of 50 years visualized as a choropleth map for each year stitched into a `GIF`

----

### Objective

I am working towards building a model that categorizes each county based on its social and economical stability over the course of modern history. Understanding the population trends is the first step in achieving that long-term goal.

I wanted to work on my data visualization skills and ability to handle large data sets. A lot of my initial stabs at reading and storing the dataset failed due to simply being too computationally expensive. I was forced to find the most optimal solutions and was definitely a positive learning experience.

----

### Future Work
For this project, I intended to look at the population growth rate of a given county for a given year. In future work, I would explore the population trends at a race and gender level as well.
Moreover, I intend to look at similar data relating to school enrollment, family composition, and income inequality, amongst other trends.

----

### Contents

Gathering data - `County Population.ipynb` : Processing the input text file and turning into a usable dataframe
`popdelta.ipynb` : using the dataframe to create the visual

----

### Flow of Work
The data used was available on the [SEER](https://seer.cancer.gov/popdata/download.html) website in the form of a gz file. Once extracted, a text file was obtained that was then converted to a dataframe.\
The data was then cleaned and grouped to obtain the desired information: population for each year at the county level. Note that the states Alaska, Hawaii, and Puerto Rico were omitted to keep focus on the Contiguous United States (mainland). There are six counties that do not have data, but the data was whole otherwise.\
A choropleth map was chosen to present the data. I was seeking a contrast color, one where the difference between population increase and decrease could be highlighted with ease. Luckily, the CMRmap had the desired effect without the need for any modification to the palette and mapping. 
One instance of the graph was plotted to test and work on the design of the visual. After that, a loop was used to plot all 50 graphs to then be stitched together as a GIF with a time period of 1 second each.

All of the work was done on Python, split between Jupyter Notebook and Google Colab.

----

### Challenges
As alluded to earlier, the biggest challenge of the project was finding a relatively cheap way to extract the data as text into a dataframe. There were no commas to separate the column names, and instead indices values for where the splits occurred. For example, the following string translates to:
##### '1969AL01001991910000000159'
Year: 1969\
State: Alabama\
State Code: 01\
County Code: 01\
Registry: 99\
Race: White\
Origin: N/A\
Sex: Male\
Population: 159

[Source](https://seer.cancer.gov/popdata/popdic.html)

What I ended up using was Google Colab with the free standard GPUs, where things ran faster. There were also difficulties I encountered while trying to install the GeoPandas library locally (see below)

----

### Libraries

All libraries used are listed in the notebooks. I would like to make a note about using Geopandas:

I installed [GEOPANDAS](https://geopandas.org/en/stable/) through Google Colab. While initially working in a local Jupyter Notebook session on Windows, I had difficulties with its installation. I used [PIPWIN](https://pypi.org/project/pipwin/) instead of PIP and that worked! To work on this project - or install Geopandas - locally on Windows, I recommend running the following commands
```bash
pip install wheel
pip install pipwin

pipwin install numpy
pipwin install pandas
pipwin install shapely
pipwin install gdal
pipwin install fiona
pipwin install pyproj
pipwin install six
pipwin install rtree
pipwin install geopandas
```
[READ MORE](https://stackoverflow.com/questions/54734667/error-installing-geopandas-a-gdal-api-version-must-be-specified-in-anaconda)

