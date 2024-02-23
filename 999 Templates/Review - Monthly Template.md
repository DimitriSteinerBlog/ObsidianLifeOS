---
full-date: <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-MM") %>
month: <% tp.date.now("YYYY-MM MMMM", 0, tp.file.title, "YYYY-MM") %>
year: <% tp.date.now("YYYY", 0, tp.file.title, "YYYY-MM") %>
banner: "https://preview.redd.it/arqa352ph7x61.jpg?width=960&crop=smart&auto=webp&s=84f9245d607b029667d5bfc4abf36547fc6213de"
---

###### [[<% tp.date.now("YYYY-MM","P-1M", tp.file.title, "YYYY-MM") %>|↶ PREVIOUS MONTH]] ⁝ [[<% tp.date.now("YYYY-MM", "P1M", tp.file.title, "YYYY-MM") %>|FOLLOWING MONTH ↷]]
# ◌ <% tp.file.title %>
## 👓 Reflect
### 🏆 Goals/Milestones Achieved
```dataview
TABLE without ID
	file.link AS "🏁 Goal/Milestone",
	replace(tags, "#life/", "") as "🎯 Type",
	"✅ " + completeddate AS "✅ Completed",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM (#life/goal OR #life/milestone) AND "5 Life" AND !"999 Templates"
WHERE 
	completeddate != "In Progress" AND
	completeddate.month = this.full-date.month AND
	completeddate.year = this.full-date.year
SORT completeddate ASC, deadline ASC
```

### 🔄 Habits
- [ ] Review [[Habit Tracker 🔁|Habits]]
	- [ ] Adjust cues/rewards for habits with bad progress

### 🗃️ Weekly Reviews
- [ ] Review [[Weekly Review 📑|Weeklies]]

### 👓 Monthly Reflection

>[!question] What went well this month?

Proud::

>[!question] What did not go well this month?

Improve::

---
## 🔭 Plan
- [ ] Check the upcoming [[Plan - This Quarter 🔭|goals and milestones]] for the current quarter
- [ ] Adjust deadline of projects as needed
- [ ] Add new projects as needed
- [ ] Adjust the [[Projects - KanBan 🗂️|status of projects]] as needed
