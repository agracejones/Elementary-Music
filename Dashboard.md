
## Today's Classes
```dataview
TABLE
  Grade AS "Grade",
  Teacher AS "Teacher",
  choice(typeof(Time) = "object", Time[dateformat(date(today), "cccc")], Time) AS "Time"
FROM "Classes"
WHERE contains(Days, dateformat(date(today), "cccc"))
SORT choice(typeof(Time) = "object", Time[dateformat(date(today), "cccc")], Time) ASC
```

