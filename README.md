## Distributed systems project
### Модель взлета самолета

Реализация на JavaScript, с использованием HTML и CSS
Проект реализует модель взлета самолета. Каждый из узлов распределенной системы представлен сервером с определенным портом.

* экипаж самолета:                  3000            npm run plane       (Андрей)
* диспетчер АДП:                    3001            npm run dadp        (Даша,Ринат)
* дис-р руления:                    3002            npm run drulen      (Паша)
* дис-р старта:                     3003            npm run dstart      (Паша)
* д-р АДЦ:                          3004            npm run dadc        (Даша,Ринат)
* д-р РДЦ:                          3005            npm run drdc        (Даша,Ринат)

____________________________________________________

#### TODO: Оформить интрфейс каждому(самый простой) чтобы были видны сообщения
#### TODO: Логика

## Сразу договоримся:

* Все сообщения ввиде json {type: "", data""}
* Делай документацию сразу!

____________________________________________________

Важная обнова. cors переоценён. вместо него стоит использовать следующий код в index.js (в начале):

```javascript
router.use(function(req, res, next) {
    res.header('Access-Control-Allow-Origin', '*');
    res.header('Access-Control-Allow-Methods', 'GET, PUT, POST, DELETE, OPTIONS');
    res.header('Access-Control-Allow-Headers', 'Content-Type, Authorization, Content-Length, X-Requested-With');

    //intercepts OPTIONS method
    if ('OPTIONS' === req.method) {
        //respond with 200
        res.send(200);
    }
    else {
        //move on
        next();
    }
});
```

и в ajax запросе надо дописать

```javascript
    xhttp.setRequestHeader("Content-Type", "application/json");   // !!!important
    xhttp.send(JSON.stringify({type: "command", data: command.value}));  // !!!important
```
отсюда - http://johnzhang.io/options-request-in-express
как то так.
