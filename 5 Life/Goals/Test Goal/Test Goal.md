---

banner: "![[goals-banner.jpg]]"
banner_icon: 🎯
banner_y: 0.42771
---
###### [[Goals 🎯]]
###### tags:: #life/goal
# Test Goal

>[!abstract]- Goal Metadata
>Value:: [[5 Life/Values/Sample Value - Healthy.md|Sample Value - Healthy]]
>Area:: null
>Start:: 2023-12-08
>Deadline:: 2024-12-31
>CompletedDate:: In Progress

## 📊 Progress

```dataviewjs
let files = dv.pages('#life/milestone').where(p => String(p.goal) == String(dv.current().file.link))

let totalMile= files.length  
let completedMile = files.where(p => p.completeddate != "In Progress").length  

let progress = Math.round((completedMile / totalMile) * 100)  

dv.span("![progress|120](https://progress-bar.dev/" + progress + "/)")
```

---

## 🏁 Milestones

```dataview
TABLE without ID
	file.link AS "🏁 Name",
	choice(completeddate = "In Progress", "🏗️", "✅") AS "✅ Completed",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone 
WHERE goal = this.file.link
SORT completeddate ASC, deadline ASC
```
```button
name + New Milestone
type command
action QuickAdd: Add Milestone
```

---

## 🗂️ Projects
```dataviewjs
const DQL = `
TABLE without ID
	banner,
	file.link AS "🏁 Name",
	"<progress value='" + (length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100 + "' max='100'></progress>" + "<br>" + round((length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100) + "% completed"
 AS Progress,
	length(filter(file.tasks.completed, (t) => t = true)) + "/" + length(file.tasks) + " Tasks",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #project/personal  
WHERE linkedgoal = this.file.link
SORT completeddate ASC, deadline ASC
`

dv.execute(DQL)

dv.container.classList.add("cards")
dv.container.classList.add("cards-cols-4")
```
