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

## 🏗️ In Progress
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

let pages = dv.pages('#life/goal and "5 Life"').where(p => p.completeddate == "In Progress")

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
dv.container.classList.add("cards-align-bottom")
```
 
## 🏆 Last 10 Milestones
```dataview
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	dateformat(completeddate,"d MMMM, yyyy") AS "✅ Completed",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone 
WHERE completeddate != "In Progress"
SORT completeddate DESC, deadline DESC
LIMIT 10
```
