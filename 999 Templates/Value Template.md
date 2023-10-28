---
banner_icon: 💎
---

###### [[Values]]
###### tags:: #life/value
# {{title}}

Why:: 

## 🎯 Related Goals
```dataview
TABLE WITHOUT ID
	file.link as "🎯 Goal",
	choice(completeddate = "In Progress", "🏗️", "✅") AS "✅ Completed",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/goal AND "5 Life"
WHERE value = [[<% tp.file.title %>]]
SORT complete DESC, deadline ASC
```