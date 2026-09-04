
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

## Weekly Schedule

![[Week Schedule]]
> There is at least an hour and a half of prep **every day.** Use it wisely and you'll never have to take work home!

- Before crosswalk
	- [ ] Put away lunch and belongings
	- [ ] Pick secret student number and mark lists
	- [ ] Open all seating charts and lesson plans
	- [ ] Pray
- 10 minute breaks between classes
	- [ ] Use the bathroom
	- [ ] Glance over next class's lesson plan and update current and next lesson on previous class
	- [ ] Room reset
	- [ ] Movement break
- Lunch
	- [ ] This is my break! Don't do any work. Just eat, use the bathroom, and unwind.
	- [ ] If not watching an episode of a show, set a timer so that I get back on track afterwards.
- 45+ minute prep period
	- [ ] Check running to-do
	- [ ] Make sure lesson plans are ready 2 weeks out
	- [ ] Get ahead on lesson plans if needed
	- [ ] Longer movement break
- Before leaving
	- [ ] Clean up desk and belongings
	- [ ] Review tomorrow's classes
	- [ ] Update to-do list
	- [ ] Lights and door
## To-Do
- [ ] Print, laminate, and cut pokemon game cards
- [ ] Write star student emails Friday
	- [x] Isabel McCormick
	- [x] Zander Fennig
	- [x] Weston Schott
	- [x] Sofia McPherson
	- [x] Emily Gay
	- [x] Celeste Carranza
	- [x] Annie Miller
	- [x] Gavin Kessler
	- [x] Juniper Cady
	- [x] Liam Gay
	- [x] Harper Glodt(after Lowry's class)
	- [x] Olivia Garcia
	- [x] Brooklynn Edmiston
	- [ ] Jet Leigh
	- [ ] Daklynn DuPont
- [x] Print more song sheets (3 pages)
- [ ] Lesson plans
	- [ ] K 1.3
	- [ ] K 1.4
	- [ ] 1st 1.5
	- [ ] 1st 1.6
	- [ ] 2nd 1.5
	- [ ] 2nd 1.6
	- [ ] 3rd 1.5
	- [ ] 3rd 1.6
	- [ ] 4th 1.5
	- [ ] 4th 1.6
	- [ ] 5th 1.5
	- [ ] 5th 1.6