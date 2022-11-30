[![Build status](https://ci.appveyor.com/api/projects/status/anf3nhurf4c9eeut/branch/master?svg=true)](https://ci.appveyor.com/project/hiiamvalya/patternscarddelivery-f9b6a/branch/master)

# Домашнее задание к занятию «2.3. Patterns»

В качестве результата пришлите ссылку на ваш GitHub-проект в личном кабинете студента на сайте [netology.ru](https://netology.ru).

Все задачи этого занятия нужно делать **в разных репозиториях**.

[Шаблон для ДЗ](https://github.com/netology-code/aqa-code/tree/master/patterns).

**Важно**: если у вас что-то не получилось, то оформляйте issue [по установленным правилам](../report-requirements.md).

**Важно**: не делайте ДЗ всех занятий в одном репозитории. Иначе вам потом придётся достаточно сложно подключать системы Continuous integration.

## Как сдавать задачи

1. Инициализируйте на своём компьютере пустой Git-репозиторий.
1. Добавьте в него готовый файл [.gitignore](../.gitignore).
1. Добавьте в этот же каталог код ваших автотестов.
1. Сделайте необходимые коммиты.
1. Добавьте в каталог `artifacts` целевой сервис: `app-card-delivery.jar` для первой задачи, `app-ibank.jar` для второй задачи — см. раздел Настройка CI.
1. Создайте публичный репозиторий на GitHub и свяжите свой локальный репозиторий с удалённым.
1. Сделайте пуш — удостоверьтесь, что ваш код появился на GitHub.
1. Удостоверьтесь, что на AppVeyor сборка зелёная.
1. Поставьте бейджик сборки вашего проекта в файл README.md.
1. Ссылку на ваш проект отправьте в личном кабинете на сайте [netology.ru](https://netology.ru).
1. Задачи, отмеченные как необязательные, можно не сдавать, это не повлияет на получение зачёта.
1. Если вы обнаружили подозрительное поведение SUT, похожее на баг, создайте описание в issue на GitHub. [Придерживайтесь схемы при описании](../report-requirements.md).

## Настройка CI
    
Настройка CI осуществляется аналогично предыдущему заданию, за исключением того, что файл целевого сервиса может называться по-другому. Для второй задачи вам также понадобится указать нужный флаг запуска для тестового режима.

## Задача №1: заказ доставки карты (изменение даты)

Вам необходимо автоматизировать тестирование новой функции формы заказа доставки карты:

<img width="626" alt="order (2)" src="https://user-images.githubusercontent.com/107319978/204903165-17ffec48-f73d-4998-aace-f00e679fe09d.png">

Требования к содержимому полей, сообщения и другие элементы, по словам заказчика и разработчиков, такие же, они ничего не меняли.

Примечание: личный совет — не забудьте это перепроверить, никому нельзя доверять 😈

Тестируемая функциональность: если заполнить форму повторно теми же данными, за исключением «Даты встречи», то система предложит перепланировать время встречи:

<img width="365" alt="replan" src="https://user-images.githubusercontent.com/107319978/204903214-955380c5-dae8-4a4a-8dfa-8a399793c6c1.png">

После нажатия кнопки «Перепланировать» произойдёт перепланирование встречи:

<img width="365" alt="success" src="https://user-images.githubusercontent.com/107319978/204903279-5dfe0e19-343e-489f-a196-3dec50c51272.png">

**Важно:** в этот раз вы не должны хардкодить данные прямо в тест. Используйте Faker, Lombok, data-классы для группировки нужных полей и утилитный класс-генератор данных — см. пример в презентации. 

Утилитными называют классы, у которых приватный конструктор и статичные методы.

Обратите внимание, что Faker может генерировать не совсем в нужном для вас формате.
