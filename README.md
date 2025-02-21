# Тестирование веб-сервиса «Кинопоиск»

В рамках проекта необходимо провести тестирование функционала веб-сервиса «Кинопоиск». В частности, проверить работу функций поиска фильмов и сериалов по названию, идентификатору и дополнительным параметрам. Также требуется проверить работу функций авторизации и выставления оценок фильмам и сериалам.

Проект состоит из пяти тестов пользовательского интерфейса (UI) и пяти тестов API.

## Полезные ссылки:

[Ссылка на финальный проект по ручному тестированию](https://ilyabakumov.yonote.ru/share/c342acef-a08b-4e00-b3da-3d7eefa9da7a/doc/test-plan-5sbg3mEIS8).


## Файлы проекта:

*   **`requirements.txt`**: Файл с зависимостями, необходимыми для работы проекта. Для установки зависимостей используйте команду:

    ```bash
    pip install -r requirements.txt
    ```

*   **`conftest.py`**: Файл с фикстурами, используемыми в проекте. Фикстуры предоставляют тестовым функциям данные и ресурсы.

*   **`config.json`**: Файл с данными конфигурации, включая:
    *   Данные для авторизации на сайте (логин и пароль).
    *   URL-адреса для тестов пользовательского интерфейса и API.
    *   Информацию о заголовках и токенах, передаваемых в тестах API.

*   **`pytest.ini`**: Файл с настройками pytest. В файле можно указать, например, дополнительные параметры запуска тестов или изменить поведение pytest.

*   **`pages/AuthPage.py`**:  Файл с классом `AuthPage`, содержащим методы для взаимодействия со страницей авторизации на сайте «Кинопоиск».

*   **`pages/FilmSeriesPage.py`**: Файл с классом `FilmSeriesPage`, содержащим методы для взаимодействия с персональной страницей фильма, сериала или персоны. Включает методы:
    *   Поиска элементов на странице.
    *   Нажатия на элементы.
    *   Нахождения элементов и считывания их текста.
    *   Нахождения кнопок.
    *   Контроля установленной оценки.
    *   Установки, изменения и удаления оценки.

*   **`pages/MainPage.py`**: Файл с классом `MainPage`, содержащим методы для взаимодействия с главной страницей сервиса и страницей результатов поиска. Включает методы:
    *   Обработки капчи (если есть).
    *   Ввода запроса в модуль поиска.
    *   Сбора информации по подсказкам к поиску.
    *   Нажатия кнопки поиска.
    *   Получения информации на странице результатов поиска.
    *   Поиска фильма или сериала.
    *   Поиска персоны.
    *   Выполнения ошибочного (пустого) поиска.

*   **`api/FilmSeriesApi.py`**: Файл с классом `FilmSeriesApi`, содержащим методы для поиска фильмов или сериалов с использованием API. Включает методы поиска фильма/сериала:
    *   По названию.
    *   По идентификатору.
    *   По дополнительным полям.

*   **`api/PersonAPI.py`**: Файл с классом `PersonAPI`, содержащим методы для поиска персоны с использованием API. Включает методы поиска персоны:
    *   По имени и фамилии.
    *   По идентификатору.

*   **`test/test_ui.py`**: Файл с тестами пользовательского интерфейса (UI).

*   **`test/test_api.py`**: Файл с тестами API.

## Запуск тестов:

*   **Тесты пользовательского интерфейса (UI):**

    ```bash
    pytest test/test_ui.py
    ```

    Для формирования отчёта Allure:

    ```bash
    pytest test/test_ui.py --alluredir allure-results-ui
    allure serve allure-results-ui
    ```

*   **Тесты API:**

    ```bash
    pytest test/test_api.py
    ```

    Для формирования отчёта Allure:

    ```bash
    pytest test/test_api.py --alluredir allure-results-api
    allure serve allure-results-api
    ```

**Пояснения:**

*   `pytest`: Команда для запуска тестов pytest.
*   `test/test_ui.py`  и  `test/test_api.py`:  Пути к файлам с тестами.
*   `--alluredir allure-results-ui`  и  `--alluredir allure-results-api`: Опция для указания директории, в которую будут сохранены результаты Allure.  Используйте разные директории (`allure-results-ui`  и  `allure-results-api`) для UI и API тестов, чтобы избежать перемешивания результатов.
*   `allure serve allure-results-ui` и `allure serve allure-results-api`:  Команда для генерации и отображения отчета Allure в веб-браузере.  Она запустит локальный сервер и автоматически откроет отчет.
*   Удостоверьтесь, что Allure Commandline Tool установлен и доступен в вашей системе (`allure --version`).
*   Замените `ЗДЕСЬ_ДОЛЖНА_БЫТЬ_ССЫЛКА` фактическим URL.
*   Вы можете объединить результаты UI и API тестов в одном отчете Allure, если сохраните их в одну и ту же директорию (`allure-results`), но это может быть менее удобно для анализа.
*   `pytest.ini` может содержать настройки, такие как маркеры, пути для поиска тестов и другие параметры.

Этот README предоставляет всю необходимую информацию для понимания структуры проекта и запуска тестов.
