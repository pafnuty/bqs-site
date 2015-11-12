---
title: Структура  
description: Документация к Bitrix Quick Start, Структура и назначение файлов
template: index

---


# Структура и назначение файлов Bitrix Quick Start

<a href="https://github.com/pafnuty/bqs-site/blob/dev/content/documentation/structure.md" class="btn btn-mini" target="_blank">Редактировать страницу</a>


Разработку сайта на Bitrix, актуальной версии следует производить в папке local. 
[Читаем для чего и зачем нужна папка local](http://dev.1c-bitrix.ru/community/blogs/vad/local-folder.php).

**Типовая структура файлов проекта на QuickStart выглядит так:**

```md
auth/
bitrix/
└── php_interface/
    ├── this_site_support.php
    └── site_closed.php
favicons/
includes/
local/ 
├── codenails/
│   ├── css/
│   ├── images/
│   ├── js/
│   ├── less/
│   └── tools/
├── components/
├── gadgets/
├── logs/
├── modules/
├── php_interface/
│   ├── cn_log.php
│   └── init.php
└── templates/
    ├── .default
    └── rename_me
        ├── description.php
        ├── footer.php
        └── header.php
personal/
├── cart/
├── order/
├── profile/
└── subscribe/
search/
.htaccess_example
404.php
favicon.ico
index.php
robots.txt
```


## auth/{#auth}
Папка, для тех, кто забывает положить форму для восстановления пароля. Ну и авторизация по умолчанию.

##bitrix/php_interface/{#php_interface}
- **this_site_support.php** — Информация о партнёре и техподдержке (нужна по требованиям монитора качества). Отображается внизу формы авторизации в админке. Этот файл не подхватывается из local, возможно со временем это исправят.
![Информация о поддержке и партнёре](https://dl.dropboxusercontent.com/u/8142395/this_site_support.png "Информация о поддержке и партнёре"){.col-margin}
- **site_closed.php** — [Красивая заглушка](http://jsfiddle.net/eoq287rd/embedded/result/) для отключенной публички. К сожалению пока этот файл не подхватывается из папки local.

## favicons/{#favicons}

Папка с различными иконками под все устройства о основные ОС, нужны для красивого отображения сайта при добавлении в закладки, на рабочие столы и т.д.

Для генерации иконок очень хорошо подходит сервис [realfavicongenerator](http://realfavicongenerator.net/).

<div class="tip">
    :facepunch: Не забываем пнуть ленивого дизайнера, чтоб отрисовал нормальные иконки.
</div>

## includes/{#includes}
В этой папаке располагаются включаемые области и прочие php-файлы, которые контент-менеджер или клиент может отредактировать через веб-интерфейс битрикса, из публичной части.

## local/{#local}
Основная папка проекта. 

### local/codenails/{#codenails}
В этой папке содержатся файлы, относящиеся к вёрстке (стили, скрипты, картинки шаблона), а так же включаемые области и php-файлы, отвечающие на ajax-запросы.

#### local/codenails/css/
- template_styles.css — Скомпилированный CSS-файл, который подключается в шаблон. 
- Так же в эту папку складываем все CSS-файлы, которые не требуется включать с LESS по различным соображениям (*к примеру не требующий правок файл какого-нибудь плагина для jQuery*). Файлы подключаются в автоматическом через cnAsset.


#### local/codenails/images/

- В эту папку кладём картинки шаблона. 
- Если нужны временные картинки, не нужно копировать их из макета, [используйте сервис](http://imgholder.ru/) (и плагин для SublimeText) **не захламляйте папку.**
- **ie_logo.png** - не удаляем картинку, она отображается в админке (см раздел про минитор качества)

#### local/codenails/js/

- Сюда складываем js-файлы и jquery-плагины, необходимые для работы шаблона, которые будут подгружаться через автозагрузчик cnAsset.

#### local/codenails/less/

- Сюда складываем LESS-файлы проекта.

### local/components/

Папка для размещения собственных компонентов.

### local/gadgets/

Папка для размещения гаджетов рабочего стола (*возможно когда-нибудь мы будем туда класть загортовки гаджетов*)

### local/logs/
Папка для хранения логов (туда автоматом записывается лог, создаваймый классом CNLog).

### local/modules/
Папка для размещения собственных модулей.

### local/php_interface/
- **cn_log.php** — Класс для ведения наглядного лога, нужен для удобной отладки того, что тяжело отладить (*пример вызова в init.php*)
- **init.php** — init.php сайта, в который подключается дефолтный init.php. Так же там присутствуют некоторые, полезные во всех проектах, функции.


### local/templates/
- **.default** — папка с шаблонами компонентов.
- **rename_me** — папка с шаблоном сайта (*не забываем переименовать*).
    - **header.php** — шапка сайта.
    - **footer.php** — подвал сайта.
    - **description.php** — описание шаблона.

## search/
Папка, отвечающая за поиск по сайту и формирование карты сайта (*не sitemap.xml, а непонятная сущность, формирующаяся из меню сайта*).

### .htaccess_example
Не забываем удалить этот файл, предварительно прочитав и сделав, как написано. Тут лежит пример правильной склейки зеркал для apache.

### 404.php
404-я страничка.