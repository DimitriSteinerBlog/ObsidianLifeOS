---
banner: "https://preview.redd.it/arqa352ph7x61.jpg?width=960&crop=smart&auto=webp&s=84f9245d607b029667d5bfc4abf36547fc6213de"
banner_x: 0.5
---
###### [[Home|Home]]
###### tags:: #atlas/view👓
# Weekly Reviews
```dataviewjs
let groups = dv.pages('"2 Journal/Weekly Review" and !#atlas/view👓').groupBy(p => p.month)

for (let group of groups.sort(g => g.key, 'desc')) { 
	dv.header(2, group.key); 
	dv.table( 
		["📅 Week", "💪 Proud", "↗️ Improve", "🎯 Focus Goals"], 
		group.rows 
			.sort(k => k.month, 'desc')
		    .map(k => [
		        k.file.link,
		        k.proud,
		        k.improve,
		        k.focusgoal
		    ])
	)
}
```
