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
SKU: Blue

Average Qty Ordered: 2053
Standard Deviation: 644 (Average Qty Ordered = 2053+or-644)
Demand Variability: 0.314

Qty on Hand: 1003
Calculated Safety Stock: 1165

Reorder Level: 
RL = Lead_time*Demand+Service_level*Std_Dev*sqrt(Lead_time) why?
Reorder Qty: 


'revenue': '123190000', 'economic_order_quantity': '44', 'economic_order_variable_cost': '15708.41', 'ABC_XYZ_Classification': 'BY', 'excess_stock': '0', 'shortages': '5979','total_orders': '24638'
```

<br>


```

```
