---
full-date: <% tp.date.now("YYYY-MM-DD", 6, tp.file.title, "YYYY-[W]ww") %>
week: <% tp.date.now("YYYY-[W]ww", 0, tp.file.title, "YYYY-[W]ww") %>
month: <% tp.date.now("YYYY-MM MMMM", 0, tp.file.title, "YYYY-[W]ww") %>
year: <% tp.date.now("YYYY", 0, tp.file.title, "YYYY-[W]ww") %>
banner: "https://preview.redd.it/arqa352ph7x61.jpg?width=960&crop=smart&auto=webp&s=84f9245d607b029667d5bfc4abf36547fc6213de"
cssClass: embed-strict
---
###### [[<% tp.date.now("gggg-[W]ww", -7, tp.file.title, "gggg-[W]ww") %>|↶ PREVIOUS WEEK]] ⁝ [[<% tp.date.now("gggg-[W]ww", 7, tp.file.title, "gggg-[W]ww") %>|FOLLOWING WEEK ↷]]
# ◌ <% tp.file.title %>
```dataview
TABLE WITHOUT ID
	file.link as "Day",
	week as "Week"
FROM "2 Journal/Daily Log"
WHERE week = "<% tp.file.title %>"
```
---
# Weekly Review
## Collect
Collect all loose papers, sticky notes etc. and capture them in Obsidian

---
## 🧹 Clear Space
### Physical Space
- [ ] Desk, bag, wallet
- [ ] Office in-tray

### Digital Space
- [ ] Clear E-Mail inbox
- [ ] Clear computer: Desktop, download folder, empty trash
- [ ] Clear smartphone: Whatsapp, pictures, messages
- [ ] Clear Obsidian Inbox

---
## 🗃️ Review
### 📝 Journal
- [[<% tp.date.weekday("YYYY-MM-DD", 0, tp.date.now("YYYY-MM-DD")) %>|Monday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 0, tp.date.now("YYYY-MM-DD")) %>#^life-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 1, tp.date.now("YYYY-MM-DD")) %>|Tuesday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 1, tp.date.now("YYYY-MM-DD")) %>#^life-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 2, tp.date.now("YYYY-MM-DD")) %>|Wednesday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 2, tp.date.now("YYYY-MM-DD")) %>#^life-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 3, tp.date.now("YYYY-MM-DD")) %>|Thursday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 3, tp.date.now("YYYY-MM-DD")) %>#^life-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 4, tp.date.now("YYYY-MM-DD")) %>|Friday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 4, tp.date.now("YYYY-MM-DD")) %>#^life-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 5, tp.date.now("YYYY-MM-DD")) %>|Saturday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 5, tp.date.now("YYYY-MM-DD")) %>#^life-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 6, tp.date.now("YYYY-MM-DD")) %>|Sunday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 6, tp.date.now("YYYY-MM-DD")) %>#^life-link]]
<br>

### 📗 Reading
```dataview
TABLE WITHOUT ID
	file.link as "Day",
	reading as "Log"
FROM "2 Journal/Daily Log"  
WHERE week = this.week
SORT file.name DESC
```
<br>

### 🍽️ Food:
- [[<% tp.date.weekday("YYYY-MM-DD", 0, tp.date.now("YYYY-MM-DD")) %>|Monday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 0, tp.date.now("YYYY-MM-DD")) %>#^food-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 1, tp.date.now("YYYY-MM-DD")) %>|Tuesday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 1, tp.date.now("YYYY-MM-DD")) %>#^food-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 2, tp.date.now("YYYY-MM-DD")) %>|Wednesday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 2, tp.date.now("YYYY-MM-DD")) %>#^food-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 3, tp.date.now("YYYY-MM-DD")) %>|Thursday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 3, tp.date.now("YYYY-MM-DD")) %>#^food-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 4, tp.date.now("YYYY-MM-DD")) %>|Friday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 4, tp.date.now("YYYY-MM-DD")) %>#^food-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 5, tp.date.now("YYYY-MM-DD")) %>|Saturday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 5, tp.date.now("YYYY-MM-DD")) %>#^food-link]]
- [[<% tp.date.weekday("YYYY-MM-DD", 6, tp.date.now("YYYY-MM-DD")) %>|Sunday]]
		![[<% tp.date.weekday("YYYY-MM-DD", 6, tp.date.now("YYYY-MM-DD")) %>#^food-link]]
<br>

### 🔁 Habits
```dataview
TABLE WITHOUT ID
	link(file.name) as "Day",
	choice(read >= 15, "✅ " + read + " min", "❌ " + read + " min") AS "📚 >15 min",
	choice(business >= 30, "✅ " + business + " min", "❌ " + business + " min") AS "💼 >30 min",
	choice(italian >= 10, "✅ " + italian + " min", "❌ " + italian + " min") AS "🇮🇹 >10 min",
	choice(phone <= 120, "✅ " + phone + " min", "❌ " + phone + " min") AS "📱 < 120 min",
	choice(exercise >= 5, "✅ " + exercise + " min", "❌ " + exercise + " min") AS "🏋️ >5 min",
	choice(water >= 1.5, "✅ " + water + " l", "❌ " + water + " l") AS "💧 >1.5l",
	choice(sleep >= 6, "✅ " + sleep + " h", "❌ " + sleep + " h") AS "💤 >6h",
	choice(veggies >= 200, "✅ " + veggies + " g", "❌ " + veggies + " g") AS "🥦 >200g",
	choice(fruits >=1, "✅ " + fruits + " pcs", "❌ " + fruits + " pcs") AS "🍎 >1pcs"
FROM "2 Journal/Daily Log"
WHERE week = this.week
SORT file.name DESC
```
<br>

### 📓 New Notes
```dataview
TABLE WITHOUT ID
	file.link,
	file.cday as "Date Created"
WHERE file.cday <= date("<% tp.date.now('YYYY-MM-DD') %>") AND file.cday > date("<% tp.date.now('YYYY-MM-DD', -7, tp.date.now('YYYY-MM-DD'), 'YYYY-MM-DD') %>")
SORT file.cday DESC
```
---
## 👓 Reflect
### 🏆 Milestones Achieved
```dataview
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	choice(completeddate != "In Progress", "✅ " + completeddate, "In Progress") AS "✅ Completed",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone AND !"999 Templates"
WHERE 
	completeddate != "In Progress" AND
	completeddate < this.full-date AND
	(this.full-date - completeddate).days < 7
SORT completeddate ASC, deadline ASC
```
<br>

### ✅ Tasks Completed
```tasks
done
done before <% tp.date.now("YYYY-MM-DD", 7, tp.file.title, "YYYY-[W]ww") %>
done after <% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-[W]ww") %>
path includes 5 Life
short mode
```
<br>
### 👓 Weekly Reflection

>[!question] What went well this week?

Proud::

>[!question] What did not go well this week?

Improve::

---
## 🔭 Plan
- [ ] Check calendar next 2-3 weeks

###  🎯 Focus Goals
#### This Month
```dataview
TABLE without ID
	file.link AS "🏁 Milestone",
	goal as "🎯 Goal",
	dateformat(deadline,"d MMMM, yyyy") AS "📅 Deadline"
FROM #life/milestone AND !"999 Templates"
WHERE
	completeddate = "In Progress" AND
	deadline.year = date(this.full-date).year AND
	deadline.month <= date(this.full-date).month
SORT deadline ASC
```
<br>

#### This Week
```dataview
TABLE WITHOUT ID
	file.link AS "Week",
	focusgoal AS "🎯 Goals"
FROM "2 Journal/Weekly Review"
WHERE week = "<% tp.date.now("YYYY-[W]ww", -7, tp.file.title, "YYYY-[W]ww") %>"
```
<br>

#### Upcoming Week
- [ ] Define focus goals for next week
	- FocusGoal::
	- FocusGoal::
	- FocusGoal::
	- FocusGoal::
	- FocusGoal::
- [ ] Check overdue and unplanned [[Tasks ✔️|tasks]] and schedule them for the upcoming week
