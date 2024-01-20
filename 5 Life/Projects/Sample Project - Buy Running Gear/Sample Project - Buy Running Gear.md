---
banner: "![[project-banner.jpg]]"
banner_icon: 🗂️
banner_y: 0.3996
status: active

---

###### [[Projects 🗂️]]
###### tags:: #project/personal 
# Sample Project - Buy Running Gear

>[!abstract]- Project Metadata
>Area:: [[Health]]
>LinkedGoal:: [[5 Life/Goals/Sample Goal - Run a Marathon/Sample Goal - Run a Marathon.md|Sample Goal - Run a Marathon]]
>LinkedMilestone:: [[5 Life/Goals/Sample Goal - Run a Marathon/Sample Milestone - Run 5 km.md|Sample Milestone - Run 5 km]]
>Start:: 2023-12-29
>Deadline:: 2024-01-31
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
- [ ] Research Running Gear
- [ ] Buy Running Gear

---

## 🗃️ Project Files
```dataview
LIST
WHERE contains(file.folder, this.file.folder)
```