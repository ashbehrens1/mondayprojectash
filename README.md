# 🚀 Project: Solving the Nexus Strategy Data Mess

### **The Strategy: Fixing a Broken Data Structure**
The original data from Nexus was a flat Smartsheet file that was a bit of a nightmare to manage. It repeated the total project budget on every single task line, which made their financial reporting look completely wrong. 

**My goal was to move them into a "Parent-Child" setup on monday.com:**
* **Engagements Board:** For big-picture executive oversight.
* **Deliverables Board:** For day-to-day task management.

---

### **Technical Solutions & Execution**
To ensure a high-fidelity migration, I bypassed manual entry in favor of a custom-built automation stack:

* **Cleaning it up:** I used a **Python (Pandas)** script to deduplicate the data so each project was only created once with its actual budget (**$820k total**), rather than being multiplied across 27 rows.
* **The "ID Handshake":** Because I wanted these boards to be linked, I had to be smart with the API. My script created the tasks first, saved their unique IDs, and then went back to link them to the main project so the relationship was rock-solid.
* **API Respect:** I added "sleep" timers in my code so I didn't hit the monday.com servers too hard and get blocked during the migration.

---

### **The Vision: What Happens After Launch**
I didn't just want to dump data; I wanted to build a system that grows with the team:

* **Automated Roll-ups:** I am planning automations where the main project status automatically flips to "Done" as soon as the last task is finished.
* **Better Dashboards:** I set up **Mirror Columns** so the leadership team can see exactly how many hours are being spent on a project in real-time without ever clicking into the task board.
* **Team Capacity:** I want to use the **Workload View** to help managers see if anyone is overwhelmed with too many hours.

---

### **Technical Discoveries & "A-ha" Moments**
While building this, I ran into a few things that showed me where we can take this next:

* **The Validation Bug:** I built a script to verify all 27 items were linked. It worked visually, but I hit a weird JSON parsing error when trying to read the links back through the API. I’d want to sync with a senior engineer to see if we can optimize those **GraphQL fragments**.
* **UI Gaps:** I noticed the native boards don't do "heatmapping" (color gradients) for numbers like budgets. This is a perfect excuse to build a **Custom App with the monday SDK** to give the client that extra visual polish.

---

### **My Professional Stack**
I used a mix of traditional coding and modern AI to move fast:

* **The Core:** Python and the Pandas library for the data heavy lifting.
* **The Lab:** The **monday.com API Playground** to "X-ray" the board structure and test my queries.
* **AI Orchestration:** I used **Gemini** for the initial architecture, **Claude** to help debug the tricky bidirectional linking logic, and **Perplexity** to stay on top of the latest API documentation.
