# SQL & Pandas: Datamart Engineering, Aggregations & A/B Testing

[English](#english) | [Русский](#русский)

---

## English

A practical data analytics project combining **SQL (SQLite)** and **Pandas** to investigate user behavior on an educational platform. Starting from raw event logs (`checker` and `pageviews`), the project builds an analytical datamart, computes behavioral aggregations, and evaluates a product A/B test measuring the impact of a new Newsfeed feature on student submission deadlines.

### Tech Stack & Tools
* **Database & Query Language:** SQLite (`sqlite3`), SQL (`SELECT`, subqueries, `JOIN`, `GROUP BY`, `CASE`, datetime arithmetic)
* **Data Analysis:** `pandas` (`read_sql`, `to_sql`, `DatetimeIndex`, `corr()`)
* **Environment:** Jupyter Notebook

### Project Structure (`src/`)

* **`ex00/ex00_first_select.ipynb`** — **Database Exploration & Filtered Queries:** Inspecting table schemas (`PRAGMA table_info`), filtering records at the database level (`user_*` exclusion of admin accounts), sorting, and parsing timestamps into a `DatetimeIndex`.
* **`ex01/ex01_subquery.ipynb`** — **Nested Subqueries:** Writing multi-level SQL subqueries to count pageview events filtered by valid first submission attempts (`status = 'ready'`, `numTrials = 1`) across active project tasks.
* **`ex02/ex02_joins.ipynb`** — **Analytical Datamart Construction:** Joining `checker` and `pageviews` logs via a single SQL query to build a `datamart` table (`uid`, `labname`, `first_commit_ts`, `first_view_ts`), splitting users into `test` and `control` cohorts, imputing baseline timestamps, and persisting tables back to SQLite.
* **`ex03/ex03_aggs.ipynb`** — **Aggregations & Correlation Analysis:** Joining submission timestamps with `deadlines` to compute minimum, maximum, and average time-to-deadline deltas (in hours), and calculating the correlation between Newsfeed pageviews and submission timing (`corr()`).
* **`ex04/ex04_ab-test.ipynb`** — **Product A/B Testing (`before` vs. `after`):** Evaluating pre- and post-exposure submission deltas across `test` and `control` groups using single-query SQL aggregations to determine whether the Newsfeed feature motivated students to start assignments earlier.

### Usage
* Place the SQLite database inside `src/data/` and open any notebook in Jupyter Lab / Jupyter Notebook or VS Code: `jupyter notebook src/ex04/ex04_ab-test.ipynb`

---

## Русский

Практический проект по аналитике данных на стыке **SQL (SQLite)** и **Pandas**, посвящённый исследованию поведения пользователей образовательной платформы. На основе сырых логов событий (`checker` и `pageviews`) в проекте формируется аналитическая витрина данных, рассчитываются поведенческие метрики и проводится продуктовый A/B-тест влияния новой ленты активности на сроки начала работы над заданиями.

### Стек и инструменты
* **База данных и язык запросов:** SQLite (`sqlite3`), SQL (`SELECT`, подзапросы, `JOIN`, `GROUP BY`, `CASE`, арифметика дат и времени)
* **Анализ данных:** `pandas` (`read_sql`, `to_sql`, `DatetimeIndex`, `corr()`)
* **Среда разработки:** Jupyter Notebook

### Структура проекта (`src/`)

* **`ex00/ex00_first_select.ipynb`** — **Изучение схемы БД и фильтрующие запросы:** Проверка структуры таблиц (`PRAGMA table_info`), фильтрация записей на стороне СУБД (выборка только пользовательских аккаунтов `user_*`), сортировка и преобразование временных меток в `DatetimeIndex`.
* **`ex01/ex01_subquery.ipynb`** — **Вложенные подзапросы:** Построение многоуровневых SQL-подзапросов для подсчёта просмотров ленты по пользователям с валидными первыми отправками решений (`status = 'ready'`, `numTrials = 1`) по списку активных заданий.
* **`ex02/ex02_joins.ipynb`** — **Построение аналитической витрины (`datamart`):** Объединение таблиц `checker` и `pageviews` одним SQL-запросом с формированием витрины (`uid`, `labname`, `first_commit_ts`, `first_view_ts`), разделение аудитории на группы `test` и `control`, заполнение базовых меток времени и сохранение таблиц в БД.
* **`ex03/ex03_aggs.ipynb`** — **Агрегации и корреляционный анализ:** Объединение данных с таблицей дедлайнов (`deadlines`) для расчёта минимальной, максимальной и средней разницы времени до дедлайна (в часах), а также оценка корреляции между числом просмотров ленты и скоростью старта работы (`corr()`).
* **`ex04/ex04_ab-test.ipynb`** — **Продуктовый A/B-тест (`before` и `after`):** Сравнение средней дельты до дедлайна до и после первого просмотра ленты в группах `test` и `control` одним SQL-запросом на группу для проверки гипотезы о влиянии новой функциональности на поведение студентов.

### Запуск
* Поместите файл базы данных SQLite в директорию `src/data/` и откройте нужный ноутбук в Jupyter Notebook / Jupyter Lab или VS Code: `jupyter notebook src/ex04/ex04_ab-test.ipynb`
