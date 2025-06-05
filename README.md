# Khushmart-shrinkage-db
A database solution to help a retail chain monitor, analyze, and control inventory shrinkage under 1.5% of total sales.

Organization overview 
**organization:**  Khush Mart (Hypothetical Retail chain)
**Industry:** Retail
**Focus area:** Inventory management and shrinkage prevention

Mission and challenge: 
**Mission:** 
Reduce inventory losses using a smart, centralized database system.
**Challenge:** 
retail shrinkage caused by theft, damage, and data entry errors was reducing profitability and accuracy.

Objective:
Khush-mart aims to **reduce shrinkage to less than 1.5% of total sales volume** through efficient tracking and data monitoring.

---

## 🧱 Entity Identification

- `EMPLOYEE_TABLE`
- `PRODUCT_TABLE`
- `CUSTOMER_TABLE`
- `SUPPLIER_TABLE`
- `SALES_TABLE`
- `INVENTORY_TABLE`
- `THEFT_CASES`
- `PRODUCT_RETURNS`

---

## 🔗 Entity Relationship Diagram (ERD)

📎 *See `ERD.png` in the repository (upload in Step 3)*

---

## 📂 Table Structures

| Table Name         | Fields |
|--------------------|--------|
| EMPLOYEE_TABLE     | EmployeeID, Name, Role, StoreID |
| PRODUCT_TABLE      | ProductID, Name, Category, SupplierID, Price |
| SUPPLIER_TABLE     | SupplierID, Name, Contact |
| SALES_TABLE        | SaleID, ProductID, QuantitySold, SaleDate |
| INVENTORY_TABLE    | InventoryID, ProductID, StoreID, QuantityOnHand |
| THEFT_CASES        | CaseID, ProductID, EmployeeID, Date, LossQuantity, Description |
| PRODUCT_RETURNS    | ReturnID, ProductID, Date, Reason, Quantity |

---

## 💡 Sample SQL View

```sql
Shrinkage Report View
CREATE VIEW shrinkage_summary AS
SELECT 
    p.ProductID,
    p.Name,
    (i.QuantityOnHand - s.QuantitySold) AS LostUnits,
    ((i.QuantityOnHand - s.QuantitySold) * 100.0 / i.QuantityOnHand) AS ShrinkagePercent
FROM 
    INVENTORY_TABLE i
JOIN 
    SALES_TABLE s ON i.ProductID = s.ProductID
JOIN 
    PRODUCT_TABLE p ON p.ProductID = i.ProductID;

## 📑 Documentation & Assumptions

- Shrinkage includes only theft, damage, and inventory errors  
- Loss prevention actions (e.g., CCTV) are not tracked  
- All field names are descriptive and user-friendly  
- Inventory updates are not real-time  

---

## ⚠️ Limitations

- No POS or live scanning integration  
- Loss prevention cost tracking not included  
- Assumes accurate and timely reporting by employees 

## 🤝 Author
- Meet Chirag

---

## 📎 Project Files

📊 [Download Full Presentation (PPTX)](./database%20design%20khushmart%20shrinkage%20for%20github.pptx)  
🖼️ [View Entity Relationship Diagram (JPG)](./entity%20relationships%20diagram.jpg)

## 🔗 Entity Relationship Diagram (ERD)

🖼️ [Click to view the ERD](./entity%20relationships%20diagram.jpg)


