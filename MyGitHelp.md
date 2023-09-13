# Что такое Git?
Инструкция доступна по команде **git help git**. Позволим автору программы ответить на этот вопрос:

>git - the stupid content tracker

>мерзавец - тупой следящий за наполнением 😆

# Документация

Полная документация доступна по ссылке:

https://git-scm.com/docs

# Как пользоваться Git?
0. При первом использовании Git после установки на компьютер
используем команды:

    `git config --global user.name <your_name>`

    `git config --global user.email <your_email>`

1. Инициализируем репозиторий

    `git init`

2. Проверяем статус репозитория *желательно* после каждого изменения

    `git status`

3. Добавляем измененные файлы в новую фиксацию

    `git add`

4. Фиксируем изменения

    `git commit -m <comment>`

    - Для первой фиксации рекомендуется использовать комментарий
"init commit".

    - Для фиксации изменений без необходимости добавлять файлы в индекс используем флаг   "-a", например

        `git commit -a -m <comment>`

        `git commit -am <comment>`
5. Проверяем журнал 

    `git log`

6. Переходим к одной из фиксаций

    `git checkout <commit_number>`

7. Возвращаемся к актуальному состоянию

    `git checkout main`

8. Сравниваем текущее состояние с одной из фиксаций

    `git diff <commit_number>`

9. Создаем новую ветку
    
    `git branch <branch_name>`

10. Смотрим существующие ветки
    
    `git branch`

11. Переходим к другой ветке

    `git checkout <branch_name>`


12. Выполняем слияние веток

    `git merge <branch_name_to_merge_with_HEAD>`

13. Удаляем ненужные ветки
    
    `git branch -d <branch_name_to_delete>`

# Полное описание команд

`git init`
https://git-scm.com/docs/git-init

`git status`
https://git-scm.com/docs/git-status

`git add`
https://git-scm.com/docs/git-add

`git commit`
https://git-scm.com/docs/git-commit

`git log`
https://git-scm.com/docs/git-log

`git checkout`
https://git-scm.com/docs/git-checkout

`git diff`
https://git-scm.com/docs/git-diff

`git branch`
https://git-scm.com/docs/git-branch