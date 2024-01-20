---
banner_icon: 🔭
cssClass: cards
---
###### [[Home]]
# Plan
[[Plan - This Month 🔭|🏃 This Month ]] | [[Plan - Next Month 🔭|🏃 Next Month ]] |[[Plan - This Quarter 🔭|📅 This Quarter ]] | [[Plan - Next Quarter 🔭|📅 Next Quarter ]] | [[Plan - This Year 🔭|👓 This Year ]] | [[Plan - 1 Year 🔭|👓 1 Year]] | [[Plan - Future 🔭|🔭 Look Ahead]]
## 👓 Next 12 Months
### 🎯 Goals
```dataviewjs
function getMilestonePages(goalName) {
	var files = dv.pages('#life/milestone')
	var goal = dv.page(goalName).file.link
	return files.where(p => String(p.goal) == String(goal))
}

function getMilestonesTotal(milestonePages) {
	return milestonePages.length
}

function getMilestonesDone(milestonePages) {
	return milestonePages.where(p => p.completeddate != "In Progress").length
}

function getProgress(milestonePages) {
	var milestonesTotal = getMilestonesTotal(milestonePages)
	var milestonesDone = getMilestonesDone(milestonePages)
	var progress = Math.round(milestonesDone / milestonesTotal * 100)
	var l = "![progress](https://progress-bar.dev/" + progress + "/)"
	return "<progress value='" + progress + "' max='100'></progress>" + "<br>" + progress + "% completed"
}

let pages = dv.pages('#life/goal and "5 Life"')
	.where(p => p.completeddate == "In Progress")
	.where(p => p.deadline.diffNow('days').days < 366)
	

dv.table(["Banner", "🎯 Goal", "📈 Progress", "🏁 Milestones", "Area", "📆 Deadline"], 
	pages
	    .sort(p => p.deadline, 'asc')
	    .map(p => [
	        p.banner,
	        p.file.link,
	        getProgress(getMilestonePages(p.file.name)),
	        getMilestonesDone(getMilestonePages(p.file.name)) + "/" + getMilestonesTotal(getMilestonePages(p.file.name)) + " Milestones",
	        p.area,
	        p.deadline
	    ])
)

dv.container.classList.add("cards-cols-4")
dv.container.classList.add("cards")
```

### 🏁 Milestones
```dataview
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone AND !"999 Templates"
WHERE
	completeddate = "In Progress" AND
	(deadline - date(today)).days < 366
SORT deadline ASC
```

### 🗂️ Projects
```dataviewjs
const DQL = `
TABLE without ID
	banner,
	file.link AS " 🗂 Name",
	"<progress value='" + (length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100 + "' max='100'></progress>" + "<br>" + round((length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100) + "% completed"
 AS "📈 Progress",
	length(filter(file.tasks.completed, (t) => t = true)) + "/" + length(file.tasks) + " Tasks" AS "✅ Tasks",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #project/personal AND "5 Life" 
WHERE 
	completeddate = "In Progress" AND 
	(deadline - date(today)).days < 366
SORT completeddate ASC, deadline ASC
`

dv.execute(DQL)

dv.container.classList.add("cards")
```
<br>