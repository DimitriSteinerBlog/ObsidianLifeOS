---
banner_icon: 🏁
---
###### [[Home]]
###### tags:: #atlas/view👓 
# Milestones Dashboard
[[Milestones 🏁|🏗️ In Progress]] | [[Milestones - Achieved 🏁|🏆 Achieved]] 
## 🏆 Achieved
```dataview
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	choice(completeddate != "In Progress", "✅ " + completeddate, "In Progress") AS "✅ Completed",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone AND !"999 Templates"
WHERE completeddate != "In Progress"
SORT completeddate ASC, deadline ASC
```