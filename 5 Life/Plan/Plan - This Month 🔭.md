---
banner_icon: 🔭
cssClass: cards
---
###### [[Home]]
# Plan
[[Plan - This Month 🔭|🏃 This Month ]] | [[Plan - Next Month 🔭|🏃 Next Month ]] |[[Plan - This Quarter 🔭|📅 This Quarter ]] | [[Plan - Next Quarter 🔭|📅 Next Quarter ]] | [[Plan - This Year 🔭|👓 This Year ]] | [[Plan - 1 Year 🔭|👓 1 Year]] | [[Plan - Future 🔭|🔭 Look Ahead]]
## 🏃 This Month
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
	.where(p => p.deadline <= moment().endOf('month'))
	

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

dv.container.classList.add("cards")
```

### 🏁 Milestones
```dataviewjs
//get the beginning and the end of the month
const endQuarter = moment().endOf('month').format('YYYY-MM-DD')
const startQuarter = moment().startOf('month').format('YYYY-MM-DD')

const query = `
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone AND !"999 Templates"
WHERE
	completeddate = "In Progress" AND
	deadline <= date(${endQuarter}) AND
	deadline >= date(${startQuarter})
SORT deadline ASC
`

dv.paragraph('```dataview\n' + query + '\n```')
```

### 🗂️ Projects
```dataviewjs
//get the beginning and the end of the quarter
const endQuarter = moment().endOf('month').format('YYYY-MM-DD')
const startQuarter = moment().startOf('month').format('YYYY-MM-DD')

const query = `
TABLE without ID
	banner,
	file.link AS " 🗂 Name",
	"<progress value='" + (length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100 + "' max='100'></progress>" + "<br>" + round((length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100) + "% completed"
 AS "📈 Progress",
	length(filter(file.tasks.completed, (t) => t = true)) + "/" + length(file.tasks) + " Tasks" AS "✅ Tasks",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM (#project/personal OR #blog/article) AND "5 Life" 
WHERE 
	(completeddate = "In Progress" OR status = "In Progress") AND 
	deadline <= date(${endQuarter}) AND
	deadline >= date(${startQuarter})
SORT completeddate ASC, deadline ASC
`

dv.paragraph('```dataview\n' + query + '\n```')
```
<br>