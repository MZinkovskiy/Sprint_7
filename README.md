# Sprint_7
Финальный проект 7-го спринта: тестирование API

Финальный проект 7 спринта
Тебе предстоит протестировать API учебного сервиса Яндекс.Самокат. Его документация: qa-scooter.praktikum-services.ru/docs/.
Перед тем как писать тесты, протестируй API вручную в Postman. Это поможет разобраться, как работают запросы.
Чтобы вспомнить материал спринта, загляни в шпаргалки.
Подготовка
Перед тем как приступить к заданиям:
Создай Maven-проект.
Назови проект Sprint_7.
Подключи JUnit 4, RestAssured, Allure.
Протестируй ручки
Проверь, что они корректно работают и выдают нужные ошибки.
Создание курьера
Проверь:
курьера можно создать;
нельзя создать двух одинаковых курьеров;
чтобы создать курьера, нужно передать в ручку все обязательные поля;
запрос возвращает правильный код ответа;
успешный запрос возвращает ok: true;
если одного из полей нет, запрос возвращает ошибку;
если создать пользователя с логином, который уже есть, возвращается ошибка.
Логин курьера
Проверь:
курьер может авторизоваться;
для авторизации нужно передать все обязательные поля;
система вернёт ошибку, если неправильно указать логин или пароль;
если какого-то поля нет, запрос возвращает ошибку;
если авторизоваться под несуществующим пользователем, запрос возвращает ошибку;
успешный запрос возвращает id.
Создание заказа
Проверь, что когда создаёшь заказ:
можно указать один из цветов — BLACK или GREY;
можно указать оба цвета;
можно совсем не указывать цвет;
тело ответа содержит track.
Чтобы протестировать создание заказа, нужно использовать параметризацию.
Список заказов
Проверь, что в тело ответа возвращается список заказов.
Отчёт Allure
Сгенерируй его и запушь в репозиторий.
Обрати внимание: всю папку target коммитить не нужно. Чтобы добавить в коммит только отчёт, можно перейти в папку проекта в консоли и выполнить команды:
# добавляем папку с отчётом Allure к файлам. Ключ -f пригодится, если папка target указана в .gitignore
git add -f .\target\allure-results\.
# выполняем коммит
git commit -m "add allure report"
# так отправишь файлы в удалённый репозиторий
git push 
Не забудь: тесты должны быть независимыми. Все данные нужно удалять после того, как тест выполнится. Если для проверки нужен пользователь, создай его перед тестом и удали после. 
Дополнительное задание
Это задание можешь выполнить по желанию: оно не повлияет на оценку за основную часть, но поможет дополнительно попрактиковаться. 
Протестируй ручки:
Удалить курьера
С методом DELETE можно работать так же, как с другими методами. 
Проверь:
неуспешный запрос возвращает соответствующую ошибку;
успешный запрос возвращает ok: true;
если отправить запрос без id, вернётся ошибка;
если отправить запрос с несуществующим id, вернётся ошибка.
Принять заказ
Проверь:
успешный запрос возвращает ok: true;
если не передать id курьера, запрос вернёт ошибку;
если передать неверный id курьера, запрос вернёт ошибку;
если не передать номер заказа, запрос вернёт ошибку;
если передать неверный номер заказа, запрос вернёт ошибку.
Получить заказ по его номеру
Проверь:
успешный запрос возвращает объект с заказом;
запрос без номера заказа возвращает ошибку;
запрос с несуществующим заказом возвращает ошибку.
В запросах 2 и 3 дополнительного задания нужно передавать query-параметры.
Query-параметры — это параметры в форме «имя параметра — значение». 
Строка запроса с параметрами выглядит так: some_url?parameter1=1&parameter2=some_value.
Из чего она состоит:
ручка some_url,
параметр parameter1 с числовым значением 1,
parameter2 со строковым значением some_value.
После пути к ручке нужно поставить ?. Параметры отделяются друг от друга знаком &.
Посмотри, как передать такой запрос в RestAssured:
        
            given()
                // здесь всё как обычно
        .auth().oauth2("введи_сюда_свой_токен")
                // в этих строчках параметры переданы в запрос
        .queryParam("parameter1", "1")
        .queryParam("parameter2", "some_value")
        .get("some_url")
        .then() 
          ... // дальше всё как обычно 
Обрати внимание на метод queryParam: туда передают имя параметра и его значение.
Как видишь, эту строчку можно повторять несколько раз — столько, сколько нужно передать параметров.
Как будут оценивать твою работу
Для основного задания
Нейминг элементов корректный. Если не помнишь правила, посмотри в шпаргалку.
В pom.xml нет ничего лишнего.
Тесты лежат в src/test/java.
Для каждой ручки тесты лежат в отдельном классе.
Написаны тесты на ручку «Создать курьера».
Написаны тесты на ручку «Логин курьера».
Написаны тесты на ручку «Создать заказ».
Написаны тесты на ручку, которая получает список заказов.
Для всех шагов автотестов должна быть использована аннотация @Step.
Сделан отчёт с помощью Allure. Не забудь закоммитить его.
В тестах проверяется тело и код ответа.
Все тесты независимы.
Необходимые тестовые данные создаются перед тестом и удаляются после того, как он выполнится.
В тестах нет хардкода.
В проекте используется Java 11.
Для дополнительного задания 
Правила те же, что и для основного задания. Что ещё:
Написаны тесты на ручку «Удалить курьера».
Написаны тесты на ручку «Принять заказ».
Написаны тесты на ручку «Получить заказ по его номеру».
Как сдать работу
Прочитай инструкцию. 
Прежде чем отправить проект
Проверь себя по чек-листу. Он поможет разобраться: проект правильно загружен на GitHub или нет. Если загрузишь решение неправильно, ревьюер вернёт его на доработку.
