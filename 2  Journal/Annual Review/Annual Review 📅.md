---
banner: "https://preview.redd.it/arqa352ph7x61.jpg?width=960&crop=smart&auto=webp&s=84f9245d607b029667d5bfc4abf36547fc6213de"
banner_x: 0.5
---
###### [[Home|Home]]
###### tags:: #atlas/view👓
# Annual Reviews
```button
name + New Annual Review
type command
action QuickAdd: Add Annual Review
```

```dataviewjs
let groups = dv.pages('"2 Journal/Annual Review" and !#atlas/view👓').groupBy(p => p.year)

for (let group of groups.sort(g => g.key, 'desc')) { 
	dv.header(2, group.key); 
	dv.table( 
		["📅 Year", "💪 Proud", "↗️ Improve"], 
		group.rows 
			.sort(k => k.year, 'desc')
		    .map(k => [
		        k.file.link,
		        k.proud,
		        k.improve
		    ])
	)
}
```
