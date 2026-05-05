# 🏭 Incremental Factory Dashboard

## 📋 Resource Master List
```dataview 
TABLE produced_at AS "Building", yield_per_t AS "Yield/t", energy_per_t AS "Energy/t", (qty_1 + " " + input_1) AS "Input 1", (qty_2 + " " + input_2) AS "Input 2", (qty_3 + " " + input_3) AS "Input 3", build_cost AS "Build Cost" FROM #resource WHERE type = "resource" SORT file.name ASC
```

