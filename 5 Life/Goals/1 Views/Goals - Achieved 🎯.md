---
banner_icon: 🎯
---
###### [[Home]]
###### tags:: #atlas/view👓 
# Goals Dashboard

```button
name + New Goal
type command
action QuickAdd: Add Goal
```

[[Goals 🎯|🏗️ In Progress]] | [[Goals - Achieved 🎯|🏆 Achieved]] 

## 🏆 Achieved

```dataview
TABLE without ID
	file.link AS "🎯 Goal",
	value as "💎 Value",
	dateformat(completeddate,"d MMMM, yyyy") AS "✅ Completed",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/goal AND "5 Life"
WHERE completeddate != "In Progress"
SORT completeddate DESC, deadline DESC
```
