# Исправление ошибки [remote rejected]

Если Git при попытке `push` выдает ошибку:

`! [remote rejected] main -> main (permission denied)`

или

`! [remote rejected] <branch_name> -> <branch_name> (permission denied)`

это означает ошибку в конфигурации программы Git на компьютере. В этом случае используем следующую инструкцию:

1. Открываем для редактирования глобальный config для экземпляра Git, установленного на компьютер

    `git config --global --edit`

2. Добавляем необходимые разрешения:

        [credential]
            helper = <Nickname>
            useHttpPath = true

3. Закрываем файл

4. Вновь выполняем `push`

5. Проходим авторизацию на GitHub

# Внесение изменений в созданные ветки в удаленном репозитории через подключение их к созданным веткам в локальном репозитории

Мы можем выполнять изменения в удаленном репозитории из локального репозитория даже в том случае, если локальный репозиторий не является результатом выполнения команды `clone`. Для этого выполняем следующие действия:

1. Создаем локальный репозиторий с произвольным именем.

1. Создаем ветку с именем, аналогичным уже имеющейся ветке в удаленном репозитории, или новым произвольным именем.

1. Подключаем удаленный репозиторий с помощью 

    `git remote add origin <URL>`

1. Переключаемся на нужную ветку, выполняем
    
    `pull origin <branch_name>`
    
    где `<branch_name>` - имя той ветки удаленного репозитория, которую необходимо связать с текущей веткой локального репозитория.

1. Вносим необходимые изменения в файлы.

1. Выполняем 
    
    `git push --set-upstream origin <branch_name>`
    
    где `<branch_name>` - имя той ветки удаленного репозитория, которую необходимо связать с текущей веткой локального репозитория.

1. Дальнейшие изменения можно загружать в удаленный репозиторий с помощью

    `git push`
    
    при этом, т.к. ветки уже связаны, нет необходимости указывать адрес назначения.