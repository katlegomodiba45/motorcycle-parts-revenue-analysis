# Wholesale Revenue Analysis - Motorcycle Parts Distributor

### Business Problem
A wholesale motorcycle parts company needed to know which product lines and warehouses make the most net revenue after payment fees.

### Dataset
5000+ transactions: product_line, warehouse, date, total, payment_fee  
Source: DataCamp Advanced SQL track - all analysis and insights are my own

### SQL Solution
SELECT
  product_line,
  CASE 
    WHEN EXTRACT(MONTH FROM date) = 6 THEN 'June'
    WHEN EXTRACT(MONTH FROM date) = 7 THEN 'July'
    WHEN EXTRACT(MONTH FROM date) = 8 THEN 'August'
  END AS month,
  warehouse,
  SUM(total) - SUM(payment_fee) AS net_revenue
FROM sales
WHERE client_type = 'Wholesale'
GROUP BY product_line, month, warehouse
ORDER BY product_line, month, warehouse;
### Key Finding
Central warehouse had highest net revenue in July for Miscellaneous parts.

### Recommendation
Increase Q3 inventory to Central warehouse and review payment fees.

### Author
Katlego Modiba | Aspiring Data Analyst | AWS Certified | SQL, Python | Mahikeng, SA
