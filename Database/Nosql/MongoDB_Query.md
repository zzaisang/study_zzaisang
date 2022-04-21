# MongoDB_Query

## MongoDB 데이터(Document) 조회

- 아래와 같은 데이터가 적재되어 있다고 가정 (collection Name : inventory)
```json
[
    { "item": "journal", "qty": 25, "size": { "h": 14, "w": 21, "uom": "cm" }, "status": "A" },
    { "item": "notebook", "qty": 50, "size": { "h": 8.5, "w": 11, "uom": "in" }, "status": "A" },
    { "item": "paper", "qty": 100, "size": { "h": 8.5, "w": 11, "uom": "in" }, "status": "D" },
    { "item": "planner", "qty": 75, "size": { "h": 22.85, "w": 30, "uom": "cm" }, "status": "D" },
    { "item": "postcard", "qty": 45, "size": { "h": 10, "w": 15.25, "uom": "cm" }, "status": "A" }
]
```


### 전체 조회
```db.inventory.find()```

### equal 조건 조회 
```db.inventory.find({status : "D"})```

### in 조건 조회 
```db.inventory.find({ status: { $in: [ "A", "D" ] } })```

### 여러개의 and 조건
```db.inventory.find({ status: "A", qty: { $lt: 30 } })```

### 여러개의 or 조건
```db.inventory.find({ $or: [ { status: "A" }, { qty: { $lt: 30 } } ] }})```

### 여러개의 And 와 or 혼합 조건
```db.inventory.find({ status: "A", $or: [ { qty: { $lt: 30 } }, { item: /^p/ } ] })```

### 조회 조건 예시 (Mysql vs mongoDB)

1. ```SELECT * FROM inventory WHERE status = "D"``` = ```{ status: "D" } ... }```
2. ```SELECT * FROM inventory WHERE status in ("A", "D")``` = ```{ status: { $in: [ "A", "D" ] } }```
3. ```SELECT * FROM inventory WHERE status = "A" AND qty < 30``` = ```{ status: "A", qty: { $lt: 30 } }```
4. ```SELECT * FROM inventory WHERE status = "A" OR qty < 30``` = ```{ $or: [ { status: "A" }, { qty: { $lt: 30 } } ] }```
5. ```SELECT * FROM inventory WHERE status = "A" AND ( qty < 30 OR item LIKE "p%")``` = ```{ status: "A", $or: [ { qty: { $lt: 30 } }, { item: /^p/ } ] }```

---
출처 : https://www.mongodb.com/docs/manual/tutorial/query-documents/