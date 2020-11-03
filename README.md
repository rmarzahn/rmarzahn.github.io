# Documentation "Unemployment in Germany during COVID-19"

The present documentation explains the concept and design choices for the data visualization project “Unemployment in Germany during COVID-19”. The objective of this project is to give a summary on the development of unemployment in Germany during the global COVID-19 pandemic from diverse perspectives.

Bringing comprehensive information into account, mainly two data sources were used for the project. On the one hand, data sets from the Bundesagentur für Arbeit *(Bundesagentur für Arbeit 2020a, Bundesagentur für Arbeit 2020b)* formed the basis to analyze the change in unemployment, on the other hand, a data set from the Robert-Koch Institut *(NPGEO 2020)* was used to reference this change to the COVID-19 cases.
The visualization project was implemented with Python 3.8.3 using mainly the pandas, altair and json library. The outcome is a data storytelling inspired web application, which can be used with Microsoft Edge, Mozilla Firefox, and Google Chrome.

To have a differentiated observation on the project, the following elaboration applies the **‘Nested Model for Visualization Design and Validation’ by Tamara Munzner** *(Munzner 2009)*. The project represents a problem-driven work, which aims to answer their questions defined below by effectively using existing visual encoding and interaction idioms.


## Domain problem characterization
With the beginning of the corona pandemic in Germany, there was the strongest increase in unemployment between two quarters since reunification *(IamExpat 2020)*. This project investigates the effects of the corona pandemic on unemployment in Germany from a national, federal and industrial view. Thus, the visualizations are addressed to people that are interested in the economic effects of COVID-19 on unemployment. More specifically, this could be employees of a specific industry or region. The visualisations answer the following questions regarding labor market effects, government measures, industry effects, and regional differences:

1. At which point of the pandemic can be seen effects on the labour market?
2. How did government measures regarding COVID-19 influence unemployment?
3. Which industry is affected most by COVID-19 regarding unemployment?
4. Is there a regional difference regarding the development of unemployment during COVID-19?

For this purpose, a secondary research approach was chosen. Various data sources from the Agentur für Arbeit were used which contain the absolute and relative increase in unemployment compared to the same month of the previous year both, per region and per industry. The data covers a time interval from January 2019 to September 2020 on a monthly basis. To be able to analyze geographic differences, not only national data for Germany but regional data for each federal state of Germany was taken into account *(Bundesagentur für Arbeit 2020b)*. Against the background of being able to rank the unemployment change in relation to the size, data regarding the sizes of different industries in Germany was added *(Bundesagentur für Arbeit 2020a)*. In context of the COVID-19 pandemic, daily data from the Robert-Koch Institut on a federal level was used to enable the analysis of possible cause-effect relations between the pandemic and change in unemployment from January 2020 to October 2020 *(NPGEO 2020)*. These data sets may all be used for non-commercial purposes *(Bundesagentur für Arbeit 2020a, Bundesagentur für Arbeit 2020b, NPGEO 2020)*.

|             | Job market industries [1]   | Unemployment Germany [2]    | Unemployment region [3]     | COVID-19 Cases RKI [4]                     |
| ----------- | --------------------------- | --------------------------- | --------------------------- | ------------------------------------------ |
| Topic       | Industry size               | Unemployment                | Unemployment                | COVID-19                                   |
| Location    | Germany                     | Germany                     |  Germany - Federal          | Germany - Federal                          |
| Time frame <br> Interval | 01/2020 - 07/2020 <br> (monthly) | 01/2019 - 09/2020 <br> (monthly) | 03/2020 - 09/2020 <br> (monthly) | 01/2020 - 10/2020 <br> (daily) |


## Data / task abstraction
Abstracting the presented ideas, this project analyzes the development and change of an economic indicator over time compared to the development of the prior year. Additionally, geographic differences as well as external measures are included. Overall, the project aims to visualize possible cause-effect relationships between the development of an economic indicator under the influence of external factors. 

To support the tasks, the selected data sets had to be prepared. To compare them on a time-related level, the daily COVID-19 data was aggregated to monthly data and all datasets were filtered for the relevant months of the pandemic from March to September. Furthermore, to guarantee correct and efficient industry-related comparisons, existing industries were clustered to an amount of ten to reduce complexity and enable comparability. Missing values were estimated with further data concerning the regional unemployment numbers per industry from the Bundesagentur für Arbeit *(Bundesagentur für Arbeit 2020c)*.

|             | Job market industries [1]   | Unemployment Germany [2]    | Unemployment region [3]     | COVID-19 Cases RKI [4]                     |
| ----------- | --------------------------- | --------------------------- | --------------------------- | ------------------------------------------ |
| Topic       | Industry size               | Unemployment                | Unemployment                | COVID-19                                   |
| Editing     | Industry clustering         | Industry clustering         | Estimation of missing values <br> Industry clustering| Summarized monthly|
| Actions     | Merged with [2]             | Merged with [1]             | Merged with [4]             | Merged with [3]                            |

To determine which data type supports a visual representation of the outlined questions, the levels of action were defined. Concerning high-level choices, existing data is used to get insights about the change of unemployment over time and regional differences in unemployment. Furthermore, additional data is calculated to get insights about the change in unemployment in relation to the industry size. Regarding low-level choices, the project targets to find correlations between the change in unemployment and COVID-19 cases as well as taken government measures from a national, federal and industrial perspective.

The chosen data sets thereby contribute to different defined questions:
|                           | Job market industries [1]   | Unemployment Germany [2]    | Unemployment region [3]     | COVID-19 Cases RKI [4]                     |
| ------------------------- | --------------------------- | --------------------------- | --------------------------- | ------------------------------------------ |
| Labor market <br> effects | -                           | -                           | Relative unemployment numbers (without industry) | -                |
| Industry <br> effects     | Absolute numbers <br> per industry | Absolute increase of <br> unemployment in relation <br> to industry size | - | -                |
| Gov.       <br> measures  | -                           | Combination of unemployment <br> increase per industry and <br> government measures | - | -            |
| Regional <br> differences | -                           | -                           | Relative unemployment increase <br> per industry | Summed monthly cases <br> per federal state |


