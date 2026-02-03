# Ontario Data Catalogue: School board achievements and progress dataset
 https://data.ontario.ca/dataset/school-board-achievements-and-progress

 For each visualization, describe and justify: 
    > What software did you use to create your data visualization?
    - Seaborn, which is "a Python data visualization library based on matplotlib." https://seaborn.pydata.org/index.html
    - I selected it because I wanted to examine the bivariate relationships between Ontario district school boards' secondary student five-year graduation rate and the Grade 10 and Grade 11 course credit accumulation rates, disaggregated by school board's physical location in Ontario (i.e., board region). I also wanted to visualize the univariate distribution of the selected variables by board region. 

    > Who is your intended audience? 
    - My intended audience is my doctoral supervisor, but it could also be subject matter experts in Ontario student achievement. For my doctoral research writing, I wanted to produce a graph suitable for presentation at a graduate seminar or conference, as background for my research topic.
    - The intended medium is print, poster, or presentation.
    
    > What information or message are you trying to convey with your visualization? 
    - I am trying to convey that Ontario secondary student achievement varies widely by where an Ontario student happens to attend school in the province.
    
    > What aspects of design did you consider when making your visualization? How did you apply them? With what elements of your plots? 
    - I identified a categorical attribute in my selected dataset, board region, and overlaid that on three quantitative student achievement variables most proximal to student public education outcomes: school board credit accumulation and graduation rates.
    - My primary design goal was substantive, given the intended audience for my data visualization. Therefore, I wanted to plot each bivariate or univariate relationship in a separate plot to show the range of possible data point values for each relationship. The Seaborn pairplot figure is ideal for this purpose. 
    - A second design goal was substantive. In particular, the univariate density plots highlight the clear and consistent differences for the selected student achievement measures in the 70 English-language school districts, according to district location in Ontario. The bivariate scatter plots provide greater detail. 
    - The third goal was aesthetic. Despite the complexity inherent in a 3x3 figure plot grid, I've attempted to minimize unnecessary detail (e.g., simplify variable names), use a pleasing, high-contrast colour palette, add grid lines to improve cross-plot comparisons, and locate figure elements in expected areas (e.g., course reference at bottom of figure).

    > How did you ensure that your data visualizations are reproducible? If the tool you used to make your data visualization is not reproducible, how will this impact your data visualization?
    - I used a dataset which is available in the public domain, and which has some accompanying data variable descriptive information available online. Regarding the dataset's file formatting, the provincial government states: "If you require an accessible format or communication supports, please contact the Ministry of Education." 
    - I am including my Python coding in a Jupyter notebook, so that others can reproduce my data visualization. I have commented my code to explain the coding functions used and the reasoning behind them.  
    
    > How did you ensure that your data visualization is accessible?  
    - I selected the Seaborn "colorblind" colour palette and subsequently checked it on the Coblis —  Color Blindness Simulator, where it performed well on all criterion items.
    - I added markers to help further distinguish the regional variable categorical values.
    - I tested and chose a more readable context, which helped to further separate the figure plots visually and which added white grid lines that did not visually clutter the figure. 

    > Who are the individuals and communities who might be impacted by your visualization?  
    - School boards in Ontario, which continue to attempt to do more with less in terms of resources, might be impacted by the knowledge that regional location is destiny, despite this being a factor over which they have no control. 
    
    > How did you choose which features of your chosen dataset to include or exclude from your visualization? 
    - I originally selected board type (i.e., Public or Roman Catholic) to filter the datapoints. Catholic school boards consistently outperformed Public boards on all three measures (see my Jupyter notebook for exploratory figures). However, Public and Catholic boards overlap geographically, and SES covariates likely contribute to regional differences in secondary student achievement, so I decided to explore this instead. 
    
    > What ‘underwater labour’ contributed to your final data visualization product?
    - My doctoral supervisor, who is the unsung champion of my research work and development efforts.
    - Ontario Ministry of Education public servants, who continue to advocate from within to publish policy-relevant data. 
    - Ontario school board administrators, teachers and their students, who strive to improve outcomes for all students, and by extension, for Ontario as a whole. 
    - DSI, without which I may not have learned how to visualization my research data in a more accessible way and more broadly, for a potentially wider audience. 
