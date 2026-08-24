
## Today's Classes
```dataview
TABLE
    Grade AS "Grade",
    Teacher AS "Teacher",
    choice(
        typeof(Time) = "object",
        Time[dateformat(date(today), "cccc")],
        Time
    ) AS "Time",
    Unit AS "Unit",
    Lesson AS "Lesson",
    NextLesson AS "Next Lesson"
FROM "Classes"
WHERE regexmatch(
    "(^|, )" + dateformat(date(today), "cccc") + "(,|$)",
    string(Days)
)
SORT
    choice(
        typeof(Time) = "object",
        Time[dateformat(date(today), "cccc")],
        Time
    ) ASC
```
