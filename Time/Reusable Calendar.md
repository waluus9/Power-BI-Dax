```cadence
Date Table (CALENDARAUTO) =
VAR MinYear = YEAR(MIN('Calendar'[Transaction_Date]))
VAR MaxYear = YEAR(MAX('Calendar'[Transaction_Date]))

RETURN
ADDCOLUMNS(
    FILTER(
        CALENDARAUTO(),
        YEAR([Date]) >= MinYear &&
        YEAR([Date]) <= MaxYear
    ),
    "Year", YEAR([Date]),
    "Quarter Number", INT(FORMAT([Date], "q")),
    "Quarter", "Q" & INT(FORMAT([Date], "q")),
    "Month number", MONTH([Date]),
    "Month Short", FORMAT([Date], "mmm"),
    "Week Number", WEEKNUM([Date])
)
```
