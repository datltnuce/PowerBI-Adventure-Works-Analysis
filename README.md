# 📊 Adventure Works Analysis  
Author: Dat Le Tien  
Date: 2025-02-15  
Tools Used: Power BI 

---

## 📑 Table of Contents  
1. [📌 Background & Overview](#-background--overview)  
2. [📂 Dataset](#-dataset)  
3. [🧠 Design Thinking Process](#-design-thinking-process)  
4. [📊 Key Insights & Visualizations](#-key-insights--visualizations)  

---

## 📌 Background & Overview  

### Objective:
### 📖 What is this project about? 

To monitor and optimize the manufacturing process by tracking production timelines, quality control, and inventory management, ensuring efficient operations and high-quality output.

### 👤 Who is this project for?  

✔️ Product Manager<br>
✔️ Operations Team<br>
✔️ Quality Control Team

### ❓Business Questions:  

✔️ Are production timelines aligning with planned schedules?<br>
✔️ What percentage of products fail quality checks, and what are the main defect causes?<br>
✔️ What is the inventory level of finished goods across different locations?<br>
✔️ How can we optimize production and minimize waste to improve efficiency?<br>

### 🎯Project Outcome:  

✔️ Enhanced quality control by reducing defective items.<br>
✔️ Better inventory management for smooth distribution.<br>
✔️ Data-driven decision-making for optimizing operations and cost savings.  

---

## 📂 Dataset 
 
Dataset: adventureworks2019 (public Google BigQuery dataset)

Dataset dictionary: AdventureWorks _ Data Dictionary

Dataset access:

- Log in to your Google Cloud Platform account and create a new project.<br>
- Navigate to the BigQuery console and select your newly created project.<br>
- In the navigation panel, select "Add Data" and then "Star a project by name".

---

## 🧠 Design Thinking Process
### 1️⃣ Empathize
| 5W1H                                                          |                                           |
| ------------------------------------------------------------------ |--------------------------------------------- |
| Who will be viewing this Dashboard?                                | Product manager<br> |
| If we had to choose only one key Stakeholder, who would it be?<br> | Product manager |
| What problem does this Dashboard solve?                            | Observe whetther production time is in accordance with the planned time<br>Minimize scrapped products.<br> |
| Describe the problem in one sentence                               | Manufacturing needs to track the quantity of scrapped products and the delivery time of products to ensure there are enough goods for distribution as well as to minimize the costs associated with scrapped products<br> |
| When and where will Stakeholders view this Dashboard?<br>          | Weekly, monthly<br> |
| Why do stakeholders need this Dashboard?<br><br>                   | Ensure that the company always has enough products to supply to customers<br>Improve the production process to minimize costs related to scrapped goods|
| How have stakeholders been achieving their goals so far?           | Improve the production process<br>Apply modern technology and machinery |


|Stakeholder Empathy Mapping                                                         |                                                          |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pains                                                      | Find out the cause of scrapped products and delays.                                                      |
| Thinking and feeling                                       |The production process needs to be improved         |
| Seeing                                                    | Production process is inefficient.                                        |
| Saying and doing                                          | Track production progress for each product, at each location<br>Track the amount of scrapped goods over time for each item, try to find out the reason behinds |
| Gains                                                     | Improving production processes will likely increase profits through increased sales and reduced production costs                            |


| Fact table<br>                        | Dim table<br>                                                 |
| -------------------------------------- | -------------------------------------------------------------- |
| Production_WorkOrder, Product_Product | Dim_date, Product_Inventory, Product_ProductTable, Production_BillofMaterials, Production_Location, Production_ScrapReason, Production_WorkOrderRouting |

### 2️⃣ Define point of view

|                            | NORTHSTAR METRIC                         |
|----------------------------|--------------------------------------|
| **What VALUE you want to measure?** | Delivery Success Rate                              |
| **WHEN the value DELIVERY SUCCESS?** |When orders are delivered on time, in full quantity, and meet quality standards. |
| **Northstar Metric Name**  | Delivery Success Rate                              |
| **WHY do you choose this metric?** | This is a composite indicator reflecting the overall efficiency of all three aspects: production (Completion Rate), inventory (Safety Stock Level Rate), and quality (Pass Rate). "Delivery Success Rate" measures the ability to deliver on time, in sufficient quantity, and with assured quality, which is the ultimate goal for all production and supply chain activities. |


Dimension Group
| Group 1 | Group 2  | Group 3 |
| ------- | -------- | ------- |
| Overview | Inventory analysis | Manufacturing Quality analysis |

Define Point of View
| View                     | Description                                                                                       | Why                                                                                                                     |
|--------------------------|---------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| View 1         | To provide a high-level summary of production performance, order completion, and key metrics. | Allow senior management and stakeholders to quickly grasp an overall picture of operations, including total orders, on-time completion rate, and actual costs. It helps in making strategic decisions without delving into detailed data.    |
| View 2 | To analyze and monitor inventory levels, safety stock compliance, and product availability.     | Focus on ensuring inventory is maintained at a safe level, avoiding shortages or overstock situations. It supports supply chain and warehouse management teams in optimizing inventory to meet demand without causing waste. |
| View 3 | To evaluate production quality, defect rates, and reasons for scrapped products.    | Design for the quality management team to analyze issues related to defective products, pass rates, and root causes of scrapped items. It helps improve production processes and ensures product quality meets required standards. |
### 3️⃣ Ideate 
Brainstorming
| Idea Name               | Layer 0 Dimension: Total Metrics              | Layer 1 Dimension: Breakdown by 1 Dimension                                   | Layer 2 Dimension: Breakdown by 2 Dimensions                                           |
|-------------------------|-----------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| View 1       | Total Orders, Total Produced, Total Actual Cost | Total Produced by Year, Quarter and Month, Completion Rate, Total Orders by Subcategory, Product Performance |Total Produced by Year, Quarter and Month          |
| View 2| Total Inventory, Safety Stocked Products, Unsafe Stocked Products                  | Available Quantity by  Date, Proportion Comparison, Safety Status by Product Name, Available Quantity by Category |                  |
| View 3| Total Scrapped Quantity, Avg Production Time (days), Defect Rate(%)                | Quality Status by Order Quality, Scrap Trend by Date, Available Quantity and Scrapped Quantity by Product Name, Total Scrapped Quantity by ScrapReason | Available Quantity and Scrapped Quantity by Product Name                |

### 4️⃣ Data modeling
![Image](https://github.com/user-attachments/assets/578094b5-341e-4af6-a2be-4c976074173c)

---

## 📊 Key Insights & Visualizations  

### 🔍 Dashboard Preview  

#### 1️⃣ View 1: Customer Segmentation Overview  
![Image](https://github.com/user-attachments/assets/7f552721-227a-43de-bd02-ce34e9f7a26b)

#### Insights:
- **Completion Rate:** The on-time completion rate is **68.6%**, while **31.4%** of tasks are delayed. This indicates a significant portion of orders need improvement in processing time.
- **Total Produced:** A total production of **4.5 million products** shows stable manufacturing capacity.
- **Total Orders by Subcategory:**  **Wheels and Road Frames** have the highest order volume, with **8.2K** and **6.7K** respectively, indicating high demand for these categories.
- **Product Performance:** Some products, such as **Mountain-100 Black** and **Mountain-500 Black**, have low production costs but could be further optimized by reducing the average production time (currently ranging from **16.9 to 17.8 days**).
#### Recommendations:
- **Improve Completion Rate:** Identify specific causes of delays to enhance production time.
- **Prioritize High-Demand Categories:** Focus on increasing production capacity for **Handlebars** and **Wheels** and consider investing in additional production lines for these items.
- **Reduce Average Production Time:** Evaluate and optimize the production process for products with low costs but long production times.
### View 2: Monthly Segment Analysis

#### 2️⃣ View 2: Monthly Segment Analysis  
![Image](https://github.com/user-attachments/assets/41e229bb-56f2-41a6-a1de-79dcfd9e8cd0)

#### Insights:
- **Total Inventory**: The current inventory is **339.74K**, with **91.11% being safe products** and **8.89% classified as unsafe products**.
- **Unsafe Products**: There are **95 unsafe products** that require attention to improve quality.
- **Inventory Trend Over Time**: Inventory levels fluctuate significantly, peaking at **48K in December 2014**.
- **Inventory Distribution by Category**: Most inventory is concentrated in **"Components" (49K)**, while categories like **Clothing (-6K)** show negative inventory levels, possibly due to stockouts or management errors.
- **Safe Stocked Products**: Items such as **Adjustable Race** and **BB Ball Bearing** have inventory levels well above the safety threshold.
#### Recommendations:
*a. Reduce Unsafe Products:*
- Identify and address unsafe products in the inventory immediately.
- Analyze the root causes of products becoming unsafe and implement preventive measures.

*b. Adjust Inventory for the Clothing Category:*
- Ensure no negative inventory levels by improving demand forecasting and procurement planning.
- Reassess the actual demand for the Clothing category to avoid overproduction or stock shortages.

*c. Optimize Safe Stocked Products:*
- Redistribute overstocked products (e.g., BB Ball Bearing) to regions or units with higher demand.

#### 3️⃣ View 3: Manufacturing Quality analysis  
![Image](https://github.com/user-attachments/assets/36277d00-1fbd-49d6-b7bd-715075696a07)

#### Insights:
- **Total Scrapped Quantity**: A total of **10.65K products** were scrapped, with **8.87% rejected** due to quality issues.
- **Scrap Trend Over Time**: The number of scrapped products peaked in 2013 (2.2K) and then declined in 2014.
- **Top Scrap Reasons**: The leading causes of scrapping include **"Paint process failed" (1271)**, **"Trim length too long" (981)**, and **"Thermoform temperature issues" (876)**.
- **Defect Rate and Average Production Time**: The defect rate is only **0.24%**, with an average production time of **13.24 days**.
- **Inventory and Scrap Distribution**: Certain products, such as BB Ball Bearing, have high inventory levels but also significant scrap quantities.
#### Recommendations:
*a. Address Common Scrap Reasons:*
- Implement stricter control processes for stages like **painting** and **trimming length**.
- Train employees and monitor temperature standards during thermoforming to reduce thermal issues.

*b. Improve Rejection Rate:*
- Conduct quality checks at critical production stages to detect errors earlier.
- Increase automation in the production process to reduce human-related errors.

---

## 🔎 Final Conclusion & Recommendations  

👉🏻 Based on the insights and findings above, we would recommend the [stakeholder team] to consider the following:  

📌 Key Takeaways:  
✔️ Recommendation 1  
✔️ Recommendation 2  
✔️ Recommendation 3
