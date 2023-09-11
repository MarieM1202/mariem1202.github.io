---
title: "Reactivating Revenue: Unlocking the Value of Dormant Customers with Snowflake Analytics"
meta_title: ""
description: "This project aims to identify a list of inactive customers for the next marketing campaign. These are the customers who have not made any transactions in the last 90 days."
date: 2023-09-10
image: "/images/customer-retention.jpg"
categories: ["SQL","DataCleaning","Database","Snowflake"]
tags: ["SQL", "Snokflake"]
draft: false

---

In today's digital landscape, data is abundant but often underutilized. Recognizing this, I set out to leverage Snowflake's capabilities to turn raw customer data into actionable insights. My focus was on identifying a critical business challenge: pinpointing customers who have been inactive for over 90 days.

### Key Discoveries

A significant highlight of this project was uncovering a segment of 13 customers who had not engaged in any transactions for over 90 days. This was achieved by creating a custom view in Snowflake, where I used a Common Table Expression (CTE) to first rank customers based on their last transaction date. 

    CREATE OR REPLACE VIEW CUSTOMERS_VW AS (
    WITH LISTIDs AS (
        SELECT 
            ID, Name, Email, LastTransaction,
            -- Ranking emails by latest transaction date
            rank() over (partition by email order by TO_DATE(LastTransaction, 'AUTO') desc) RANK 
        FROM CUSTOMERS
        -- Only the latest transaction for each email is considered
        QUALIFY RANK = 1
    )

This was further filtered to only include those with the most recent transaction in each email group. The final query then incorporated additional transformation functions like SPLIT_PART and DATEDIFF to produce a more enriched dataset, which also included calculated columns such as 'AGE' and 'DaysSinceLastTrans.'

     SELECT 
        ID,
        SPLIT_PART(TRIM(NAME, ' 0'), ',', 1) AS FIRST_NAME,
        SPLIT_PART(TRIM(NAME, ' 0'), ', ', 2) AS LAST_NAME,
        EMAIL,
        
        TO_DATE(DoB, 'MMMM DD, YYYY') AS DoB,
        DATEDIFF(year, TO_DATE(DoB, 'MMMM DD, YYYY'), current_date()) AS AGE,
        
        TO_DATE(LastTransaction, 'AUTO') AS LastTransaction,
        DATEDIFF(days, LastTransaction, current_date()) AS DaysSinceLastTrans,
        
        IFF(((COMPANY IS NULL) OR (COMPANY = '')), 'N/A', COMPANY) AS COMPANY,
        LTRIM(PHONE, '+0') AS PHONE,
        ADDRESS, postalZip, Region, COUNTRY
    FROM
        CUSTOMERS
    WHERE
        NOT(email IS NULL OR email = '') AND ID IN (SELECT ID FROM LISTIDs));


The use of this complex query served a twofold purpose: it not only helped identify inactive customers but also provided a comprehensive snapshot of customer data that could be leveraged for various other analytics. This demonstrates the potency of effective data analysis in not only identifying key customer segments but also in enabling targeted business strategies. Such insights are invaluable for any organization looking to improve customer engagement and retention.

### Accomplishments 
The final output of the project was a CSV file meticulously listing these 13 inactive customers, thereby providing the company with the opportunity for targeted re-engagement efforts. The creation and implementation of this Snowflake-based solution offered a more streamlined, automated way to track customer engagement, replacing what might have been a tedious manual process.

| ID | Name          | Email               | DOB       | Age | Last Trans  | Days Since |
|----|---------------|---------------------|-----------|-----|-------------|------------|
| 7  | Mayer D.      | ipsum@...            | 1997-11-27| 26  | 2022-09-01  | 375        |
| 6  | Golden L.     | lacus@...            | 1970-09-12| 53  | 2022-10-01  | 345        |
| 10 | Alford R.     | vel@...              | 1967-10-20| 56  | 2022-07-18  | 420        |
| 4  | Bennett N.    | elementum@...        | 1951-10-21| 72  | 2021-12-21  | 629        |
| 1  | Kline A.      | tempor@...           | 1996-02-10| 27  | 2022-09-21  | 355        |
| 9  | Hyde A.       | odio@...             | 1951-01-31| 72  | 2022-06-19  | 449        |
| ...| ...           | ...                  | ...       | ... | ...         | ...        |

 

### Conclusion
This project was not just a technical exercise but a practical application of data analytics to solve a real-world business problem. Beyond the technicalities, I learned the importance of aligning data strategy with business objectives. Challenges like data normalization and ensuring data privacy were learning experiences that added layers of complexity to the project. As a next step, this framework could be expanded to automate the entire process through real-time analytics, further optimizing customer re-engagement strategies. In the end, I was able to successfully blend technical skills with business strategy, all powered by Snowflake's reliable and scalable data warehousing solutions.

Check out my project on [GitHub](https://github.com/MarieM1202/CustomerRetention-SQL-Snowflake).
