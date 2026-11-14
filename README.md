# MEPHI Linux Security 2026

Бухгалтерский шифр: 374787.

Работа выполнена в VirtualBox VM Simply Linux 11.1 через POSIX-команды в терминале.

## Результаты

- Создан user1 с UID 1234, основной группой students; срок пароля — 90 дней. Аккаунт остаётся заблокированным, так как пароль ему не задавался.
- set-UID: /home/user1/cat, root:user1, режим 4750; чтение /etc/shadow проверено. Хеши в отчётах скрыты.
- Capability: /home/user1/chown-cap с cap_chown=ep; смена владельца тестового файла проверена, тестовый файл возвращён user1.
- sudoers разрешает user1 запускать /usr/bin/timedatectl без пароля. Правило показано через sudo -l, конфигурация прошла visudo -c. Время системы не менялось.
- Поиск set-UID сохранён в files-suid.out. Процессов с EUID 0 и пользовательским RUID не обнаружено. passwd в проверке имел RUID/EUID 1000.

## Файлы

Снимок экрана: mephi-screenshot.png. Команды: history.out. Атрибуты: stat.out, getcap.out. Мониторинг: files-suid.out, processes.out. Учётные записи и настройки: etc-passwd, etc-group, etc-sudoers, sudoers-user1-time. Файл etc-shadow.redacted содержит маркер вместо хешей и безопасен для публикации. Проверки: setuid-check.out, capability-check.out, sudo-check.out, visudo-check.out.# MEPHI Linux Security 2026

Бухгалтерский шифр: 374787.

Работа выполнена в VM Simply Linux 11.1 через терминал.

## Результаты

- Создан user1 (UID 1234, группа students), срок пароля 90 дней. Учётная запись заблокирована до задания пароля.
- /home/user1/cat: root:user1, режим 4750; проверено чтение /etc/shadow. Хеши паролей замаскированы в опубликованных отчётах.
- /home/user1/chown-cap получил cap_chown=ep; смена владельца тестового файла проверена, тестовый файл возвращён user1.
- sudoers разрешает запуск /usr/bin/timedatectl через sudo; проверка visudo -c успешна. Системное время не менялось.
- Сканирование set-UID сохранено в files-suid.out. Процессов с EUID 0 и пользовательским RUID не найдено; passwd во время запроса имел RUID/EUID 1000.

## Артефакты

mephi-screenshot.png, history.out, stat.out, getcap.out, files-suid.out, processes.out, etc-passwd, etc-group, etc-sudoers, sudoers-user1-time, etc-shadow.redacted, setuid-check.out, capability-check.out, sudo-check.out, visudo-check.out.
