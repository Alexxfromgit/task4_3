# task4_3

**Задание 4.3 - Simple back-up**

Условие задания:

    Создайте bash скрипт task4_3.sh, который создает бекапы заданной директории. Этот скрипт должен:
    • Принимать 2 аргумента командной строки:
        a. Абсолютный путь к директории c которой необходимо создать бекап
        b. Число бекапов, которые необходимо сохранить
    • Бекапы должны сохраняться в директории /tmp/backups/ 
    • При достижении заданного количества бекапов, скрипт производит удаление самых старых бекапов (т.е. в директории с бекапами должно находится не более n бекапов указанной директории)
    • Файлы бекапов должны быть запакованы tar и сжаты gzip.
    • Название файла архива должно иметь формат  <dir name>*.tar.gz
    Под “*” подразумевается любая удобная вам информация, по которой вы можете потом сортировать файлы бекапов. Это может быть например нумерация (1,2,3 и т.д.) или время в любом удобном вам формате (например 2018-03-21-145536).
    • Пример запуска скрипта: “./task4_3.sh /etc/default 3”, приводит к:
        a. Созданию файла /tmp/backups/etc-default.tar.gz, в котором заархивировано содержимое директории /etc/default (т.е. “/” в пути директории должен заменяться на “-”, а корневой каталог в пути - отбрасываться)
        b. В директории с бекапами находится не более 3 архивов (файлов) /tmp/backups/etc-default*.tar.gz.
        
Дополнительные требования:

    1. При каждом запуске скрипта должен либо создаваться бекап, либо выводиться сообщение об ошибке.
    2. В скрипте необходимо предусмотреть проверку, что в командной строке передано правильное количество аргументов, а также что директория с которой необходимо создать бекап существует. В случае выявления проблем скрипт должен вывести сообщение в stderr и завершиться с ненулевым кодом возврата
    3. Шаблон имени архивов для ротации: <archived dirname with dashes>*.tar.gz
    4. Баш скрипты с выполненными заданиями должны быть загружены в гитхаб репозитарий c названием ‘task4_3’
    5. В гитхаб репозитарии ‘task4_3’ должен содержаться один скрипт task4_3.sh

Проверка результатов:

    • Для каждого запуска будет использоваться отдельная ВМ (ОС ubuntu xenial 16.04 server, образ). Т.е. считайте, что до вас никто ничего не настраивал. Скрипт будет запущен из-под суперпользователя (root). ВМ имеет доступ в интернет.
    • В ВМ будет склонирован репозиторий с заданием ( например https://github.com/user/task4_3, если репозиторий будет иметь другое имя, то задание будет автоматически помечено как невыполненное.
    • Автоматически будет запущен скрипт  ‘task4_3.sh’ из корневой папки репозитория (если скрипт будет называться иначе или будет находиться в подпапке - он запущен не будет, соответственно, задание будет автоматически помечено как невыполненное)
    • Скрипт будет запускаться с различными наборами параметров и должен корректно отрабатывать следующие ситуации:
        ◦ Не все параметры были переданы
        ◦ Было передано более чем 2 параметра
        ◦ Папка или файл, бекап которого нужно создать, не существует
        ◦ Параметр, отвечающий за количество бекапов, которые нужно хранить,  не является корректным
        ◦ Если папка, где будут храниться бекапы, не существует, ее необходимо создать
        ◦ Путь к папке, передаваемой в скрипт в виде параметра, может содержать пробелы и спец. символы
    • Все сообщения об ошибках должны выводиться в stderr. Если сообщение будет отправлено в stdout, то оно не будет выловлено проверкой, и как следствие, будет считаться, что скрипт не удовлетворяет заданным критериям.
    • Имя бекапа должно строго соответствовать заданной маске с учетом регистра (если передано /etc/default, то имя файла архива должно начинаться с  etc-default и заканчиваться на .tar.gz )
    • Подразумевается, что оба параметра, передаваемые в скрипт, связаны между собой: т.е. количество бекапов для хранения относится только к бекапу переданной папки, а не ко всем бекапам в /tmp/backup.
    • Если вы решили использовать нумерацию в именах файлов (etc-default.1.tar.gz, etc-default.2.tar.gz и т.д.) то следует реализовать общепринятую иерархию архивов: самый “свежий” должен иметь имя etc-default.tar.gz, предыдущий - etc-default.1.tar.gz, созданный 2 запуска назад - etc-default.2.tar.gz и т.д.
