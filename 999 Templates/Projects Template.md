---
<%* 
const dv = this.app.plugins.plugins["dataview"].api; 
let areas = dv.pages('#life/area and "5 Life"').file.sort(n => n.name); 
let area_names = areas.name; 
let area_links = areas.link; 
let goals = dv.pages('#life/goal and "5 Life"').file.sort(n => n.name); 
let goal_names = goals.name; 
let goal_links = goals.link; 
let milestones = dv.pages('#life/milestone and "5 Life"').file.sort(n => n.name); 
let milestone_names = milestones.name; 
let milestone_links = milestones.link; 
-%>

banner: "![[project-banner.jpg]]"
banner_icon: 🗂️
banner_y: 0.3996
status: backlog
---

###### [[Projects 🗂️]]
###### tags:: #project/personal 
# <% tp.file.title %>

>[!abstract]- Project Metadata
>Area:: <% await tp.system.suggester(area_names, area_links, false, "Please select the area for this project") %>
>LinkedGoal:: <% await tp.system.suggester(goal_names, goal_links, false, "Please select the goal for this project") %>
>LinkedMilestone:: <% await tp.system.suggester(milestone_names, milestone_links, false, "Please select the milestone for this project") %>
>Start:: <% tp.date.now("YYYY-MM-DD") %>
>Deadline:: <% await tp.system.prompt("Deadline Date (YYYY-MM-DD)") %>
>CompletedDate:: In Progress

## 📊 Progress

```dataviewjs  
let file = dv.current().file
let totalTask = file.tasks.length  
let completedTask = file.tasks.where(t => t.completed).length  
let tasksp = Math.round((completedTask / totalTask) * 100)  
dv.span("![progress|120](https://progress-bar.dev/" + tasksp + "/)")
```

---

## ✅ Tasks
- [ ] Task 1

---

## 🗃️ Project Files
```dataview
LIST
WHERE contains(file.folder, this.file.folder)
```