
# «Запуск приложений в K8S»


### Задание 1


*Создать Deployment приложения, состоящего из двух контейнеров — nginx и multitool. Решить возникшую ошибку.* 
*После запуска увеличить количество реплик работающего приложения до 2.*

*Продемонстрировать количество подов до и после масштабирования.*

*Создать Service, который обеспечит доступ до реплик приложений из п.1.*

*Создать отдельный Pod с приложением multitool и убедиться с помощью curl, что из пода есть доступ до приложений из п.1.*



Создаем Namespace:

![](img/1.png)

![](img/2.png)

Пишем манифест Deployment , состоящего из двух контейнеров — nginx и multitool:

![](img/3.png)

Запускаем:

![](img/4.png)

Проверяем:

![](img/5.png)

Увеличиваем количество реплик до двух:

![](img/6.png)

Результат:

![](img/7.png)

После масштабирования стало два пода: 

![](img/8.png)


Пишем манифест Service с именем nginx-multitool-svc в namespace netology.

![](img/9.png)

Запускаем:

![](img/10.png)

Проверем сервисы в namespace netology: 

![](img/11.png)

Пишем манифест отдельного пода multitool в namespace netology.

![](img/12.png)

Применяем:

![](img/13.png)

Проверяем поды в namespace netology: 

![](img/14.png)

С помощью curl, проверяю, есть ли из пода multitool доступ до приложений:


![](img/15.png)

![](img/16.png)


### Задание 2


*Создать Deployment приложения nginx и обеспечить старт контейнера только после того, как будет запущен сервис этого приложения.*

*Убедиться, что nginx не стартует. В качестве Init-контейнера взять busybox.*

*Создать и запустить Service. Убедиться, что Init запустился.*
*Продемонстрировать состояние пода до и после запуска сервиса.*



Создаем манифест Deployment приложения nginx, который запустится только после запуска сервиса. В качестве Init-контейнера
используем busybox:

![](img/17.png)

Применяем:

![](img/18.png)

Проверяем запущен ли Pod: 

![](img/19.png)

Pod не запущен и находится в состоянии Init:0/1.


Создаем манифест Service:

![](img/20.png)

Применяем:

![](img/21.png)

Проверяем запуск под nginx:

![](img/22.png)

Ссылка на манифесты:

https://github.com/dmistus/Kubernetes_03/tree/main/src
 





