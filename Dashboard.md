
## Today's Classes
```dataview
TABLE
    Grade AS "Grade",
    Teacher AS "Teacher",
    Days,
    Time
FROM "Classes"
WHERE contains(string(Days), "Wednesday")
```

