
## Today's Classes
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
WHERE contains(
  typeof(Days) = "array"
    ? Days
    : split(Days, ", "),
  dateformat(date(today), "cccc")
)
SORT choice(
  typeof(Time) = "object",
  Time[dateformat(date(today), "cccc")],
  Time
) ASC