```mermaid
graph TD
    A[低效 SQL 指令]

    subgraph 資源消耗
        B1[排序操作: DISTINCT, ORDER BY]
        B5[JOIN 操作: OUTER JOIN]
        C1[對大量資料進行 DISTINCT 或 ORDER BY 操作會建立臨時排序資料,耗費大量記憶體和 CPU 資源]
        C5[OUTER JOIN 相比 INNER JOIN 需要更多記憶體和 CPU 資源]
    end

    subgraph 索引使用
        B2[索引未使用: LIKE 前綴非常數, NOT IN/NOT EXISTS]
        B3[OR 條件]
        C2[使用前綴不是常數的 LIKE 查詢或大量資料的 NOT IN/NOT EXISTS 會導致全表掃瞄]
        C3[在 WHERE 子句中使用 OR 條件會讓優化器無法充分利用索引]
    end

    subgraph 臨時表操作
        B4[資料集合操作: UNION, INSERT INTO...SELECT]
        C4[連接大量資料集的 UNION 或對大量資料進行 INSERT INTO...SELECT 操作會建立臨時表導致效率低落]
    end

    subgraph 其他影響
        B6[邏輯判斷: CASE]
        B7[遞迴查詢: RECURSIVE CTEs]
        C6[大量使用 CASE 來進行邏輯判斷會降低查詢效率]
        C7[遞迴查詢會重複執行相同操作導致低效]
    end

    A --> B1
    A --> B2
    A --> B3
    A --> B4
    A --> B5
    A --> B6
    A --> B7
    B1 --> C1
    B2 --> C2
    B3 --> C3
    B4 --> C4
    B5 --> C5
    B6 --> C6
    B7 --> C7
```
    --------------------------------------------------------------------------------------------------------------
```mermaid

erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE_ITEM : includes
    CUSTOMER {
       nchar  customerid
       nvarchar  ContactName
       nvarchar ContactTitle
       nvarchar Address
       nvarchar City
       nvarchar Region
       nvarchar PostalCode
       nvarchar Country
       nvarchar Phone
       nvarchar Fax
    }
    ORDER {
        string orderNumber
        date orderDate
        int  OrderID
       nchar CustomerID
        int EmployeeID
       datetime OrderDate
        datetime RequiredDate
       datetime ShippedDate
       datetime ShipVia
       money Freight
      nvarchar  ShipName
      nvarchar  ShipAddress
       nvarchar ShipCity
       nvarchar ShipRegion
       nvarchar ShipPostalCode
       nvarchar ShipCountry
    }
    LINE_ITEM {
        int quantity
        float price
    }

```

# 50 SQL



## Entity-Relationship Diagram (ERD): An ERD is a structural diagram that illustrates the relationships between entities (tables) in a database. It helps in designing and understanding the database schema, identifying primary keys, foreign keys, and relationships between tables. ERDs are particularly useful during the database design phase and for documenting existing databases.
## Data Flow Diagram (DFD): A DFD is a graphical representation of the flow of data in a system, showing the processes, external entities, and the data flows between them. While not specific to SQL, DFDs can be helpful in understanding the overall data flow and how different components interact with the database.
## Database Schema Diagram: This diagram visually represents the structure of a database, including tables, columns, data types, primary keys, foreign keys, and relationships. It provides a clear overview of the database schema and can be useful for documentation and understanding the database design.
## Query Plan Diagram: A query plan diagram illustrates the execution plan chosen by the database management system (DBMS) to execute a specific SQL query. It can help in understanding how the DBMS processes a query, identifying potential performance bottlenecks, and optimizing queries.
## Database Architecture Diagram: This diagram depicts the overall architecture of a database system, including the various components such as client applications, connection pooling, load balancing, replication, and storage layers. It can be useful for understanding the high-level design and infrastructure of a database system.
## Database Cluster Diagram: For clustered or distributed database systems, a cluster diagram can represent the nodes, instances, and replication or sharding strategies employed in the database architecture.
## Database Backup and Recovery Diagram: This diagram illustrates the backup and recovery processes, including the different backup types (full, differential, transaction log), backup schedules, and restoration procedures. It can be helpful for documenting and understanding backup and disaster recovery strategies.

## In the CTE Usage section, I’ve added two tasks:

## DEFINE CTE: This represents the creation of the CTE using the WITH clause.
## USE CTE: This represents the usage of the defined CTE in a subsequent SQL operation.

## Certainly! A Common Table Expression (CTE) is a temporary result set that you can reference within a SELECT, INSERT, UPDATE, DELETE, or MERGE statement. It’s defined using the WITH clause and can make complex queries more readable and maintainable.
```mermaid
gantt
    title T-SQL Commands

    section Data Definition Language (DDL)
    CREATE DATABASE :done, create1, 2024-04-27, 2024-04-28
    CREATE TABLE :done, create2, after create1, 1d
    CREATE INDEX :done, create3, after create2, 1d
    CREATE VIEW :done, create4, after create3, 1d
    CREATE PROCEDURE :done, create5, after create4, 1d
    CREATE FUNCTION :done, create6, after create5, 1d
    ALTER TABLE :done, alter1, after create6, 1d
    DROP TABLE :done, drop1, after alter1, 1d
    DROP INDEX :done, drop2, after drop1, 1d
    DROP VIEW :done, drop3, after drop2, 1d
    DROP PROCEDURE :done, drop4, after drop3, 1d
    DROP FUNCTION :done, drop5, after drop4, 1d

    section Data Manipulation Language (DML)
    INSERT INTO :done, insert1, 2024-04-29, 2024-04-30
    UPDATE :done, update1, after insert1, 1d
    DELETE :done, delete1, after update1, 1d
    MERGE :done, merge1, after delete1, 1d
    SELECT INTO :done, selectinto1, after merge1, 1d

    section Data Control Language (DCL)
    GRANT :done, grant1, 2024-05-01, 2024-05-02
    REVOKE :done, revoke1, after grant1, 1d
    DENY :done, deny1, after revoke1, 1d

    section Query Commands
    SELECT :done, select1, 2024-05-03, 2024-05-04
    FROM :done, from1, after select1, 1d
    WHERE :done, where1, after from1, 1d
    GROUP BY :done, groupby1, after where1, 1d
    HAVING :done, having1, after groupby1, 1d
    ORDER BY :done, orderby1, after having1, 1d
    LIMIT :done, limit1, after orderby1, 1d
    OFFSET :done, offset1, after limit1, 1d
    JOIN :done, join1, after offset1, 1d
    UNION :done, union1, after join1, 1d
    INTERSECT :done, intersect1, after union1, 1d
    EXCEPT :done, except1, after intersect1, 1d

    section Subqueries
    IN :done, in1, 2024-05-05, 2024-05-06
    EXISTS :done, exists1, after in1, 1d
    NOT EXISTS :done, notexists1, after exists1, 1d
    ALL :done, all1, after notexists1, 1d
    ANY :done, any1, after all1, 1d
    SOME :done, some1, after any1, 1d

    section Aggregate Functions
    SUM :done, sum1, 2024-05-07, 2024-05-08
    AVG :done, avg1, after sum1, 1d
    MAX :done, max1, after avg1, 1d
    MIN :done, min1, after max1, 1d
    COUNT :done, count1, after min1, 1d
    GROUPING SETS :done, groupingsets1, after count1, 1d

    section String Functions
    LEN :done, len1, 2024-05-09, 2024-05-10
    LOWER :done, lower1, after len1, 1d
    UPPER :done, upper1, after lower1, 1d
    LTRIM :done, ltrim1, after upper1, 1d
    RTRIM :done, rtrim1, after ltrim1, 1d
    CONCAT :done, concat1, after rtrim1, 1d

    section CTE Usage
    DEFINE CTE :done, cte1, 2024-05-11, 2024-05-12
    USE CTE :done, cte2, after cte1, 1d
```
