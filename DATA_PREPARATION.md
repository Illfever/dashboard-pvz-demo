# Подготовка исходных данных

## Извлечение данных из JSON (пример)

Исходный HAR-файл (не включён в репозиторий) обрабатывался следующим образом:

```python
import json

# Загрузка и парсинг JSON
with open("your_path/orders_data.har", "r", encoding="utf-8") as f:
    har = json.load(f)

all_entries = []
for entry in har["log"]["entries"]:
    if "logV2" in entry["request"]["url"]:
        text = entry["response"]["content"].get("text")
        if text:
            data = json.loads(text)
            all_entries.extend(data.get("logV2", {}).get("entries", []))

# Преобразование в таблицу
rows = []
for entry in all_entries:
    for ex in entry['exemplars']:
        # В исходных данных причина возврата может лежать в двух местах
        reason = ex.get('returnReason') or entry.get('returnReason')
        
        rows.append({
            'orderNumber': entry['orderNumber'],
            'postingId': entry['postingId'],
            'moment': entry['moment'],
            'isReturned': 1 if ex['isReturned'] else 0,
            'returnReason': reason
        })

orders = pd.DataFrame(rows)

# Преобразование времени в datetime
orders['moment'] = pd.to_datetime(orders['moment']).dt.tz_convert('Asia/Krasnoyarsk').dt.strftime('%Y-%m-%d %H:%M:%S')
```

Этот код не входит в `preprocessing.ipynb` и приведён только для понимания источника данных.

## Результат
- `total_orders.csv` — заказы клиентов (обезличенные данные)
- `total_drivers.csv` — поставки товаров (обезличенные данные)

Оба файла находятся в папке `data/` репозитория.