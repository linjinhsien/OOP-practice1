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