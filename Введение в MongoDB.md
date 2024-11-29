# Nereljacionnye-bazy-dannyh-i-MongoDB

задание 1
Цель практической работы:
Научиться выполнять простые запросы в MongoDB.

Запрос:
```
db.posts.find({
  topics: "as",
  author: { $regex: "example\\.ru$" },
  score: { $gt: 100 }
})
```

Задание 2
Цель практической работы:
Научиться писать запросы с использованием различных структур данных в MongoDB.

Запрос:
```
db.posts.insertMany([
  {
    creation_date: new Date(),
    author: "skbx@example.com",
    topics: ["mongodb"]
  },
  {
    creation_date: new Date("2021-12-31"),
    author: "skbx@example.ru"
  }
])
```

Задание 3
Цель практической работы:
Научиться анализировать запросы и создавать индексы в MongoDB.

Создание индекса:
```
db.users.createIndex({ first_name: 1, last_name: 1 })
```
Проверка использования индекса:
```
db.users.find({ first_name: "John", last_name: "Doe" }).explain("executionStats")
```

Задание 4
Цель практической работы:
Научиться писать аналитические запросы в MongoDB.

Запрос:
```
db.users.aggregate([
  { $match: { visits: { $gt: 300 } } },
  {
    $group: {
      _id: { $substr: ["$first_name", 0, 1] },
      total_karma: { $sum: "$karma" }
    }
  }
])
```

Задание 5
Цель практической работы:
Научиться писать хранимые процедуры в MongoDB.

Запрос на создание функции:
```
db.system.js.save({
  _id: "shuffle",
  value: function(str) {
    return str.split('').sort(function() {
      return 0.5 - Math.random();
    }).join('');
  }
})
```
Использование функции
```
db.eval("shuffle('example')")
```
