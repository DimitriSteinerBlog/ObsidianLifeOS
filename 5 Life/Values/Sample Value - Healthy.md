---
banner_icon: 💎
---
###### [[Values]]
###### tags:: #life/value
# Sample Value - Healthy

Why:: To live a long life

## 🎯 Related Goals
```dataview
TABLE WITHOUT ID
	file.link as "🎯 Goal",
	choice(completeddate = "In Progress", "🏗️", "✅") AS "✅ Completed",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/goal AND "5 Life"
WHERE value = [[Sample Value - Healthy]]
SORT complete DESC, deadline ASC
```