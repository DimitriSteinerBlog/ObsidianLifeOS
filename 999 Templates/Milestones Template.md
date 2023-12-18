---
<%* 
const dv = this.app.plugins.plugins["dataview"].api; 
let goals = dv.pages('#life/goal and "5 Life"').file.sort(n => n.name); 
let goal_names = goals.name; 
let goal_links = goals.link; 
-%>

cssClass: cards, cards-cols-4
banner_icon: 🏁
---
###### [[Milestones 🏁]]
###### tags:: #life/milestone
# <% tp.file.title %>
Goal:: <% await tp.system.suggester(goal_names, goal_links, false, "Please select the goal for this milestone") %>
Deadline:: <% await tp.system.prompt("Deadline Date (YYYY-MM-DD)") %>
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