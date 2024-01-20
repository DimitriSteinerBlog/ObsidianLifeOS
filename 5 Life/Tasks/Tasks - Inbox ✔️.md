---
banner_icon: ✔️
---
###### [[Home]]
###### tags:: #atlas/view👓
# Tasks Dashboard
[[Tasks ✔️|🏁 Today]] | [[Tasks - Overdue ✔️|⚠️ Overdue]] | [[Tasks - Upcoming ✔️|➡️ Upcoming]] | [[Tasks - Inbox ✔️|📥 Inbox]] | [[Tasks - Calendar ✔️|📅 Calendar]] | [[Tasks - Timeline ✔️|⏳ Timeline]]
## 📥 Inbox
```dataviewjs
//exclude projects which don't have the status "active"
let excluded = '(' + dv.pagePaths('#project/personal AND "5 Life"')
  .where(p => dv.page(p).status != "active")
  .array()
  .map(x => 'path does not include ' + x)
  .join(') AND (') + ')'

if (excluded == '()') {
	excluded = ''
}

const query = `
not done
no due date
short mode
group by function task.file.folder.split('/').slice(-3).reverse().pop()
group by filename
path includes 5 Life
path does not include Projects - KanBan 🗂️
path does not include Literature - KanBan 📚
path does not include Blog - KanBan 🌐
${excluded}`

dv.paragraph('```tasks\n' + query + '\n```')
```