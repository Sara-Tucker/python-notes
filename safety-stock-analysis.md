# Safety Stock Analysis

<br>

### Dataset format:
- SKU = color
- Month = qty ordered

Sku | mar | apr | may | jun | jul | aug | unit cost | lead-time | retail_price | qty_on_hand | backlog
--- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ---
Blue | 2665 | 1841 | 1231 | 2598 | 1988 | 1988 | 1001 | 2 | 5000 | 1003 | 10

<br>

[Full dataset example of 40 SKUs](https://github.com/KevinFasusi/supplychainpy/blob/master/supplychainpy/sample_data/complete_dataset_small.csv)

<br>
<br>

## Example Analysis
```
SKU: KR202-209

Average Qty Ordered: 2053  
Standard Deviation: 644 (Average Qty Ordered = 2053+or-644)  
Demand Variability: 0.314

Qty on Hand: 1003  
Calculated Safety Stock: 1165

Reorder Level:  
Reorder Qty: 
ReLev = Lead_time\*Demand+Service_level\*Std_Dev\*sqrt(Lead_time) - think this got messed up

Economic Order Qty: 44  
Economic Order Variable Cost: $15,708

ABC XYZ Classification: BY
(Medium consumption value. Predictably variable demand. Less reliable forecasts.)

Excess stock: 0  
Shortage units: 5979

Total Qty Ordered: 24,638  
Revenue: $123,190
```

<br>

```
Revenue Rank: 19/40  
Excess Rank: 6/40  
Shortage Rank: 15/40  
Safety Stock Rank: 29/40  
Unit Cost Rank: 21/40

Min Ordered Month: 731  
Max Ordered Month: 2927  
Inventory Turns: 24  
Inventory Traffic Light: Green (inventory to cover demand for next 7 days and up to safety stock)
```
