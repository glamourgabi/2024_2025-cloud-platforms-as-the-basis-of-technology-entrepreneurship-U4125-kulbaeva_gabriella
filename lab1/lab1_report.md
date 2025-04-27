# Лабораторная работа №1 «Обзор Google Cloud и исследование основных сервисов»
**University:** [ITMO University](https://itmo.ru/)  
**Faculty:** [FTMI](https://ftmi.itmo.ru/)  
**Course:** [Cloud platforms as the basis of technology entrepreneurship](https://itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/)  
**Year:** 2024/2025  
**Group:** U4125  
**Author:** Kulbaeva Gabriella Ruslanovna  
**Lab:** Lab1  
**Date of create:** 27.04.2025  
**Date of finished:**  

## Ход работы  
### Шаг 1: Получение доступа к Google Cloud  
Здесь получила доступ и необходимые права  
### Шаг 2: Создание Service Account  
### Шаг 3: Создание VM
<img width="1224" alt="лаба1 1" src="https://github.com/user-attachments/assets/0857b913-0bc1-42c5-a854-514775090112" />
<img width="1224" alt="лаба1 2" src="https://github.com/user-attachments/assets/331265a4-7eef-4320-baa8-11fcae7c7e73" />  

### Шаг 4: Привязка Service Account к VM  
Привязала к VM свой сервисный аккаунт, чтобы VM могла использовать права, назначенные сервисному аккаунту.  
После этого подключилась к VM через **SSH**.

<img width="1224" alt="лаба1 3" src="https://github.com/user-attachments/assets/b182a9a5-c02e-4be1-8e67-c6e597ed2fd8" />  

### Шаг 5: Работа с Google Cloud Storage и утилитой gsutil  
Выполнила несколько команд с помощью утилиты **gsutil**:  
* Сначала проверила доступ к бакету  
* Потом создала директорию для хранения файлов через mkdir  
* Скопировала 3 файла из бакета в директорию на VM. Всё успешно!
 
<img width="1224" alt="лаб1 4" src="https://github.com/user-attachments/assets/5cdd809c-a353-4b83-8c62-7a2bbcfca92d" />
<img width="1113" alt="лаба1 5" src="https://github.com/user-attachments/assets/35a02a3d-9370-4c25-94e2-7935d372ca0d" />  

### Шаг 6: Изменение роли Service Account  
В разделе IAM & Admin изменила роль сервисного аккаунта на Compute Viewer.  
<img width="1231" alt="лаб1 6" src="https://github.com/user-attachments/assets/9d505346-aa4b-4c67-b15e-5769e2c9f50d" />  

### Шаг 7: Повторная попытка копирования файлов  

Пытаемся еще раз скопировать, есть ошибка, всё хорошо!  

<img width="1231" alt="лаб1 8" src="https://github.com/user-attachments/assets/74e3a8f2-5708-4799-9a56-660ece9c146e" />  

### Шаг 8: Удаление созданных ресурсов    
После выполнения лабы все удалила!  

<img width="1231" alt="лаб1 9" src="https://github.com/user-attachments/assets/71fd5c2a-6cde-4793-8654-2e91b1f0ca44" />
