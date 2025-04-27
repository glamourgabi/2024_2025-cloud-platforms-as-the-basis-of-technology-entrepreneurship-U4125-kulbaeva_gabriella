# Лабораторная работа №2 «Исследование Cloud Run»
**University:** [ITMO University](https://itmo.ru/)  
**Faculty:** [FTMI](https://ftmi.itmo.ru/)  
**Course:** [Cloud platforms as the basis of technology entrepreneurship](https://itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/)  
**Year:** 2024/2025  
**Group:** U4125  
**Author:** Kulbaeva Gabriella Ruslanovna  
**Lab:** Lab2  
**Date of create:** 27.04.2025  
**Date of finished:**  

## Ход работы  

### Шаг 1: Создание Cloud Run сервиса
Для начала работы с **Cloud Run** я создала сервис.  

<img width="1231" alt="лаб2 1" src="https://github.com/user-attachments/assets/c07c5965-b961-4238-bf87-8288de6a8616" />  

### Шаг 2: Тестирование Cloud Run сервиса
После развертывания я протестировала сервис, зайдя по предоставленной ссылке. Сервис успешно запустился.  

<img width="1231" alt="лаб2 2" src="https://github.com/user-attachments/assets/9529c0d2-2e60-4736-b87f-2c25d07262f3" />  

Логи:  

<img width="1231" alt="лаб2 3" src="https://github.com/user-attachments/assets/6b8093e1-eed2-45d2-b980-3b24f111f2f5" />

### Шаг 3: Изменение порта на 8090
Внесла изменения в конфигурацию Cloud Run и настроила порт с **8080** на **8090**. Успешно!  

<img width="1231" alt="лаба2 6" src="https://github.com/user-attachments/assets/bc5abc00-978b-46d3-ab0e-74c08858c43d" />

<img width="1231" alt="лаба2 7" src="https://github.com/user-attachments/assets/2b655ac3-63f0-4d6a-9d39-3b331aa0d10b" />  

### Шаг 4: Разделение трафика между версиями
Я настроила разделение трафика между двумя версиями сервиса, указав пропорцию **40/60**. Это позволяет гибко управлять нагрузкой и тестировать различные версии приложения.

<img width="1231" alt="лаба2 8" src="https://github.com/user-attachments/assets/8f8fb175-c39b-4324-bbb5-3eee87202e2e" />   

### Шаг 5: Анализ работы сервиса после изменения трафика
Проверила работу обеих версий. Обе версии чувствовали себя хорошо.  

<img width="1231" alt="лаба2 9" src="https://github.com/user-attachments/assets/106a80b7-98f7-4a4a-b023-10a38e302570" />

<img width="1231" alt="лаба2 10" src="https://github.com/user-attachments/assets/c2e37947-30ff-486e-9144-355d8b74b8b4" />  

### Шаг 6: Удаление ресурсов
Удалила всё!
<img width="1231" alt="лаба2 11" src="https://github.com/user-attachments/assets/ae3e9850-a0c6-4d22-bb78-d22a2ec72c80" />  







