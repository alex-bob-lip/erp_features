# Методика работы с конфигурациями большого объема

!Черновик

Дано:

    1. Конфигурация, исходники которой занимают 3,5 гБ на жестком диске (ERP).
    2. Команда разработки состоящая не только из программстов, но и аналитиков.
    3. Есть хранилище конфигурации.

Проблемы:

    1. Большой объем репозитория сказывается на:
        1.  Скорости начала работы с репозиторием.
        2.  Времени выполнения этапа получения исходников в процессе тестирования.
    2. Разработка нескольких таких проектов потребует значительного дискового пространства.
    3. Аналитику исходники конфигурации в общем случае могут не быть нужны - он пишет фичи.

Решение:

Для хранения исходников конфигурации использовать отдельную ветку репозитория.

Чтобы это реализовать нужно:

    1. Настроить задачу гитсинк на Jenkins для синхронизации хранилища с выбранной веткой
        1. первая команда смена кодировки, вторая - смена ветки, треться экспорт
    2. Создать задачу которая будет автоматически обновлять ветку с исходниками из ветки где хранятся прочие исходники (фичи, внешние обработки)
    3. Выполнение полной сборочной линии запускать по изменениям ветки с исходниками конфигурации.