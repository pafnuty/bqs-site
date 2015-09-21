Title: Правила оформления CSS-кода
Description: Правила оформления CSS-кода в Bitrix Quick Start
Template: index  

----


# Правила оформления CSS-кода

<div class="tip">
    :construction: Страница не закончена. <a href="https://github.com/pafnuty/bqs-site/blob/dev/content/code/css.md" class="btn btn-small" target="_blank">Редактировать</a>
</div>

## Комментирование кода
```less
    /* =================================================
       Каталог */
    /* ================================================= */
        .catalog {
            &-item {

             } //.catalog-item
        } //.catalog
        // Тут может быть сколько угодно строк кода

    /* =================================================
       Корзина */
    /* ================================================= */
        .basket {
            &-item {

             } //.basket-item
        } //.basket
        // Тут ещё 500 строк кода
```

## Организация LESS-файлов
Имя файла следует начинать с двухзначной цифры, после которой идёт тире и пояснительное название файла, понятное для человека. Это даёт возможность нормального восприятия структуры файлов и приводит структуру проектов в общий порядок.
- **00-09** — файлы, которые не попадают в результирующий CSS (миксины, переменные и т.д.)
- **10-19** — файлы, которые обязательно должны присутствовать, задают костяк шаблона (сетка, кнопки, иконки, формы и т.д.) и оформляют стандартные элементы html.
- **20-79** — различные дополнительные файлы, отвечающие за оформление конкретных кусков вёрстки (меню, модальные окна, слайдеры, хлебные крошки, каталог и т.д.).
- **80-main.less** — основной файл стилей сайта, сюда как правило пишется всё, что относится к конкретному сайту, это уникальный для каждого проекта файл, если куски кода кочуют в этом файле из проекта в проект - значит   надо выносить их в отдельный файлы в пределах имён 20-79.
- **90-helpers.less** — различные хелперы типа `.clearfix` и прочие стили, помогающие привести вёрстку в нужный вид, е создавая излишнего кода.


## Стиль LESS (и CSS) кода: 
- **Основной стиль «лесенкой»**, где каждое свойство отдельная строка.
- **Для визуального отделения используется табулятор**, но не пробел.
- **Группы свойств перечисляемых через запятую, располагаются в отдельной строке.**
- **Все «подправила» оформляются по тем же правилам, что и «основные».**
- **Нужно группировать правила в единый блок с использованием расширенного синтаксиса LESS** (включая символ `&`).
- **Используемые миксы (mix) располагаются в конце списка свойств.**
- Для служебных комментариев в тексте лучше использовать однострочный LESS-комментарий `//` вместо CSS-комментария `/* */`.
- **Используйте переменные**. <br>Переменные для размеров, для цвета, для отступов и т.д. Это экономит кучу времени. 
Не придётся запоминать коды цветов, размеры отступов (особенно если вёрстка не по сетке). Название переменной запомнить всегда проще, ведь это ВЫ её написали :)
- **Создавайте миксины чаще** <br>Если вы пишете код и возникает ощущение deja vu, смело добавляйте миксин. Это значительно сэкономит время в последующих проектах. Не пытайтесь сразу сделать миксин идеальным, с кучей параметров. Он должен быть простым и понятным. Впоследствии вы будете его расширять и делать более универсальным.
- **Используйте параметризацию миксинов** <br>Любой миксин, который вы используете, можно запараметризовать. Во-первых, это удобно. Во-вторых, это экономит получившийся результат в css. 
Когда мы добавляем миксин, пусть это будет оформление кнопки, а далее простыми css-свойствами меняем ему размеры или цвет, то в скомпилированном css в селекторе будут сначала правила, описанные в миксине, а затем уже те, которые вы описали. Получается ненужное дублирование css-свойств. Избежать этого можно, вставляя значения параметров в миксин: так миксин скомпилируется сразу с нужными параметрами. И не забывайте ставить параметрам значения по умолчанию.


## Инструменты для автоформатирования кода, настройка параметров