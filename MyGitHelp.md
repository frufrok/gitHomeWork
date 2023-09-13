# Что такое Git?
Инструкция доступна по команде `git help git`. Позволим автору программы ответить на этот вопрос:

>git - the stupid content tracker

>мерзавец - тупой следящий за наполнением 😆

# Кто написал эту инструкцию?

Эту инструкцию написал этот git:

![Some git](https://s76vlx.storage.yandex.net/rdisk/e16cc65bf021aa21f271befb253c37ece675c09a4d51368040417e7fd2035e8e/6501b541/MmrzcZdFqBsuAaoM02nEu40aFHfZ0HM_lAf7zYILhQHxiIFT0qKpWgtrCKdpk-bV6YBQeWAXmvoNQtPFH2A-Qg==?uid=0&filename=ProfilePhoto.jpg&disposition=inline&hash=&limit=0&content_type=image%2Fjpeg&owner_uid=0&fsize=703241&hid=f164b8e4c3a79ed4f380efcc4b63f79d&media_type=image&tknv=v2&etag=7d8a3eb5b87a753a717e76489650507f&rtoken=1Sg4MehunQxo&force_default=no&ycrid=na-01180b052967da50384b14e8f4459542-downloader19e&ts=6053d4ff71240&s=ac4096c9bb58ba36008cd3f50d43b30dcd92ff7755979c3c7e723b80142b421c&pb=U2FsdGVkX18Rj4DFUTrJsumDG55K3fZdhKz5syjJbvHLUWZJTr9O77YtUwrZDYoNe7Ixq1T5MXlzTYjGqa_c8zorhmzKoklnJhQvJQzYM5w)

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
5. Проверяем журнал (простой и в стиле графа)

    `git log`

    `git log --graph`

6. Смотрим существующие ветки
    
    `git branch`

7. Создаем новую ветку
    
    `git branch <branch_name>`

8. Переходим к любому из состояний/веток

    `git checkout <commit_number>`
    `git checkout <branch_name>`

9. Возвращаемся к главной ветке

    `git checkout main`

    или то же самое, но если вы ментально застяли где-то в первой 19 века:

    `git checkout master`

10. Сравниваем текущее состояние с другим

    `git diff <commit_number>`

    `git diff <branch_name>`

11. Выполняем слияние веток

    `git merge <branch_name_to_merge_with_HEAD>`

12. Удаляем ненужные ветки (второй вариант - для удаления ветки до слияния её с другими)
    
    `git branch -d <branch_name_to_delete>`

    `git branch -D <branch_name_to_delete>`

# Клонирование приватных репозиториев

Тут я чуть вперед забежал, каюсъ, но иначе пришлось бы качать все через облако или выставлять на всеобщее обозрение мое творчество на GitHub путем создания публичного репозитория.

При клонировании приватных репозиториев через терминал необходимо использовать PAT - Personal Access Token - персональный токен доступа или личный знак доступа. Для генерации токена необходимо перейти в настройки аккаунта на GitHub:

https://github.com/settings/tokens

Для нормальной работы с приватными репозиториями необходимо указать следующие сферы применения:
repo - работа с репозиториями
delete_repo - удаление репозиториев

Для клонирования приватного репозитория необходимо модифицировать команду `git clone` следующим образом:

`git clone https://<PAT>@github.com/<UserName>/<RepoName>`

Здесь в промежуток между протоколом `https://` и адресом репозитория `github.com/<UserName>/<RepoName>` добавлен токен в формате `<PAT>@`, где `<PAT>` - токен, `@` - разделитель между токеном и адресом.

После клонирования приватного репозитория необходимо пройти процедуру аутентификации на GitHub через браузер как и при обычной работе с публичными репозиториями или с помощью токена.

Срок действия токена рекомендуется ограничить, после истечения срока его действия токен можно регенерировать и использовать снова. Токен можно посмотреть один раз при генерации, далее его пара (скважина от ключа) хранится на GitHub, а сам токен - нигде, кроме тех мест, куда его сохранит сам пользователь.

Конечно, самая глупая идея - сохранить токен в текстовом файле где-то в репозитории, ведь тогда он при любом вызове команды `commit` попадает в историю (`log`), а если запустить `push`, то еще и в удаленный репозиторий (хорошо, что он приватный). В этом случае необходимо регенерировать токен и скомпрометированный вариант перестанет работать.

# Работа с изображениями

Для добавления в разметку изображения используем следующую конструкцию:

`![<description>](<path or link>)`

`<description>` - это описание изображения, отображаемое в том случае, если невозможно отобразить само изображение;

`<path or link>` - это ссылка или путь к файлу изображения.

# Решение конфликтов

При слиянии веток, в которых изменения касались одних и тех же строк кода, возможен конфликт. Для решения конфликта необходимо выбрать один из вариантов слияния (___**принять существующие изменения | принять входящие изменения | принять оба изменения (предпочтительный вариант) | показать разницу**___) и после решения конфликта обязательно зафиксировать изменения командой `git commit`.

Пример конфликта:

![Скриншот примера конфликта при слиянии (домашнее задание)](https://s373vla.storage.yandex.net/rdisk/72ee7c288dd7e89044e9d33cbeb1ee6b74f035945cbd0875058b12d20372766b/6501b56f/MmrzcZdFqBsuAaoM02nEu2q_XlcrxkHI77HJcbg_qUkd5R4hmUUeas2ePgf_bDI8r9YI29UkB7jJ12qPiIqdCg==?uid=0&filename=MergeConflictSample.png&disposition=inline&hash=&limit=0&content_type=image%2Fpng&owner_uid=0&fsize=125419&hid=c51c344026b54501683c021f5059aaba&media_type=image&tknv=v2&etag=0a0e8557770759d1486bacb83bbe42d9&rtoken=c9F5kR9WZTVR&force_default=no&ycrid=na-55b1cad094abe2f1837a332bc51f9869-downloader19e&ts=6053d52b4f9c0&s=9ae34c7d062f933f6c25564bc61ce9eda8c163327764775859e66136bbf60f6e&pb=U2FsdGVkX19vHEj9IeTaTbbBfTapl3zd2nCdLZ0k-yTqcxHIZMxJW4kc3MuI6c9lEe0Oo6AMZzo3_IIG7wxhH3kI0Inc_FzrFpvRQGJpv3g)

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