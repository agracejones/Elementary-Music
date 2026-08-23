
## Today's Classes
```dataview
TABLE Grade, Time, Lesson
FROM "Classes"
WHERE contains(days, dateformat(date(today), "cccc"))
SORT time ASC
```

