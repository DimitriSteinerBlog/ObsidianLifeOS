---
<%* 
const dv = this.app.plugins.plugins["dataview"].api; 
let areas = dv.pages('#life/area and "5 Life"').file.sort(n => n.name); 
let area_names = areas.name; 
let area_links = areas.link; 
let values = dv.pages('#life/value and "5 Life"').file.sort(n => n.name); 
let value_names = values.name; 
let value_links = values.link; 
-%>

banner: "![[goals-banner.jpg]]"
banner_icon: 🎯
banner_y: 0.42771
---
###### [[Goals 🎯]]
###### tags:: #life/goal
# <% tp.file.title %>

>[!abstract]- Goal Metadata
>Value:: <% await tp.system.suggester(value_names, value_links, false, "Please select the value for this goal") %>
>Area:: <% await tp.system.suggester(area_names, area_links, false, "Please select the area for this goal") %>
>Start:: <% tp.date.now("YYYY-MM-DD") %>
>Deadline:: <% await tp.system.prompt("Deadline Date (YYYY-MM-DD)") %>
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
