---
title: "Union and union all in sql server Part 17.(https://www.youtube.com/watch?v=9w5uRCFOiTo&list=PL08903FB7ACA1C2FB&index=19)+CHATGPT+SSMS21"
date: 2025-10-23
tags: [SQL]
---




--  1️ 建立測試資料表 (如果存在就先刪掉)
IF OBJECT_ID('A', 'U') IS NOT NULL DROP TABLE A;
IF OBJECT_ID('B', 'U') IS NOT NULL DROP TABLE B;
GO

--  2️建立兩個表
CREATE TABLE A (Name NVARCHAR(10));
CREATE TABLE B (Name NVARCHAR(10));

-- 3️插入資料
INSERT INTO A VALUES ('Andy'), ('Bill'), ('Carol');
INSERT INTO B VALUES ('Bill'), ('David'), ('Andy');

-- 4️查看原始資料
SELECT 'Table A' AS 來源, * FROM A;
SELECT 'Table B' AS 來源, * FROM B;

-- 5️使用 UNION（自動移除重複）
PRINT '--- 使用 UNION（移除重複） ---';
SELECT Name FROM A
UNION
SELECT Name FROM B;

--  6️使用 UNION ALL（保留所有資料）
PRINT '--- 使用 UNION ALL（保留重複） ---';
SELECT Name FROM A
UNION ALL
SELECT Name FROM B;

--  7️ 額外示範：用 DISTINCT 模擬 UNION
PRINT '--- 使用 DISTINCT 模擬 UNION ---';
SELECT DISTINCT Name
FROM (
    SELECT Name FROM A
    UNION ALL
    SELECT Name FROM B
) AS Combined;
