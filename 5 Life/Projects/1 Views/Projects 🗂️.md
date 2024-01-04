---
banner_icon: 🗂
cssClass: cards
---
###### [[Home]]
# Projects Dashboard

```button
name + New Project
type command
action QuickAdd: Add Project
```

[[Projects - KanBan 🗂️| 🧮 KanBan]] | [[Projects 🗂️|🏗️ Active]] | [[Projects - Inactive 🗂️|⛔ Inactive]] | [[Projects - Backlog 🗂️| 📋 Backlog]] | [[Projects - Archive 🗂️|🗃️ Archive]]
## 🏗️ Active Projects
```dataview
TABLE without ID
	banner,
	file.link AS " 🗂 Name",
	"<progress value='" + (length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100 + "' max='100'></progress>" + "<br>" + round((length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100) + "% completed"
 AS "📈 Progress",
	length(filter(file.tasks.completed, (t) => t = true)) + "/" + length(file.tasks) + " Tasks" AS "✅ Tasks",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #project/personal AND "5 Life" 
WHERE status = "active"
SORT completeddate ASC, deadline ASC
```
<br>

## 📅 Projects Calendar
```dataviewjs
await dv.view("tasksCalendar", {
	pages: '"5 Life/Projects"',
	view: "month", 
	firstDayOfWeek: "1", 
	options: "style1 noOverdueDays noIcons noDone"})
```