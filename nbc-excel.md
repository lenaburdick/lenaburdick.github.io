# Microsoft Excel

**Project description:**  
This project is a collection of data from four NBC TV shows: The office, 30 Rock, Community, and Parks and Recreation.  

**Download the workbook here:**  

<a href="/uploads/NBC Thursday Night Line Up - Github.xlsm" download>
  <img src="/images/icons/Excel_Button.png" alt="Download Excel File" width="150" height="50">
</a> 
</br> </br>

>  [!IMPORTANT]
>  If given the option, ensure it is a macro-enabled file (.xlsm). Click "Enable Macros" when prompted after opening. You can also browse the screenshots or video (coming soon) below.


Workbook Guide:
======


Introduction Page
------

<details>
<summary> Full Page Screenshot </summary>
<img src="images/NBC/Excel/NBC_Excel_MainPage.png"/>
</details>

> This sheet gives users an overview of the workbook as a whole. It also functions as an index for skills utilized and formula types.


---

Episode List
------
<details>
<summary> Full Page Screenshot </summary>
<img src="images/NBC/Excel/NBC_Excel_EpisodeList.png"/>
</details>

> This sheet features a table of every episode of each show. The table can be filtered and sorted by different metrics. Some cells utilize conditional formatting to quickly identify information about air time, ratings, and schedule. All other cells are colors based on the show and season– these colors can be specified using the "Color Values" tool.


---

Graphs
------
<details>
<summary> Full Page Screenshot </summary>
<img src="images/NBC/Excel/NBC_Excel_Graphs.png"/>
</details>

> This sheet utilizes pivot tables and lookup tables to graph various metrics. A future goal of this project is automatically matching the colors of TV shows in the legend with the colors specified in the "Color Values" tool.

![NBC_Excel_SampleGraphs](https://github.com/user-attachments/assets/ca2172da-a95f-4632-88f4-f5b6e647438c)


---

Color Values
------

**Technical Details:** [Click Here](/excel-nbc-colorvalues.md) to explore the technical details of the Color Value Tool

<details>
<summary> Full Page Screenshot</summary>

<img width="911" alt="NBC_Excel_ColorValues_Main" src="https://github.com/user-attachments/assets/f5ba0ecb-a0bc-41e5-b15e-15649381275b" />
  
</details>


> This tool gives users control over the colors used to identify shows & seasons in "Episode List". A future goal of this project is to connect this tool to the "Graphs" sheet, as well. Please note that this tool will only work in a macro-enabled workbook (see instructions at top of page for more details).

![NBC_Excel_ColorValues_Overview](https://github.com/user-attachments/assets/cc9b0d92-ea7f-417e-86b8-db41c846083d)


---

Season Info
------

<details>
<summary> Sample Page Screenshot</summary>

<img width="1415" alt="NBC_Excel_SeasonInfo" src="https://github.com/user-attachments/assets/c0a349b5-2586-4efb-82b5-cfc2fbfa79f9" />
  
</details>

> Each show has its own sheet titled "[Show Name] Season Info". These data came from .csv files scraped from Wikipedia tables. Some data had to be cleaned and formatted for consistency.

