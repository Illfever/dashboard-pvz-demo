# Дашборд аналитики ПВЗ

Аналитический дашборд для пункта выдачи заказов (ПВЗ), собранный на основе открытых для менеджера данных.  Позволяет отслеживать ключевые метрики за периоды: Февраль, Март, Апрель.

## Данные
- `total_orders.csv` — информация о заказах клиентов
- `total_drivers.csv` — информация о поставках товаров

Подробнее о подготовке данных см. в [DATA_PREPARATION.md](DATA_PREPARATION.md)

## Инструменты
- **Jupyter Notebook** — среда для разработки и запуска кода
- **Python** + **SQLite** — обработка данных и выполнение запросов
- **Google Sheets** — визуализация дашборда

## Метрики
- Выдача и отказы товаров
- Приёмка товаров (план, излишки, недостачи)
- Нагрузка по часам и дням недели
- Распределение заказов по числу товаров

## Структура проекта
```
dashboard-pvz-demo-main/
├── data/                     # исходные обезличенные данные
│ ├── total_orders.csv       
│ └── total_drivers.csv
├── processed/                # результат работы Jupyter Notebook (7 листов в одном .xlsx файле)
│ └── total_pvz_demo.xlsx
├── notebooks/                # Jupyter Notebook с обработкой
│ └── preprocessing.ipynb
├── DATA_PREPARATION.md       # пример кода подготовки данных
├── README.md                 # о проекте
└── requirements.txt          # зависимости
```

## Как использовать
1. Скачайте репозиторий с GitHub [dashboard-pvz-demo](https://github.com/Illfever/dashboard-pvz-demo)
2. Откройте `notebooks/pvz_dashboard_demo.ipynb`
3. Укажите путь до папки `dashboard-pvz-demo-main` в переменную `your_parh` в ячейке 2
4. Запустите все ячейки `Kernel → Restart & Run All Cells`
5. Результат сохранится в `processed/total_pvz_demo.xlsx`
6. Сделайте копию таблицы [Дашборд ПВЗ Потайных ИС (demo)](https://docs.google.com/spreadsheets/d/1xlIDR9gBZlEHfQP-As368SFXn0fRu0vME9kiBt6pfkg/edit?usp=sharing) `Файл → Создать копию`
7. Скопируйте данные из файла `processed/total_pvz_demo.xlsx` на лист "Периоды" в соответствующие таблицы (ячейки для вставки выделены белым) или оставьте без изменений, т.к. данные уже внесены
8. На листе "Графики" выберите период в ячейке A2

## Требования
Установите зависимости:
pip install -r requirements.txt

## Готовый дашборд
Результат работы проекта можно посмотреть по ссылке в Google Sheets:  
[Дашборд ПВЗ Потайных ИС (demo)](https://docs.google.com/spreadsheets/d/1xlIDR9gBZlEHfQP-As368SFXn0fRu0vME9kiBt6pfkg/edit?usp=sharing)

## Автор
Ирина Потайных
