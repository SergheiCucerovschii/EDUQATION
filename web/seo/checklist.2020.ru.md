ТЕХНИЧЕСКИЕ:
  - Оптимизация скорости загрузки:
    - Фронт:
      - Уменьшение / обработка картинок
      - Сжатие ресурсов
      - Оптимизация content / code (text/html ration) - 15% +
    - Бэк:
      - Выбор (при разработке) - качественной платформы
      - Настройка кэширования сайта (если высокий трафик)  
  - СКАНИРОВАНИЕ "на вирусы":
    - вредные скрипты могли попасти внутри вашего сайта разными путями:
      * установили "бесплатный" плагин или тему (или крякнутый)  
      * не правильно настроили защиту форм и т д
      * взломали
    - вредные скрипты могут нанесть ущерб разного характера сайту (замедлить, создать ГК (говно ссылки), атаковать другие сайты), есть ситуации когда из-за них владельцам блокировали даже учетную запись как на хосте так и в рекламных кампаниях  
    - инструменты проверки - полон интернет (напр - https://sitecheck.sucuri.net/), некоторые дают даже "сертификат" того что сайт исправлен
     
       
КЛЮЧЕВЫЕ СЛОВА:
  - Поиск:
    - Фразы от 2-х до 5 слов
    - Изучить частотные и менее частотные
    - Сборка ядра
    - Распределение слов по корзинам
    - * Инструменты:
      - Google Trends
      - Google Keyword Planner
      - Yandex Wordstat
    - определение "стоп слов" 
    - определение "отрицательных слов"
    - распределение фраз и слов по рубрикам и по страницам (по типу страниц сайта)   
  - Применение:
    1. В URL ( ex.: /moi-slova-uchavstvuiut-v-url ) 
    2. В теге **title** ( ex.: ```<title>Moi Frazy i slova</title>``` )
    3. В тегах **h1,h2,h3** ( ex.: ```<h1>Moi Frazy i slova</h1>``` )
    4. В акцентированном тексте **strong, em** ( ex.: ```v tekste <stronh>Moi Frazy i slova</strong>``` )
    5. В якорях (ссылках)  **a** ( ex.: ```v tekste <a href="URL">Moi Frazy i slova</a>``` )
    6. В атрибутах **alt** ( ex.: ```<img alt="Moi Frazy i slova" ... >``` )
    7. В мета и микроданных 

Общение с роботами:
 - robots.txt:
   - Запретить скан служебных страниц
   - Запретить скан тех частей сайта что в разработке
   - Запретить скан удаленных страниц
   - Разрешить скан ресурсов (css, js, картинок)
 - sitemap.xml:
   - указать список важных адресов сайта
   - указать приоритетность свежих, важных страниц 
   - подавить приоритетность ненужных страниц
   - указать частоту изменения
   - * желательно найти вариант автоматизации генерирования карты XML
 - meta - robots (частичный синоним robots.txt):
   - указать запрет на скан не важных страниц
   - запретить индексирование - дубликатов
   - рекомендую так же ознакомится и автоматизировать по возможности:
     * Noimageindex,Noarchive,Nosnippet,Unavailable_after
 - validation:  проверить - все ли необходимые страницы сканируются или индексируются (например через - google search console)
 - crawl errors: проверить - если поисковик не выдает ошибки скана
 - устроить "замануху", с некоторыми "менее рисковыми" страницами можно производить эксперименты:
   * обновлять часто содержимое страницы - проверить "уловит" ли Google эту частоту
 * **НЕ ЗЫБЫАЙТЕ!!!** о том что роботы "не любят" ошибки, алгоритм поиска будит "минусовать" за каждую ошибку!

МИКРОРАЗМЕТКА (Rich snippets):
  - Schema.org Структурированные данные:
    - идентифицировать самые важные сущности вашего проекта (Product,Organization,Person,Review...)
    - Вбить требуемые поля (а так же поля важные для проекта - например - если компания предоставляет териториальные услуги - то привязыть сущности к адресу/названию города )
    - Добавить в виде JSON-LD (скриптом или плагином) автоматизацию структурирования
    - проверить валидатором : https://search.google.com/structured-data/testing-tool
  - open graph (facebook snippets):
    - уточнить тип материала (website, audio, video, music, profile, etc...)
    - добавить правильное image, title, description - особонно на тех страницах что будут продвигаться в соц сетях
  - tw cards (twitter snippets) и другие менее популярные форматы (ими можно заняться после подключения основных):
     
ССЫЛКИ:
  - Правильно отмеченный внутри сайтовые ссылки:
    - canonical - ссылки на оригинал
    - alternate - ссылки на альтернативные варианты материалов (напр - языковой вариант)     
    - amphtml - ссылки на вариант оптимизированных под AMP страницы
    - prev/next/index/... - ссылки многостраничных материалов
    - nofollow - ссылки по которым нельзя "переходить" (поисковики не любят большое кол-во таких ссылок)
    - noindex - не идексировать (не обрабатывать и не выдавать) эту страницу
  - Правильно отмеченные внешние ссылки (исходящие) - ссылки которые ведут на  тематично - не релевантные сайты - сказываются плохо и на ваш сайт
    

РЕДИРЕКТЫ:
  - поисковая система не любит редиректы (по возможности стоит избегать)
  - Применять 301 - для www.domain.example -> domain.example в случае если у вас сайт и так и так открывается - иначе поисковик будет оценивать как два сайта
  - Применять 301 - для всех важных страниц, адреса которых были отредактированны после того как они набрали уже историю в поисковике
  - Если сайт переехал в "новый дом" (домен поменялся), оставить еще месяца 2-3 редирект 301 с старого сайта, так как это передест трафик и вес и опыт новому домену


ДОМЕН:
  - Длину доменного имени выбирать не сильно большой
  - Не включать политику конфиденциальности данных о вледельце домена (это сказывается отрицательно на уровне доверия) - можно проверить инструментами типа WHOIS
  - Домен арендовать на длинный срок - по возможности (продлить если уже есть), влияет на степень доверия
  - Приобрести домен - у которого была уже хорошая репутация (время положительного пребывания доменя на рынке - дает толчек!)

ПРОТОКОЛ:
  - использовать режим HTTPS (TLS), однозначно влияет на рэнкинг особенно тех сайтов которые связанны с комерческими операциями
  - сертификаты SSL/TLS покутать в зависимости от сферы деятельности и от авторизованных поставщиком (большинтсво провайдеров доменов/хостинга - продают и сертификаты)


ПРАВИЛЬНЫЙ КОНТЕНТ:
  - ТОПОЛОГИЯ:
    * расположить важный контент в "видных/доступных" местах:
      1. У начала страницы (над "горизонтом")
      2. В правильных семантичных секциях (header,main,nav,...) 
      3. В элементах что придают важность/выделяют (h1-h3,strong,a,...)
      4. Убедиться в том что пользователь может увидеть важное желательно при нулевом усилие - zero effort content (любой скроллинг, клик, касание - или другие действия, для того чтобы увидеть контент, отменят его важность) 
 

(main source: https://moz.com/learn/seo/off-site-seo)

РЕФЛЕКСИЯ (назвал так потому что вы смотрите на сайт - другими - сторонними глазами):
  * ССЫЛКИ:
    - количество ссылок (DLKAF, ссылочная масса приводящая людей на сайт - именно на ваш конкретный домен)
    - тематическая релевантность (PLLF,важны те ссылки что ближе к теме продвигаемого сайта, страницы)
    - важность домена ссылок (не забудьте о том что ссылатся на сайт - с нулевого домена - нет смысла)
    - диверсия (лучше чтобы больше сайтов ссылались на ваш, нежели много ссылок с одного и того же сайта)
     
    ТАКТИКА:
      * Хорошее решение до сих пор обменятся ссылками партнерами чьи сайты на высоте
      * Разместить ссылки на разных тематичных платформах, форумах, блогах
      * Рекламные ссылки неплохи,  но их стоит добавлять туда где ваша ссылка не капля в море (к слову - один анонс=ссылка на портале анонсов где их в день добавляют пот сотне тысяч - это очень малый вес)
      * Регистрация в тематичных директориях сайта
      * Если сайт связан с брендом, на него можно ссылаться и не напрямую, просто упомянать он нем в разным комментиариях, постах и т д, без прямой ссылки (DLBF)
      * Если акцент ставится на соц сети (темы хорошо идущие в соц сетях - это услуги, продукты, новости) - то количество репостов, впечатлений (лайков) и так далее - тоже влиет на продвижение ссылки (SM)
      * !!! ЛУЧШЕ не покупать ссылки на "колограмм" так как такие сайты (которые предоставляют подобные услуги) очень быстро обнаруживаются и их репутация падает, что не только приведет к "негодности" ссылок что вы купили, но так же может привести к "порче" вашему сайту
      * Проверить ТОПОЛОГИЮ ссылок ведущих на ваш сайт, на сайте где они размещенны (не скрыты ли они)

ПОВЕДЕНЧЕСКИЕ:
  * за частую этот пункт вводит в заблуждение так как многим СЕО специалистам и владельцам сайтов кажется что тут не чего сделать - так как поведение людей не подвластно им :) :
    - очень важно установить инструменты отслеживая людей на сайте (напр Google Analytics, Google Tag Manager, Facebook Pixel, etc...) 
    - очень важно тщательно настроить инструменты (ведь при стандартных настройках - вы получите гору цифр и графиков - из которых иногда очень тяжело увидеть важные аспекты)
    - важно отфильтровать данные которые не соответствуют целевой аудитории
    - важно отследить "пути" и цепочки событий - связанные с поведением людей, от момента попадения на сайт - до момента завершения взаимодествия
    - важно отметить цели (клик, просмотр, покупка, ...) - иначе коефициент конверсии не будет соответствовать реальности
    - если есть опыт / или специалист по JS - можно дописать свои фрагменты логики
    - важно настроить авто отчеты - дабы не составлять их в ручную