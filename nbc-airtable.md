# Airtable

## Project Description:

This project is a collection of data from four NBC TV shows: The Office, 30 Rock, Community, and Parks and Recreation. This data was initially collected using the methods outlined in [Data Collections Methods](/nbc-datamthods.md).

## Why Airtable?

Airtable is a relational database software. This allows for more complex links between data than spreadsheet software like Excel or Google Sheets. Airtable also allows users to create interactive dashboards and views. Expand the section below to see the differences in the data structure between Airtable and Excel.

<details>
<summary> Full Page Screenshot </summary>
  
![NBC Airtable Base Schema](https://github.com/user-attachments/assets/707f955e-92b8-41e9-a321-fdeda1f83d14)
  
</details><br/>

## Access the Database:

Airtable is limited in public features that can be accessed wihtout an account. I hope to expand the publically available features of this database, but in the meantime, you can get a sense of the base through the screenshots below or by watching the video (coming soon).

You can also access a read-only version (account required) of the dashboards below:

<a href="https://airtable.com/invite/l?inviteId=inv7DwQSFPrkqpBNR&inviteToken=78132d4b44bc6a2e9e9e4614f0040b030214cf91a0d72bbb08b13b9a1e863106&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts">
  <img src="/images/icons/Airtable_Button.png" alt="Request Access to Airtable Base" width="150" height="50">
</a> 

Some pages can be seen publically (no account required), but much of the data is restricted and will not render:

<a href="[https://airtable.com/invite/l?inviteId=inv7DwQSFPrkqpBNR&inviteToken=78132d4b44bc6a2e9e9e4614f0040b030214cf91a0d72bbb08b13b9a1e863106&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts](https://airtable.com/appw7S2sXMf1zRiMv/shrstIhF7bMnQak1Y)">
  <img src="/images/icons/Airtable_Button2.png" alt="See Public Airtable Dashboard" width="150" height="50">
</a> 

## Dashboards

One of Airtable's main strengths is the ability to create user-friendly interfaces. These allow users to interact with (and even update) data from custom pages tailored to their needs.

Below, I will highlight some sample pages from this interface.

### Menu
<img width="163" alt="NBC_Airtable_Menu" src="https://github.com/user-attachments/assets/19aa29aa-d9a5-4efc-aad1-0d4f18682fe9" />


### Introduction to Base
**Page Type:** Dashboard <br/> <br/>
<img width="540" alt="NBC_Airtable_MainPage" src="https://github.com/user-attachments/assets/c5795baa-0bbd-49a4-a784-74cf8366809f" />

#### Featured Elements <br/>
**Buttons** <br/>
> Buttons allow users to navigate to other pages in the interface, open a record creation form, go to external URLs, or go to URLs associated with the data (such as an episode's Wikipedia page).

**Numbers** <br/>
> Numbers summarize data linked to a record by finding a sum, average, maximum, count, or other measure of that data.

**Charts** <br/>
> This bar chart shows the average views-per-episode received by each TV show per season. The overlapping line graph shows the maximum number of views any individual episode received that season.

**Gallery View** <br/>
> Gallery views summarize records through a primary image field (in this case, the show logo), with other selected data displayed below. To avoid having too many fields, I created a field called "Basic Info Summary" that summarizes the number of seasons and episodes in a given show. The cards in this gallery view show the fields "Basic Info Summary" and "IMDB Description".

Formula for the field "Basic Info Summary"
```
Name & " is a " & {Years} &
" sitcom that ran for " & {Total Seasons} & " seasons and produced " &
{Total Episodes} & " total episodes. It premiered on " & DATETIME_FORMAT({Premiere Date}, 'MMMM DD, YYYY')
& ", and its finale aired on " & DATETIME_FORMAT({Finale Date}, 'MMMM DD, YYYY') & "."
```


### Shows Overview
**Page Type:** Record Review <br/> <br/>
![NBC_Airtable_SO_ShowPages](https://github.com/user-attachments/assets/b9d7359e-c591-44d7-9950-698afba71ef9)


![NBC_Airtable_SO_Levels](https://github.com/user-attachments/assets/8b2002e9-e2e5-49ee-93ae-93f4e6f4c8ef)

#### Featured Elements <br/>
**Buttons** <br/>
> Buttons allow users to navigate to each show's Wikipedia page, Peacock link, or JustWatch link (to see an updated list of streaming services where the show is available). After drilling down to deeper levels of data, users can visit the Wikipedia page for an individual episode, writer, or director (if available).

**Click Into Record Details** <br/>
> By selecting a piece data on one page (ex. "Season 5" on the "30 Rock" page), users can see deeper levels of data. On this page, users can see stats and information for each show, season, and episode in the dataset. Users can also select individual writers or directors to see a list of all their writing and directing credits between the four shows. Each TV Cycle Year (ex. 2010-11) even has its own page with an overview of which of the 4 shows was on that year, their timeslots, and statistics about each of them.

**In-Line Editing** <br/>
>Authorized users (me) can edit rating and review information from the page itself. This makes it easy to look up an episode and review it without needing to open the larger database.

### Episode List
**Page Type:** List <br/> <br/>

![NBC_Airtable_EpisodeList_Graphic](https://github.com/user-attachments/assets/b0c87888-ac33-484f-8c5d-e0c621213215)


#### Featured Elements <br/>
**Hierarchies of Data** <br/>
> This list utilizes two levels of data: TV Cycle Year and Episodes. Information about each TV year (like which shows are on air that year) can be displayed in the year header, and information about episodes can be displayed in the episode rows. Users can click into either years or episodes to see detail pages. Lists in Airtable can have even more levels, which can be useful for projects where hierarchies or dependencies are important. 

**Grouping, Filtering, Sorting, and Searching** <br/>
> Users can apply their own custom grouping, sorting, and filtering to the data. Users can also search for an episode directly by title. This makes this view the most useful for finding specific episodes quickly.

