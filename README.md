### Тестове завдання

#### Середовище розробки

**Версії необхідного ПЗ:**
- **Node.js:** 12.22.12
- **Yarn:** 1.22.22

**Запуск проекту:**

*Локально (при наявності потрібних версій Node.js):*
1. `yarn install` - встановлення залежностей.
2. `yarn serve` - запуск сервера розробки.

*Використовуючи Docker:*
1. `docker-compose up -d` - створення та запуск контейнерів в фоновому режимі.
2. `docker-compose exec vue-app yarn install` - встановлення залежностей у контейнері.
3. `docker-compose exec vue-app yarn serve` - запуск сервера розробки у контейнері.

---

### Опис завдань

#### Завдання 1: Робота зі статусами

- **Мета:** Розробити логіку відображення статусів у таблиці.
- **Вхідні дані:**
  - Колонка `Status` таблиці, яка приймає значення від `1` до `5`.

- **Що потрібно зробити:**
  1. Створити довільний довідник значень статусів на front-end.
  2. Реалізувати логіку заміни `id` статусу на відповідне текстове значення з довідника, не змінюючи код зовнішнього компонента.

#### Завдання 2: Фільтрація активних записів

- **Мета:** Додати можливість управління відображенням активних/неактивних записів.
- **Вхідні дані:**
  - Дані з back-end, отримані з моделі Laravel, яка використовує `SoftDeletes`.
  - Колонка `Is Active` відображає активність запису в булевому форматі, залежно від поля `deleted_at`.
  - Базова структура запиту на back-end:
    ```php
    TestData::query()
      ->withTrashed()
      ->select(
          'id as dtRowId',
          'name',
          'description',
          'status_id',
          'deleted_at',
          'created_at',
          'updated_at',
          DB::raw('(deleted_at IS NULL) AS is_active'),
      );
    ```

- **Що потрібно зробити:**
  1. Розробити компонент `VueSwitch` над таблицею, який дозволить користувачам перемикати відображення активних та неактивних записів, інформуючи про це back-end.

---

#### Документація по роботі з таблицею

- **Front-end:** [https://docs.laravel-enso.com/frontend/tables.html](https://docs.laravel-enso.com/frontend/tables.html)
- **Back-end:** [https://docs.laravel-enso.com/backend/tables.html](https://docs.laravel-enso.com/backend/tables.html)
