# HomeworkDjango
В настоящем проекте были выполнены домашние задания по урокам 19.2 и 20.1. 

Далее на онлайн уроке 20.2 с Алексеем Останиным от 24.02.2024 были добавлены разбирвемые темы (шаблоны, подшабломы, фильтры), на примере шаблона, добавленного из bootstrap.com (версия 5.3)

* Выведение всех продуктов на главную страницу через цикл {% for product in object_list %} / {% endfor %} в файле products_list.html

* Постраничное выведение каждого продукта на отдельную страницу, через применение файла product_detail.html и контроллера product_detail (в views)

* Настойка медиафайлов через настройку путей:
  
  1) + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT) в catalog/ urls
        
  2) В Settings:
            MEDIA_URL = '/media/'
            MEDIA_ROOT = BASE_DIR / 'media'
     
  3) Создание папки tamplatetags, добавление в него файла my_tags  с прописыванием в нем Кастомных шаблонных тегов для отображения media  файлов
     
  4) Прописывание  шаблонных фильтров или  шаблонных тегов в шаблонах . Например: {{ product.preview | media_filter }}
     То есть чтобы можно было писать 
    <a href="{{ object.image|mymedia }}" />
     вместо 
    <a href="/media/{{ object.image }}" />
 
* Задание 1
Для начала работы над задачей выполните первые шаги:

 Настройте виртуальное окружение.
 Создайте новый Django-проект.
  
mkdir project
 — создаем новую директорию для проекта.
 
cd project
 — переходим в созданную директорию.
 
python3 -m venv env
 — создаем виртуальное окружение.
 
pip3 install django
 — устанавливаем пакет Django.
 
pip3 freeze >  requirements.txt
 — сохраняем список зависимостей.
 После создания виртуального окружения создайте проект с помощью команды:
 - django-admin startproject config .

* Задание 2
После успешного создания проекта сделайте первую настройку. Для этого:

 Создайте первое приложение с названием 
catalog
 - python manage.py startapp catalog
.
 Внесите начальные настройки проекта.
 Сделайте настройку урлов (URL-файлов) для нового приложения.
* Задание 3
Подготовьте два шаблона для домашней страницы и страницы с контактной информацией.

Для создания шаблонов лучше использовать UIkit Bootstrap. Это удобный набор элементов, которые уже стилизованы и готовы к использованию. UIkit Bootstrap помогает избежать самостоятельной верстки макетов.

Если возникнут проблемы при создании собственного интерфейса, возьмите за основу данный шаблон: https://github.com/oscarbotru/.

* Задание 4
В приложении в контроллере реализуйте два контроллера:

 Контроллер, который отвечает за отображение домашней страницы.
 Контроллер, который отвечает за отображение контактной информации.
 
* Дополнительное задание
Реализуйте обработку сбора обратной связи от пользователя, который зашел на страницу контактов и отправил свои данные для обратной связи.

При этом шаблон должен отправлять POST-запрос. Для этого необходимо заполнить его:

<form method="post">
	{% csrf_token %}
	<input name="name" />
	<input type="submit" value="Отправить" />
</form>

Очень важно не забыть добавить 
{% csrf_token %}
Он отвечает за безопасную обработку запроса и блокирует вредоносные и опасные для целостности данных пользователя запросы.

Также, чтобы запрос отправлялся методом POST, в форме необходимо указать соответствующий метод 
<form method="post">

* Команды для создания фикстур:
* Общая:
  python -Xutf8 manage.py dumpdata catalog -o fixture/data_catalog.json
    
* По каждой таблице отдельно:
  
  python -Xutf8 manage.py dumpdata catalog.product -o fixture/catalog_product.json
  
  python -Xutf8 manage.py dumpdata catalog.category -o fixture/catalog_category.json

  


