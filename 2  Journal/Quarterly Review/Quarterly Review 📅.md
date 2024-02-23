---
banner: "https://preview.redd.it/arqa352ph7x61.jpg?width=960&crop=smart&auto=webp&s=84f9245d607b029667d5bfc4abf36547fc6213de"
banner_x: 0.5
---
###### [[Home|Home]]
###### tags:: #atlas/view👓
# Quarterly Reviews
```button
name + New Quarterly Review
type command
action QuickAdd: Add Quarterly Review
```

```dataviewjs
let groups = dv.pages('"2 Journal/Quarterly Review" and !#atlas/view👓').groupBy(p => p.year)

for (let group of groups.sort(g => g.key, 'desc')) { 
	dv.header(2, group.key); 
	dv.table( 
		["📅 Quarter", "💪 Proud", "↗️ Improve"], 
		group.rows 
			.sort(k => k.quarter, 'desc')
		    .map(k => [
		        k.file.link,
		        k.proud,
		        k.improve
		    ])
	)
}
```
