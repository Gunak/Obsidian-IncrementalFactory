<%*
// 1. Data Collection Prompts
let name = await tp.system.prompt("1. What resource is this?");
let building = await tp.system.prompt("2. Produced in which Building?", "Assembler");

// Building Cost Prompts
let costRes1 = await tp.system.prompt("3a. Building Cost: Resource 1 Name");
let costAmt1 = await tp.system.prompt("3b. Building Cost: Resource 1 Amount", "0");
let costRes2 = await tp.system.prompt("3c. Building Cost: Resource 2 Name");
let costAmt2 = await tp.system.prompt("3d. Building Cost: Resource 2 Amount", "0");

// Input Prompts
let in1 = await tp.system.prompt("4a. Input 1 Name");
let qty1 = await tp.system.prompt("4b. Input 1 Qty", "0");
let in2 = await tp.system.prompt("4c. Input 2 Name");
let qty2 = await tp.system.prompt("4d. Input 2 Qty", "0");
let in3 = await tp.system.prompt("4e. Input 3 Name");
let qty3 = await tp.system.prompt("4f. Input 3 Qty", "0");

let energy = await tp.system.prompt("5. Energy required per tick?", "0");
let yieldQty = await tp.system.prompt("6. Quantity produced per tick?", "1");

// 2. Rename the file
await tp.file.rename(name);
%>---
type: resource
produced_at: "[[<% building %>]]"
science_type: 
tags: [resource]
---
# 📦 <% name %>

### 🏭 Production Specs
- **Building**: [[<% building %>]]
- **Yield**: <% yieldQty %> /t
- **Energy Req**: <% energy %> E/t

### 🛠️ Construction Cost
- **Cost 1**: [[<% costRes1 %>]] x<% costAmt1 %>
- **Cost 2**: [[<% costRes2 %>]] x<% costAmt2 %>

### 📥 Inputs (per tick)
- [input_1:: [[<% in1 %>]]] | **Qty**: [qty_1:: <% qty1 %>]
- [input_2:: [[<% in2 %>]]] | **Qty**: [qty_2:: <% qty2 %>]
- [input_3:: [[<% in3 %>]]] | **Qty**: [qty_3:: <% qty3 %>]

---

### 🔄 Downstream Recipes
```dataview
LIST FROM #resource 
WHERE (contains(input_1, [[<% name %>]]) OR contains(input_2, [[<% name %>]]) OR contains(input_3, [[<% name %>]]))
AND file.name != this.file.name