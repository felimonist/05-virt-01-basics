
Домашнее задание к занятию "1. Введение в виртуализацию. Типы и функции гипервизоров. Обзор рынка вендоров и областей применения." -Богданов Антон Викторович

Задание 1.

Аппаратная виртуализация - гипервизор ставится непосредственно на сервер и взаимодействует с аппаратным обеспечением сервера напрямую. Гостевая ОС полностью отделяется от управления инфраструктурой хоста, она не требует никаких изменений, и не подозревает, что запущена в виртуальном окружении.

Паравиртуализация - гипервизор ставится на ОС и взаимодействует с аппаратным обеспечением сервера через прослойку ввиде ОС. 
Гостевая ОС модифицируется для коммуникации с гипервизором с целью улучшения производительности и эффективности работы. В ядре гостевой ОС модифицируются невиртуализуемые инструкции на гипервызовы, которые напрямую отправляются в гипервизор. 

Виртуализация на основе ОС (контейнерная виртуализация) - ядро ОС поддерживает несколько изолированных экземпляров пространства пользователя и эти экземпляры с точки зрения пользователя полностью идентичны реальному серверу.


Задание 2.

1. физические сервера - Высоконагруженная база данных, чувствительная к отказу; Системы, выполняющие высокопроизводительные расчеты на GPU;
Данные сервисы критичны к производительности и лучше не использовать виртуализацию, как прослойку на которую необходимо тратить ресурсы.
2. паравиртуализация - Windows системы для использования бухгалтерским отделом
Ввиду токо что системы не нагружены и их много, лучше использовать паравиртуализацию для оптимизиции ресурсов серверов.
3. виртуализация уровня ОС - Различные web-приложения
Готовая среда для приложений позволяет быстро их запускать и с помощью различных оркестраторов горизонтально масштабировать.

Задание 3.

1.VMWare VSphere - позволяет создавать кластера серверов для большей отказоустойчивости, имеет множество сторонних решения для бэкапа. Позволяет автоматизировать создания и обслуживание виртуальных машин.

2.KVM - бесплатное решение, производительное. Есть множество систем виртуализации на базе KVM, например Proxmox. Так же есть множество инструментов для резервного копирования, либо можно написать самому и бэкапить машины через скрипты.

3.MS HyperV - бесплатное решение, так же при его использовании с windows инфраструктурой можно немного съэкономить на лицензиях.

4.Docker - можно запустить на подавляющем большинстве дистрибутивов Linux. Сборку и развёртывание контейнеров можно автоматизировать например через docker-compose.

Задание 4.Трудно обслуживать (бэкап, автоматизация развертывания готовых образов серверов, обновление гипервизоров), управлять ресурсами.  
Если бы был выбор, я бы использовал гетерогенную среду в таком виде:
Верхний уровень - аппаратная виртуализация для оптимального управления ресурсами и возможности централизованного бэкапа виртуальных машин.
Нижний уровень - контейнеризация, для быстрого разворачивания сервисов и экономии ресурсов.
Так же оба уровня возможно автоматизировать.
