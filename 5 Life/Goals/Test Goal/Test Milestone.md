---

cssClass: cards, cards-cols-4
banner_icon: 🏁
---
###### [[Milestones 🏁]]
###### tags:: #life/milestone
# Test Milestone
Goal:: [[5 Life/Goals/Test Goal/Test Goal.md|Test Goal]]
Deadline:: 2024-06-30
CompletedDate:: In Progress

## 🗂️ Projects
```dataview
TABLE without ID
	banner,
	file.link AS "🏁 Name",
	"<progress value='" + (length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100 + "' max='100'></progress>" + "<br>" + round((length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100) + "% completed"
 AS Progress,
	length(filter(file.tasks.completed, (t) => t = true)) + "/" + length(file.tasks) + " Tasks",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #project/personal  
WHERE linkedmilestone = this.file.link
SORT completeddate ASC, deadline ASC
```