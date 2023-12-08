---
banner_icon: 🏁
---
###### [[Home]]
###### tags:: #atlas/view👓 
# Milestones Dashboard
[[Milestones 🏁|🏗️ In Progress]] | [[Milestones - Achieved 🏁|🏆 Achieved]] 
## 🏗️ In Progress
### This Month
```dataview
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone AND !"999 Templates"
WHERE
	completeddate = "In Progress" AND
	deadline.year = date(today).year AND
	deadline.month <= date(today).month
SORT deadline ASC
```

### This Year
```dataview
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone AND !"999 Templates"
WHERE
	completeddate = "In Progress" AND
	deadline.year = date(today).year AND
	deadline.month > date(today).month
SORT deadline ASC
```

### Short-Term (1-2 Years)
```dataview
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone AND !"999 Templates"
WHERE
	completeddate = "In Progress" AND
	deadline.year > date(today).year AND
	(deadline - date(today)).days < 730
SORT deadline ASC
```

### Medium-Term (3-5 Years)
```dataview
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone AND !"999 Templates"
WHERE
	completeddate = "In Progress" AND
	(deadline - date(today)).days >= 730 AND 
	(deadline - date(today)).days < 1825
SORT deadline ASC
```

### Long-Term (5+ Years)
```dataview
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone AND !"999 Templates"
WHERE
	completeddate = "In Progress" AND
	(deadline - date(today)).days >= 1825
SORT deadline ASC
```