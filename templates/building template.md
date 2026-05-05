<%
let building = await tp.system.prompt("What is the name of the building?");
await tp.file.rename(building)
%>---
type: building
produces: 
science: 
tags: 
  - 
---

# <% building %>

### 🛠️ Construction Cost
- **Cost 1: ** 
- **Cost 2: **


### Resource Input
- [[Energy]] x __
- [[Resource_Input]] x Quantity
- [[Resource_Input]] x Quantity


### Resource Output
- [[Resource_Output]] x 1