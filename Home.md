---
cssclass: dashboard
banner: "![[home-banner.jpg]]"
banner_icon: 🌍
---
<br>

# Life
- ## ⭐ Quick Links
	- [[Areas 🗃️|🗃️ Areas]] 
	- [[Recipes MOC|🍳 Recipes]]
	- [[People MOC 👤|👤 People]]
	- [[Technology MOC 💻|💻Technology]]
- ## 🔨 Productivity Hub
	- [[Goals 🎯|🎯 Goals]] 
	- [[Milestones 🏁|🏁 Milestones]]
	- [[Projects 🗂️|🗂️ Projects]]
	- [[Tasks - Timeline ✔️|✅ Tasks]]  
- ## 👓 Review & Plan
	- [[Weekly Review 📑|📑 Weekly Reviews]] 
	- [[Monthly Review 📆|📅 Monthly Reviews]] 
	- [[Values 💎|💎 Values]] 
	- [[Plan - This Quarter 🔭|🔭 Plan]]

 # PKM
- ## 📝 Notemaking
	- [[Literature 📚|📚 Literature]] 
	- [[Cooling Pod ❄️|🥶 Cooling Pod]] 
	- [[Notebox 📝|📝 Notebox]]
 - ## 🧠 Knowledge
	- [[MOC Library 📚|📚 MOC Library]]
	- [[Mental Models MOC 🧠|🧠 Mental Models]]

# Vault Info
- ## 🗄️ Recent Files
 `$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(3).file.link)`
- ## 〽️ Stats
	-  🗃️ File Count: `$=dv.pages().length`
	-  📗 Books: `$=dv.pages('#sources/book AND !"999 Templates"').length`
	-  🍳 Recipes: `$=dv.pages('#topic/cooking/recipe AND !"999 Templates"').length`