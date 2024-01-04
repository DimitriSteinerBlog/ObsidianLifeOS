---
banner_icon: ✔️
---
###### [[Home]]
###### tags:: #atlas/view👓
# Tasks Dashboard
[[Tasks ✔️|🏁 Today]] | [[Tasks - Overdue ✔️|⚠️ Overdue]] | [[Tasks - Upcoming ✔️|➡️ Upcoming]] | [[Tasks - Inbox ✔️|📥 Inbox]] | [[Tasks - Calendar ✔️|📅 Calendar]] | [[Tasks - Timeline ✔️|⏳ Timeline]]
## ⏳ Timeline
```dataviewjs
await dv.view("taskido", {
	pages: '"5 Life"',
	options: "noMotivation noRepeat noFile noDone noYear",
	carryForwardOverdue: true,
	taskFiles: '"5 Life/Tasks"',
	select: "5 Life/Tasks/Other Tasks.md"
})
```


