---
full-date: <% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").endOf('quarter').format('YYYY-MM-DD') %>
quarter: <% tp.date.now("YYYY-[Q]Q", 0, tp.file.title, "YYYY-[Q]Q") %>
year: <% tp.date.now("YYYY", 0, tp.file.title, "YYYY-[Q]Q") %>
banner: "https://preview.redd.it/arqa352ph7x61.jpg?width=960&crop=smart&auto=webp&s=84f9245d607b029667d5bfc4abf36547fc6213de"
---

###### [[<% tp.date.now("YYYY-[Q]Q","P-1M", tp.file.title, "YYYY-[Q]Q") %>|↶ PREVIOUS QUARTER]] ⁝ [[<% tp.date.now("YYYY-[Q]Q", "P1M", tp.file.title, "YYYY-[Q]Q") %>|FOLLOWING QUARTER ↷]]
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
	completeddate >= date("<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").startOf('quarter').format('YYYY-MM-DD') %>") AND
	completeddate <= date("<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").endOf('quarter').format('YYYY-MM-DD') %>")
SORT completeddate ASC, deadline ASC
```

### 🗃️ Monthly Reviews
[[<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").startOf('quarter').format('YYYY-MM') %>]]
💪 `$= dv.page("<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").startOf('quarter').format('YYYY-MM') %>").proud`
📉 `$= dv.page("<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").startOf('quarter').format('YYYY-MM') %>").improve`

[[<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").endOf('quarter').subtract(1, "M").format('YYYY-MM') %>]]
💪 `$= dv.page("<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").endOf('quarter').subtract(1, "M").format('YYYY-MM') %>").proud`
📉 `$= dv.page("<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").endOf('quarter').subtract(1, "M").format('YYYY-MM') %>").improve`

[[<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").endOf('quarter').format('YYYY-MM') %>]]
💪 `$= dv.page("<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").endOf('quarter').format('YYYY-MM') %>").proud`
📉 `$= dv.page("<% moment(tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-[Q]Q"), "YYYY-MM-DD").endOf('quarter').format('YYYY-MM') %>").improve`

### 👓 Quarterly Reflection

>[!question] What went well this quarter?

Proud::

>[!question] What did not go well this quarter?

Improve::

---
## 🔭 Plan
- [ ] Check the upcoming [[Plan - This Year 🔭|goals and milestones]] for the current year
- [ ] Adjust deadline of milestones as needed
- [ ] Add new milestones as needed
