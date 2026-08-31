
## Today's Classes
```dataviewjs
const today = moment().format("dddd");

const classes = [];

for (const p of dv.pages('"Classes"')) {
    if (!String(p.Days).includes(today)) continue;

    let time;

    if (p.Time && typeof p.Time === "object" && !Array.isArray(p.Time)) {
        time = p.Time[today];
    } else {
        time = p.Time;
    }

    if (!time) continue;

    const start = String(time).match(/^(\d{1,2}):(\d{2})/);

    let sortTime = 9999;

    if (start) {
        let hour = Number(start[1]);
        const minute = Number(start[2]);

        // Your school schedule uses 12-hour time without AM/PM.
        // Treat 1:00–7:59 as afternoon.
        if (hour >= 1 && hour <= 7) {
            hour += 12;
        }

        sortTime = hour * 60 + minute;
    }

    classes.push({
        grade: p.Grade,
        teacher: p.Teacher,
        time: String(time),
        unit: p.Unit,
        lesson: p.Lesson,
        nextLesson: p.NextLesson,
        sortTime: sortTime
    });
}

classes.sort((a, b) => a.sortTime - b.sortTime);

dv.table(
    ["Grade", "Teacher", "Time", "Unit", "Lesson", "Next Lesson"],
    classes.map(c => [
        c.grade,
        c.teacher,
        c.time,
        c.unit,
        c.lesson,
        c.nextLesson
    ])
);
```


![[Week Schedule]]
> There are at least two hours of prep **every day.** Use them wisely and you'll never have to take work home!
## To-Do
- [ ] Print, laminate, and cut picture rhythms
- [ ] Print, laminate, and cut pokemon game cards
- [ ] Make, print, laminate, and cut rhythm building blocks