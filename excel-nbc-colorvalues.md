# "Color Values" Tool
## Technical Details

This tool functions using a combination of in-sheet formulas and 3 VBA macros.

![NBC_Excel_ColorValues_Overview](https://github.com/user-attachments/assets/cc9b0d92-ea7f-417e-86b8-db41c846083d)

### Full Page Screenshot:
<img width="1464" alt="NBC_Excel_ColorValues_Expanded" src="https://github.com/user-attachments/assets/772844d9-00c1-4c8a-983e-f63c8b685c9b" />


### Cells A9:D12

First, users enter the show names in cells A9:A12. Then, the following formula in cells B9:B12 find the appropriate number of seasons from the "Season Info" sheets.

```javascript
=MAX(INDIRECT("'" & 'Color Values'!A9 & " Season Info'!C:C"))
```

Then, users use the bucket tool to select the first and last colors of the gradient for each show in cells C9:D12.

Pressing the button "Generate Gradient" runs two macros in order: FindHEXCode and PrintGradient.

### Macro 1: FindHEXCode
Finds the HEX codes for the colors in cells C9:D12. Then, prints the respective HEX codes in each cell.

```vba
Sub FindHEXCode()
Set r = Range("C9:D12")
Dim hexColor As String
Dim i As Long
Dim h As Long

For h = 1 To r.Columns.Count

For i = 1 To r.Rows.Count
  r.Cells(i, h).Activate
  hexColor = "#" + Right("000000" & Hex(ActiveCell.Interior.Color), 6)
  ActiveCell = hexColor
Next i

Next h
```

### Cells E9:M12

Once these HEX codes have been generated, formulas in cells E9:M12 split the HEX codes into their RGB values. For each red, green, and blue, a start value, end value, and increment value is found. Below, I will use cells E9:G9 as examples for each formula:

**Start Red Value (E9):** Starting at digit 2, takes the next two digits of HEX code in column C and converts to the red component of the RGB value. Ex. #FBBACF –> FB –> 251
```
=TEXT(HEX2DEC(MID(C9,2,2)), "00")
```

**End Red Value (F9):** Starting at digit 2, takes the next two digits of HEX code in column D and converts to the red component of the RGB value.
```
=TEXT(HEX2DEC(MID(D9,2,2)), "00")
```


**Red Increment (G9):** Divides (End Red Value - Start Red Value) by the number of seasons and rounds to nearest integer. This will give us equally-spaced red values for each season of the show.
```
=ROUND((F9-E9)/B9,0)
```


### Cells P9:Z12
These cells use a formula to generate HEX codes based on the number of seasons, the start values for each color, and the increment values for each color.

**Example Cell (P9):**
```
=IF( P$8> $B9,
     "",
     "#" & IF(ISODD(LEN(DEC2HEX($E9+$G9*(P$8-1)))),
    "0",
    "")&DEC2HEX($E9+$G9*(P$8-1))&IF(ISODD(LEN(DEC2HEX($H9+$J9*(P$8-1)))),
    "0",
    "")&DEC2HEX($H9+$J9*(P$8-1))&IF(ISODD(LEN(DEC2HEX($K9+$M9*(P$8-1)))),
    "0",
    "")&DEC2HEX($K9+$M9*(P$8-1)))
```


### Macro 2: FindHEXCode
Finds the HEX codes in cells P9:Z12, then changes the background colors of those cells to match their respective HEX codes.


```vba
Sub PrintGradient()
    Dim ws As Worksheet
    Dim rng As Range, cell As Range
    Dim clr As String

    ' Set worksheet reference
    Set ws = ThisWorkbook.Sheets("Color Values")

    ' Define the target range P9:Z12
    Set rng = ws.Range("P9:Z12")

    ' Turn off event handling to prevent errors
    Application.EnableEvents = False
    On Error GoTo bm_Safe_Exit

    ' Loop through each cell in P9:Z12
    For Each cell In rng
        If IsEmpty(cell.Value2) Then
            cell.Interior.Color = xlNone ' Clear cell color if empty
        ElseIf Trim(cell.Value2) = "" Then
            cell.Interior.Color = xlNone ' Clear cell color if only spaces
        ElseIf Len(cell.Value2) = 7 Then
            clr = cell.Value2
            cell.Interior.Color = RGB(Application.Hex2Dec(Right(clr, 2)), Application.Hex2Dec(Mid(clr, 4, 2)), Application.Hex2Dec(Mid(clr, 2, 2)))
        End If
    Next cell

bm_Safe_Exit:
    Application.EnableEvents = True ' Re-enable event handling
End Sub••••ˇˇˇˇ
```

### Applying Gradient to "Episode List"
Once users have generated their gradient, they can click the button "Apply to Episode List". This will run the Macro "ApplyEpisodeColors".

### Macro 3: Apply Episode Colors
Matches the TV show and season for every row in the "Episode List" sheet to its HEX code in the table above. Then, it changes the background color of that row to match the HEX code. The show title (column A) will always be the same as the "End Gradient" color, regardless of season. This macro does not override the conditional formatting used in the "Epsode List" sheet.

```vba
Sub ApplyEpisodeColors()
    Dim wsEpisodes As Worksheet, wsColors As Worksheet
    Dim episodeRow As Range, colorRow As Range
    Dim matchEpisode As Range, matchSeason As Range
    Dim hexColor As String, seasonNumber As Variant
    Dim seasonColumn As Range
    Dim cell As Range
    Dim rgbColor As Long
    Dim showHEX As String ' representative color for whole show (final season color)
    Dim showColor As Long
    
    ' Set worksheet references
    Set wsEpisodes = ThisWorkbook.Sheets("Episode List")
    Set wsColors = ThisWorkbook.Sheets("Color Values")
    
    ' Loop through each row in "Episode List", starting at row 2
    For Each episodeRow In wsEpisodes.Range("A2:A" & wsEpisodes.Cells(Rows.Count, 1).End(xlUp).Row)
        ' Find the matching row in "Color Values"
        Set matchEpisode = wsColors.Range("A:A").Find(episodeRow.Value, LookAt:=xlWhole)
        
        ' If no match found, skip to the next row
        If Not matchEpisode Is Nothing Then
            ' Get the season number from Column C of the current episode row
            seasonNumber = wsEpisodes.Cells(episodeRow.Row, 3).Value
            
            ' Find the matching season number in row 8 of range P8:Z8
            Set seasonColumn = wsColors.Range("P8:Z8").Find(seasonNumber, LookAt:=xlWhole)
            
            ' If season number is found, extract the HEX color
            If Not seasonColumn Is Nothing Then
                hexColor = wsColors.Cells(matchEpisode.Row, seasonColumn.Column).Value
                showHEX = wsColors.Cells(matchEpisode.Row, 4).Value 'Color of Final Season (used as whole show color)
                
                ' Validate HEX format (should be exactly 6 characters)
                If Len(hexColor) = 7 Then 'Probably do not need this validation
                    ' Convert HEX to RGB
                    rgbColor = RGB(Application.Hex2Dec(Right(hexColor, 2)), Application.Hex2Dec(Mid(hexColor, 4, 2)), Application.Hex2Dec(Mid(hexColor, 2, 2)))
                    showColor = RGB(Application.Hex2Dec(Right(showHEX, 2)), Application.Hex2Dec(Mid(showHEX, 4, 2)), Application.Hex2Dec(Mid(showHEX, 2, 2)))
                    
                     ' Apply the show color to columns A in the same row of "Episode List"
                    For Each cell In wsEpisodes.Range("A" & episodeRow.Row & ":A" & episodeRow.Row)
                        cell.Interior.Color = showColor
                    Next cell
                    
                    ' Apply the color to columns A:F in the same row of "Episode List"
                    For Each cell In wsEpisodes.Range("B" & episodeRow.Row & ":Q" & episodeRow.Row)
                        cell.Interior.Color = rgbColor
                    Next cell
                    
                End If
            End If
        End If
    Next episodeRow
End Sub

```

