---
title: "MongoDB Performance Explain"
date: 2023-12-25T14:24:02+08:00
draft: true
---

這篇文章是 [M201: MongoDB Performance](https://learn.mongodb.com/courses/m201-mongodb-performance) 的課程筆記  
MongoDB 中，透過 explain 指令能夠進行效能分析

# Explain 功能
透過 explain() 可以知道進行查詢時的以下幾個資訊
- 使用了哪一個 index
- 此次查詢是否有效地篩選了資料（selective）
- 查詢的過程中各個階段所花費的時間

# Explain 的模式
MongoDB 的 explain() 共有三種模式，不同的模式會影響執行 explain() 的方式以及輸出的內容會有差異
1. queryPlanner
2. executionStats
3. allPlansExecution

## queryPlanner
- 透過內建的查詢優化器，選擇最優的查詢計畫並**評估查詢結果**，而**不會實際執行查詢計畫**
- explain() 的預設模式

## executionStats
- 實際執行查詢計畫，因此能獲得每個階段的詳細資訊

## allPlansExecution
- 結合 queryPlanner 和 executionStats 的資訊

# 如何使用 explain
執行 explain 最簡單的方式就是在執行指令的最後面加上 explain():  
```
db.restaurants.find().explain()
db.restaurants.find().explain("executionStats" )
```

然而，若需使用較複雜的查詢語法或需要多次運行 explain()，則可宣告 explain() 物件：
```
exp = db.restaurants.explain()
exp.find()
exp.find("cuisine" : "Japanese")
```

# 參考
- https://learn.mongodb.com/learn/course/m201-mongodb-performance/lesson-2-mongodb-indexes/learn?page=5
- https://ithelp.ithome.com.tw/m/articles/10264606