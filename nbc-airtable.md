# Airtable

## Project Description:

This project is a collection of data from four NBC TV shows: The Office, 30 Rock, Community, and Parks and Recreation. This data was initially collected using the methods outlined in [Data Collections Methods](/nbc-datamethods.md).

## Why Airtable?

Airtable is a relational database software. This allows for more complex links between data than spreadsheet software like Excel or Google Sheets. Airtable also allows users to create interactive dashboards and views. Expand the section below to see the differences in the data structure between Airtable and Excel.

<details>
<summary> Full Page Screenshot </summary>
  
<img alt="Excel and Airtable Schema Comparison " src="images/NBC Airtable Base Schema.png" />
  
</details>

<br/>

## Access the Database:

Airtable is limited in public features that can be accessed without an account. I hope to expand the publically available features of this database, but in the meantime, you can get a sense of the base through the screenshots below or by watching the video (coming soon).

You can request access to a read-only version (account required) of the dashboards below. You can also publically access some of the pages below (no account required), but much of the data is restricted and will not render.

<a href="https://airtable.com/invite/l?inviteId=inv7DwQSFPrkqpBNR&inviteToken=78132d4b44bc6a2e9e9e4614f0040b030214cf91a0d72bbb08b13b9a1e863106&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts">
  <img src="/images/icons/Airtable_Button.png" alt="Request Access to Airtable Base" width="150" height="50">
</a> 
<a href="https://airtable.com/appw7S2sXMf1zRiMv/shrstIhF7bMnQak1Y">
  <img src="/images/icons/Airtable_Button2.png" alt="See Public Airtable Dashboard" width="150" height="50">
</a> <br/>




----
<br/>

# Explore the Dashboards

One of Airtable's main strengths is the ability to create user-friendly interfaces. These allow users to interact with (and even update) data from custom pages tailored to their needs. Here are some sample pages from this interface.

## Menu
<img width="163" alt="NBC_Airtable_Menu" src="https://github.com/user-attachments/assets/19aa29aa-d9a5-4efc-aad1-0d4f18682fe9" />

----

## Introduction to Base
<img width="540" alt="NBC_Airtable_MainPage" src="https://github.com/user-attachments/assets/c5795baa-0bbd-49a4-a784-74cf8366809f" /> <br/>

**Page Type:** Dashboard <br/> <br/>

**Featured Elements:** <br/>
> **Buttons** <br/>
> Buttons allow users to navigate to other pages in the interface, open a record creation form, go to external URLs, or go to URLs associated with the data (such as an episode's Wikipedia page).

> **Numbers** <br/>
> Numbers summarize data linked to a record by finding a sum, average, maximum, count, or other measure of that data.

> **Charts** <br/>
> This bar chart shows the average views-per-episode received by each TV show per season. The overlapping line graph shows the maximum number of views any individual episode received that season.

> **Gallery View** <br/>
> Gallery views summarize records through a primary image field (in this case, the show logo), with other selected data displayed below. To avoid having too many fields, I created a field called "Basic Info Summary" that summarizes the number of seasons and episodes in a given show. The cards in this gallery view show the fields "Basic Info Summary" and "IMDB Description".

**Formula for the field "Basic Info Summary":**
```
Name & " is a " & {Years} &
" sitcom that ran for " & {Total Seasons} & " seasons and produced " &
{Total Episodes} & " total episodes. It premiered on " & DATETIME_FORMAT({Premiere Date}, 'MMMM DD, YYYY')
& ", and its finale aired on " & DATETIME_FORMAT({Finale Date}, 'MMMM DD, YYYY') & "."
```

<br/>
----

## Shows Overview
![NBC_Airtable_SO_ShowPages](https://github.com/user-attachments/assets/b9d7359e-c591-44d7-9950-698afba71ef9)


![NBC_Airtable_SO_Levels](https://github.com/user-attachments/assets/8b2002e9-e2e5-49ee-93ae-93f4e6f4c8ef)

**Page Type:** Record Review <br/> <br/>

**Featured Elements:** <br/>
> **Buttons** <br/>
> Buttons allow users to navigate to each show's Wikipedia page, Peacock link, or JustWatch link (to see an updated list of streaming services where the show is available). After drilling down to deeper levels of data, users can visit the Wikipedia page for an individual episode, writer, or director (if available).

> **Click Into Record Details** <br/>
> By selecting a piece data on one page (ex. "Season 5" on the "30 Rock" page), users can see deeper levels of data. On this page, users can see stats and information for each show, season, and episode in the dataset. Users can also select individual writers or directors to see a list of all their writing and directing credits between the four shows. Each TV Cycle Year (ex. 2010-11) even has its own page with an overview of which of the 4 shows was on that year, their timeslots, and statistics about each of them.

> **In-Line Editing** <br/>
>Authorized users (me) can edit rating and review information from the page itself. This makes it easy to look up an episode and review it without needing to open the larger database.

<br/>
----

## Episode List

![NBC_Airtable_EpisodeList_Graphic](https://github.com/user-attachments/assets/b0c87888-ac33-484f-8c5d-e0c621213215)

**Page Type:** List <br/> <br/>

**Featured Elements:** <br/>
> **Hierarchies of Data** <br/>
> This list utilizes two levels of data: TV Cycle Year and Episodes. Information about each TV year (like which shows are on air that year) can be displayed in the year header, and information about episodes can be displayed in the episode rows. Users can click into either years or episodes to see detail pages. Lists in Airtable can have even more levels, which can be useful for projects where hierarchies or dependencies are important. 

> **Grouping, Filtering, Sorting, and Searching** <br/>
> Users can apply their own custom grouping, sorting, and filtering to the data. Users can also search for an episode directly by title. This makes this view the most useful for finding specific episodes quickly.

<br/>
----

## Lena's Reviews
<img width="910" alt="NBC_Airtable_LenaReviews" src="https://github.com/user-attachments/assets/f721b370-0a37-48c6-b739-ea7f35904798" />

**Page Type:** Gallery <br/><br/>
**Featured Elements:** <br/>
> **Gallery View** <br/>
> Gallery views summarize records through a primary image field (in this case, the DVD cover), with other selected data displayed below. This view is filtered so that it only shows episodes I have rated or reviewed. Users can click on an episode to open the details page, where they can see information and statistics about an episode or edit ratings/reviews in-line.


<br/>
----

## Season Timeline

<img width="707" alt="NBC_Airtable_SeasonTimeline" src="https://github.com/user-attachments/assets/0c8addd5-59f9-4412-8cfc-2477fa480960" />

**Page Type:** Timeline <br/><br/>
**Featured Elements:** <br/>
>**Timelines** <br/>
> Timelines allow Airtable users to visualize events or periods of time using a start and end date. For more complex timelines– such as production schedules where one task may depend on the completion of another– [Gantt Charts](https://www.airtable.com/articles/product/gantt-charts) are also an option.

<br/>
----

## Calendar 

![NBC_Airtable_CalendarGraphic](https://github.com/user-attachments/assets/fdf7fd34-6ed4-479d-98c0-f9fece654dbb)

**Page Type:** Calendar <br/><br/>
**Featured Elements:** <br/>
> **Calendars** <br/>
> Calendars allow users to display their records based on a date field. In this case, the calendar shows TV episodes based on their original air date.

<br/>
----

## Statistics

<img width="515" alt="NBC_Airtable_StatsDash" src="https://github.com/user-attachments/assets/3dea0f13-e8e4-4a6a-b265-5c73e672f648" />

![NBC_Airtable_StatsDash_Graphic](https://github.com/user-attachments/assets/f4e37e8c-d510-4e04-b203-90f79a2cfc91)

**Page Type:** Blank Dashboard <br/><br/>

**Featured Elements:** <br/>

> **Connected Filters** <br/>
> Users can customize what they see by filtering the data to only include certain shows, years, seasons, writers, and directors. These filters are connected to the numbers, line graph, pie chart, and episode list, and the graphics automatically update to match the filters. This allows users to answer specific questions without being overwhelmed by options.

> **Numbers, Line Graphs, and Pie Charts** <br/>
> These elements display important data in a visual, succinct manner.

> **Episode List** <br/>
> The list of records shows the data entries that make up the graphics. Users can expand individual episodes to get more information.

<br/>
----

## Writers
<img width="752" alt="NBC_Airtable_Writers_TinaFey" src="https://github.com/user-attachments/assets/1f016070-4ea3-4f7f-802d-2a1454551e5b" />
<img width="753" alt="NBC_Airtable_MichaelShur" src="https://github.com/user-attachments/assets/39cb735a-e65f-4ba1-aef7-c40de190da92" />

**Page Type:** Blank Dashboard <br/><br/>

**Featured Elements:** <br/>

>**Record Picker** <br/>
> Users can switch between writers using the record picker in the top righthand corner. The options are pre-filtered to exclude creators who have directed but do not have writing credits.

>**Buttons** <br/>
> Users can visit a writer's Wikipedia page or the Wikipedia page for any individual episode using buttons.

>**Numbers, Line Charts, and Bar Charts** <br/>
> These are all ways to summarize writer data visually. The "Views Per Episode" line graph is color-coded by TV show, and the bar chart includes a manual filter for users to see a writer's involvement in a given show each season.


>**"Hero" and "Carousel" Photos** <br/>
> Airtable dashboards include many options for displaying photos. "Hero" photos, like the writer headshots, are large singular images without a file or field name. Meanwhile, "carousel" photos are areas that can display multiple photos at once, like our show logos. If their were too many photos for the space, a scrollbar is added automatically.


> **Gallery Views** <br/>
>  Gallery views summarize records through a primary image field (like a season DVD cover), with other selected data displayed below. The two gallery views on this page are identical, but they are filtered differently. "Lena's Reviews" only shows the records of episodes I have rated or reviewed. "Most Viewed Episodes," however, shows all the writer's episodes sorted from most-to-least views. Depending on screen size, the top 1-3 episodes are displayed.






