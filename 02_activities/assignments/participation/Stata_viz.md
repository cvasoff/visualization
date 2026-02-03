# Ontario Data Catalogue: School board achievements and progress dataset
 https://data.ontario.ca/dataset/school-board-achievements-and-progress

 For each visualization, describe and justify: 
    > What software did you use to create your data visualization?
    - Stata "statistical software for data science": https://www.stata.com/
    - I selected Stata because I could produce a coding file for image replication. However, I also find it cumbersome for producing detailed graphs. So, I thought it would be interesting to produce similar graphs using both software applications and to compare the relative effort required and the customization/flexibility inherent in each application.

    > Who is your intended audience? 
    - Definitely a specialized audience that is already knowlegeable on the topic and Ontario student achievement and attainment. Stata graph formatting, in my opinion, would likely be off-putting to a non-specialist audience. 

    > What information or message are you trying to convey with your visualization? 
    - I am attempting to provide a lot of information about the association between secondary student credit accumulation and graduation rates as possible, and to clearly show that the two factors are linked according to students' school board attendance. This would not have been possible had the provincial government not recently decided to publish this single (cross-sectional) dataset for the first time, late last year. 
    
    > What aspects of design did you consider when making your visualization? How did you apply them? With what elements of your plots? 
    - I wanted to strike a balance between an uncluttered and clean layout, while providing as much contextual information as possible to help the audience accurately interpret the data as objectively as possible. For example, despite the complexity inherent in showing both the Grade 10 and Grade 11 credit rates on a single graph, I chose to do so to demonstrate that both indicators maintain a similar relationship for high school graduations rates by board. Therefore, I visually distinguished the two grade's credit rates using colour (blue or orange) and added a lowess trend line to highlight the similarity of direction in the relationship between credit and graduation rates among school boards. I also added more detail information about the dataset: cross-sectional data, credit accumulation benchmark metrics, and which school boards were excluded.
    - In generating a more technical graph, with added complexity, I understand that the data visualization is primarily suited for distribution in a print or web-based mediums, and for the purpose of exploring and evaluating factors which potentially affect student outcomes in an Ontario public education context. 
    - The data visualization presentation is purposely as factual and objective as possible. However, in selecting these variables without conditioning them on other factors, such as student or school board demography or boards' relative resource challenges, I know that I've simplified the story my visualization tells. Therefore, my narrative is not neutral in its messaging. 
    
    > How did you ensure that your data visualizations are reproducible? If the tool you used to make your data visualization is not reproducible, how will this impact your data visualization? 
    - The data visualization clearly displays the dataset information source. However, it would be challenging to reproduce this graph without specialist training in Stata software. Also, Stata is not open source, so cost is a potential barrier for reproducibility as well.
    - These factors mean that some audiences may dismiss my messaging since they may not be able to reproduce the results for themselves. 
    
    > How did you ensure that your data visualization is accessible? 
    - I continued to refine my data visualization iteratively by adjusting the layout (e.g., centring headings, adjusting font size, and relocating information), improving information formatting (e.g., changing decimal to percentage for interpretability), and using colour to highlight the main message.
    - I checked my initial data visualization on the Coblis —  Color Blindness Simulator, and changed my colour scheme until I'd optimized my colour contrast to the fullest extent possible given Stata's limited colour palette and ease for reformatting. I strove to use hue to distinguish the two scatter plot groups depicted on my graph.
   
    > Who are the individuals and communities who might be impacted by your visualization? 
    - The primary group of people who might be impacted by my graph would be academics or policy-oriented organizations which are already interested in student achievement or attainment inequities.
    - It crossed my mind that the Ontario government might be concerned about how the information it's publishing might be harnessed as being at cross-purposes to its political and policy formulations, but not sure what to do about that. 

    > How did you choose which features of your chosen dataset to include or exclude from your visualization?
    - For this visualization, I chose to explore the relationship between factors for which there is little published peer-reviewed research: credit accumulation and student graduation rates. I also wanted to exclude other categorical variables on which I could potentially filter, to examine the main relationship finding first. 
    - I also chose not to identify specific school board outliers; the purpose of the graph is to show the overall relationship, not which boards are struggling to improve student outcomes. 

    > What ‘underwater labour’ contributed to your final data visualization product?
    - This information is identical to my response for the python visualization; except I would like to mention the role of the University of Toronto in providing me with the graduate-level training and knowledge required to explore and share my research findings in the first instance. 