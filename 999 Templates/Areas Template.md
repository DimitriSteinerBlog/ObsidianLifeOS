---
banner: "![[areas-banner.jpg]]"
cssClass: cards, cards-cols-4
---
###### [[Areas 🗃️|Areas]]
###### tags:: #life/area 
# <% tp.file.title %>
## 🎯 Goals
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

let pages = dv.pages('#life/goal and "5 Life"').where(p => String(p.area) == String(dv.current().file.link))

dv.table(["Banner", "🎯 Goal", "📈 Progress", "🏁 Milestones", "📆 Deadline"], 
	pages
	    .sort(p => p.deadline, 'asc')
	    .map(p => [
	        p.banner,
	        p.file.link,
	        getProgress(getMilestonePages(p.file.name)),
	        getMilestonesDone(getMilestonePages(p.file.name)) + "/" + getMilestonesTotal(getMilestonePages(p.file.name)) + " Milestones",
	        p.deadline
	    ])
)
```

## 🗂️ Projects
```dataview
TABLE without ID
	banner,
	file.link AS " 🗂 Name",
	"<progress value='" + (length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100 + "' max='100'></progress>" + "<br>" + round((length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100) + "% completed"
 AS "📈 Progress",
	length(filter(file.tasks.completed, (t) => t = true)) + "/" + length(file.tasks) + " Tasks" AS "✅ Tasks",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #project/personal AND "5 Life" 
WHERE area = this.file.link
SORT completeddate ASC, deadline ASC
```