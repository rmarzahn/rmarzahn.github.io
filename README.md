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
| Labor market <br> effects | -                           | -                           | Relative unemployment <br> numbers (without industry) | -                |
| Industry <br> effects     | Absolute numbers <br> per industry | Absolute increase of <br> unemployment in relation <br> to industry size | - | -                |
| Government <br> measures  | -                           | Combination of unemployment <br> increase per industry and <br> government measures | - | -            |
| Regional <br> differences | -                           | -                           | Relative unemployment <br> increase per industry | Summed monthly cases <br> per federal state |

Having prepared the datasets separately, they were combined to an integrated database containing different attribute types:
- Nominal data: Industry, Region
- Metric data: Datetime, COVID-19 Cases, Unemployment Numbers (absolute + relative) 


## Visual encoding / interaction design
Defining a suitable visualization, an explanatory data analysis and considerations about different visualization types were processed. To answer the question concerning the labour market effects, a map was considered as the best choice. Due to the geographic approach, the federal perspective can be included easier compared to, for instance, multiple line charts. The colour of a region shows how much it has been affected by unemployment change. To also include a time-related view and details on the development of unemployment, sparklines next to the map provide information of the development over time. 

It becomes clear that there are large regional differences. To find an explanation for these differences, the second visualisation investigates industries in Germany on a national level from an industrial perspective. It shows the size of an industry measured by the amount of jobs subject to social insurance contributions. Due to the number of industries and against the background of higher clarity, a horizontal bar chart was chosen over a vertical one. This visualization motivates to have a closer look at the increase in unemployment per industry over time in relation to the industry size. In order to interpret the different trends, the user can choose between different government measures which are displayed as a time interval in the line chart. Also, an industry can be chosen by clicking on the bar or the line in the diagram which makes it easier to look at one industry in particular. As a consequence the two charts are combined by interactive selection and conditioning. That is why a multiple line chart was a suitable solution weighted against small multiples. This visualisation makes clear that, in addition to regional differences, the sectors are also affected to varying degrees.

The third visualisation combines the findings of the first two and shows the development of unemployment per region and per sector. Regarding regional differences, a map and a heatmap visualization was weighed against each other. For the given purpose, a heatmap gave a better overview perspective by giving the user the possibility to see all regions, industries, and the average increase in unemployment per industry in one visualization. The darker a field in the heat map is, the higher was the increase in unemployment. To provide a possible explanation, again an interactive tool is included. The user can click on the different fields of the heat map in order to see the development of unemployment per region and industry over time as a simple line chart. Against the background of the influence of the COVID-19 pandemic, a bar chart showing the federal COVID-19 cases is overlaid to give an idea of how these case numbers have affected the increase in unemployment.

Concerning the choice of colors, a category wise scale was chosen over a continuous scale. By this means, a clearer and more significant statement can be shown and it is easier to see and distinguish differences. The color scheme was chosen because it starts at a defined zero and gets more intense as unemployment increases. Therefore, the viewer intuitively catches an eye on industries and regions that were affected most. Moreover, the bluish color is decent and neutral and, therefore, not distracting or unpleasant to look at.


## Algorithm design
To make sure that the computational complexity is appropriately, redundant and not required data was deleted in the data preparation process. Additionally, the extent of data was reduced by aggregating daily to monthly data and filtering for the regarded time frame of the COVID-19 pandemic.

Nonetheless, the practical implementation shows minor bottlenecks. To classify the values for the color scale, a loop over the whole data frame was used. With regard to the little amount of rows this was a reasonable solution but would cause performance problems with a greater amount of rows. This problem could easily be fixed by working with the pandas .loc function instead of a loop. Furthermore, the use of GeoJSON data to display a map can cause negative effects. Addressing this downside, there is a trade-off between the quality of GeoJSON data and performance time which needs to be considered while implementing.


## Possible Improvements and Limitations
Regarding a content wise perspective, the static integration of the data could be changed to a dynamic integration. Thereby, the visualizations could be updated automatically over time. Besides that, the interactive visualizations could be equipped with a multi selection instead of single selection to enable the possibilities for direct comparisons between industries and regions.
Considering a technical perspective, the web application itself is responsive and usable from diverse devices. The visualizations, however, are implemented statically, which causes displaying problems. Additionally, some browsers, e.g. Safari, have problems displaying the visualizations in the correct layout.
Adding a process wise perspective, a faster determination of the topic and better focus on the bigger picture instead of getting lost in minor details could support a more fluent project process. 


## References
*Bundesagentur für Arbeit (2020a)*: Arbeitsmarkt nach Branchen - Deutschland (Monatszahlen), online available at: <br> https://statistik.arbeitsagentur.de/SiteGlobals/Forms/Suche/Einzelheftsuche_Formular.html?nn=20898&topic_f=tabelle-arbeitsmarkt-branchen [final call: 19th October 2020].

*Bundesagentur für Arbeit (2020b)*: Auswirkungen der Coronakrise auf den Arbeitsmarkt - Deutschland, West/Ost, Länder, Kreise und Agenturen für Arbeit (Monatszahlen), online available at: <br> https://statistik.arbeitsagentur.de/SiteGlobals/Forms/Suche/Einzelheftsuche_Formular.html?nn=15024&r_f=ur_Deutschland&topic_f=corona-datenset-corona [final call: 16th October 2020].

*Bundesagentur für Arbeit (2020c)*: Eckwerte Arbeitsmarkt, online available at: <br> https://statistik.arbeitsagentur.de/DE/Navigation/Statistiken/Interaktive-Angebote/Dashboard-Eckwerte-Arbeitsmarkt/Dashboard-Eckwerte-Arbeitsmarkt-Nav.html [final call: 21th October 2020].

*IamExpat (2020)*: Corona crisis: Greatest decline in German workforce since reunification, online available at:<br> https://www.iamexpat.de/career/employment-news/corona-crisis-greatest-decline-german-workforce-reunification [final call: 12th October 2020].

*Munzner, T. (2009)*: A Neasted Model for Visualization Design and Validation, in: IEEE Transactions on Visualization and Computer Graphics 15(6), pp. 921-928.

*Nationale Plattform für geographische Daten (NPGEO) (2020)*: RKI Covid19, online available at: <br> https://npgeo-corona-npgeo-de.hub.arcgis.com/datasets/dd4580c810204019a7b8eb3e0b329dd6_0/data [final call: 16th October 2020].
