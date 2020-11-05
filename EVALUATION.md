# Evaluation Group 4 - 'Influence of COVID-19 on Flight Traffic'

The present evaluation classifies the concept and design choices for the data visualization project “Influence of COVID-19 on Flight Traffic” *(Péjac 2020)*. 

The objective of this project is to give a data exploration story on how the COVID-19 pandemic affected global flights. It aims for an unbiased exploration of flight volume during the pandemic and is using interactive parts to give an idea of global interconnectedness. For this the target audience is defined as people interested in the influence of COVID-19 on flight traffic, for example people working in air traffic. The project mainly tries to answer two different questions *(Péjac et al. 2020)*:
- How did the CoVid19 pandemic influence global flight traffic?
- Did the flight traffic in some regions of the world react differently?

## User Story
Using the Cognitive Walkthrough method the following work describes how a person from the target audience can use the visualizations and if the given questions can be answered. 

The initial impression of the web application is very clean and minimalistic. However a short introduction giving some contextual information about what the provided visualizations are going to address is missing. 

The first visualization, a layered line and bar chart, gives insights about how the number of flights developed in relation to the number of COVID-19 cases between January 2019 and August 2020. Therefore it is possible to evaluate if a temporal shift or synchronous reaction of the numbers is apparent. The visualization provides a good overview and enables to analyze a possible connection. Additionally interaction with the second visualization is implemented to have a closer look on a specific time interval. However the amount of lines, similar colors, missing declaration of interaction and which type of the charts shows the number of flights and COVID-19 cases cause confusion. In addition it is not clear if the first part of the graph provides any information since the shown months have no relevance to the research question.    

The following visualization shows the connectedness between different regions by giving insights about the amount of flights between them over time. The heatmap visualizes it in a compact, clear way and is breaking down complexity with provided tooltips for detailed information. The point which does not become clear is the meaning of white fields.  

The third visualization again provides information about the connectedness of different regions. This time a geographic approach was chosen. By investigating the question with a map, an even better overview and additional information about the geographical location of viewed regions is given. But there is no legend, which explains the meaning of the points and the size of the edges. Without geographical knowledge and missing tooltips or labeling, further uncertainty could be caused. 


## Validation
To evaluate the visualization valid the following part addresses threats by applying the **‘Nested Model for Visualization Design and Validation’ by Tamara Munzner** *(Munzner 2009)*. 

The COVID-19 pandemic and related travel restrictions had a strong impact on the flight traffic. Experts assume that a lot of airlines go bankrupt *(Statista 2020)*. Therefore, this project investigates the flight traffic changes during this time. Different visualizations help to find out whether there are regional differences regarding the flight mobility behaviour over time.

To gain a better understanding of the domain, data regarding the COVID-19 cases per region and the number of flights per region were used. The data allows the user to look at the number of cases and flights in a certain region as well as the number of flights between two regions. 

Validating the visual encoding and interaction regarding the first interactive visualization, the user can highlight the region he is interested in by clicking on the legend next to the chart. Furthermore, it is possible to draw an interval within the chart to look at a specific time frame which is linked to the second chart. However, there are no hints that these interactions exist. Additionally the choice of colours has not been aligned with the colour of the bars. As a result, the colours of some lines and the bars are very similar and are therefore difficult to distinguish. Also, by showing the absolute flight numbers the user has to assess the change in flight traffic due to COVID-19 to answer the research question himself.

Regarding the visual encoding of the second visualization, the darker a field in the heatmap is, the more flight traffic was between the two regions. Tooltips allow the user to get the exact number of flights. However, the continuous legend makes it difficult to distinguish some colours in the heatmap. As in the first chart it might be helpful to show the relative change in flight traffic instead of absolute numbers to investigate the influence of the COVID-19 pandemic. 

Evaluating the interaction of last visualization, the user can draw an interval but there is no apparent benefit. In addition, some lines, marking the amount of flights, are barely visible as they are too thin. The title of the chart does not clearly explain the content of the visualization and a legend declaring the meaning of points and edges is missing.


## Improvements
Based on the highlighted issues the following part outlines possible improvements for the visualizations.

As mentioned above, it would be helpful with regard to the research question to show the percentage change in flight traffic instead of using absolute numbers. For a better overview, the chart could focus some regions or provide a drop-down selection. Also, an explanation is missing whether the lines or bars represent the COVID-19 cases or flights. This could be resolved by tooltips for example. As some lines and the bars have similar colours, the choice of colour needs to be changed. 

A categorisation in the second chart would help to better distinguish the fields of the heatmap. Like in the first chart, the relative change in the numbers of flights would be more informative.

For the third chart a legend or tooltips would be helpful to get any information of the content in this chart. Also, the title could provide more information like the time frame that is covered in the graph. 

Overall, the information given by the different visualizations are similar. Therefore, further perspectives would have been interesting. For example, additional factors like travel restrictions could have been integrated to provide more information on the correlation between COVID-19 cases and flight traffic.

Additionally descriptive text passages in the form of an introduction or transition between the visualizations would clarify the task and message the charts should provide. Also the implemented interaction can easily be overlooked. Therefore a reference to selective or conditional parts should be given.


## References
*Munzner, T. (2009)*: A Nested Model for Visualization Design and Validation, in: IEEE Transactions on Visualization and Computer Graphics 15(6), pp. 921-928.

*Péjac, B. (2020)*: CoViD19 & FLight Traffic - A Data Exploration Story, online available at: https://brunottonurb.github.io/datavis/ [final call: 05.11.2020].

*Péjac, B., Mühlenhaupt, J. & Wieseke, M. (2020)*: CoViD19 & Flight Traffic - A Data Exploration Story, online available at: https://box.fu-berlin.de/s/4pqa4FxGM3G6wx4#pdfviewer [final call: 04.11.2020].

*Statista (2020)*: Auswirkungen des Coronavirus (COVID-19) auf die Luftfahrt, online available at: https://de.statista.com/statistik/studie/id/72253/dokument/auswirkungen-des-coronavirus-auf-die-luftfahrt/ [final call: 05.11.2020].

