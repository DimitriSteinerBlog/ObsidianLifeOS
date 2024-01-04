---
banner_icon: ✔️
---
###### [[Home]]
###### tags:: #atlas/view👓
# Tasks Dashboard
[[Tasks ✔️|🏁 Today]] | [[Tasks - Overdue ✔️|⚠️ Overdue]] | [[Tasks - Upcoming ✔️|➡️ Upcoming]] | [[Tasks - Inbox ✔️|📥 Inbox]] | [[Tasks - Calendar ✔️|📅 Calendar]] | [[Tasks - Timeline ✔️|⏳ Timeline]]
## 📅 Calendar
```dataviewjs
await dv.view("tasksCalendar", {
	pages: '"5 Life" OR "6 Blog"',
	view: "week", 
	firstDayOfWeek: "1", 
	options: "style4 noDailyNote noDone",
	css: ".tasksCalendar.style4[view='week'] .grid { height: 500px !important }"
})
```