---
year: <% tp.date.now("YYYY", 0, tp.file.title, "YYYY-[Q]Q") %>
banner: "https://preview.redd.it/arqa352ph7x61.jpg?width=960&crop=smart&auto=webp&s=84f9245d607b029667d5bfc4abf36547fc6213de"
---

###### [[<% tp.date.now("YYYY","P-1Y", tp.file.title, "YYYY") %>|↶ PREVIOUS YEAR]] ⁝ [[<% tp.date.now("YYYY", "P1Y", tp.file.title, "YYYY") %>|FOLLOWING YEAR ↷]]
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
	completeddate.year = this.year
SORT completeddate ASC, deadline ASC
```

### 🗃️ Quarterly Reviews
[[<% tp.date.now("YYYY-[Q1]", 0, tp.file.title, "YYYY-[Q]Q") %>]]
💪 `$= dv.page("<% tp.date.now("YYYY-[Q1]", 0, tp.file.title, "YYYY-[Q]Q") %>").proud`
📉 `$= dv.page("<% tp.date.now("YYYY-[Q1]", 0, tp.file.title, "YYYY-[Q]Q") %>").improve`

[[<% tp.date.now("YYYY-[Q2]", 0, tp.file.title, "YYYY-[Q]Q") %>]]
💪 `$= dv.page("<% tp.date.now("YYYY-[Q2]", 0, tp.file.title, "YYYY-[Q]Q") %>").proud`
📉 `$= dv.page("<% tp.date.now("YYYY-[Q2]", 0, tp.file.title, "YYYY-[Q]Q") %>").improve`

[[<% tp.date.now("YYYY-[Q3]", 0, tp.file.title, "YYYY-[Q]Q") %>]]
💪 `$= dv.page("<% tp.date.now("YYYY-[Q3]", 0, tp.file.title, "YYYY-[Q]Q") %>").proud`
📉 `$= dv.page("<% tp.date.now("YYYY-[Q3]", 0, tp.file.title, "YYYY-[Q]Q") %>").improve`

[[<% tp.date.now("YYYY-[Q4]", 0, tp.file.title, "YYYY-[Q]Q") %>]]
💪 `$= dv.page("<% tp.date.now("YYYY-[Q4]", 0, tp.file.title, "YYYY-[Q]Q") %>").proud`
📉 `$= dv.page("<% tp.date.now("YYYY-[Q4]", 0, tp.file.title, "YYYY-[Q]Q") %>").improve`

### 👓 Annual Reflection

>[!question] What went well this year?

Proud::

>[!question] What did not go well this year?

Improve::

---
## 🔭 Plan
- [ ] Check the upcoming [[Plan - Future 🔭]] for the next few years
- [ ] Add new goals as needed
- [ ] Choose goals for the next year
- [ ] Add milestones to chosen goals and adjust deadlines
- [ ] Add projects to chosen milestones and adjust deadlines
