University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Cloud platforms as the basis of technology entrepreneurship](https://itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/)  
Year: 2024/2025  
Group: U4125  
Author: **Kulbaeva Gabriella Ruslanovna**  
Lab: **Разработка инфраструктуры MVP AI-приложения**  
Date of create: 06.05.2025  
Date of finished:   

---

# 1. Идея приложения

**Story** – веб-сервис для креаторов.  
Пользователь вводит 3-10 ключевых слов → сервис за секунды генерирует связный сторителлинг-текст (пост, сценарий ролика, подпись к фото).  

---

# 2. Архитектура  
<img width="720" alt="лаба4" src="https://github.com/user-attachments/assets/ce972b7a-b05c-4da7-b516-e25d3a451c0f" />  

---

# 3. Ресурсы  

| Компонент                 | Почему выбираем |
|---------------------------|-----------------|
| **Vertex AI LLM API**     | SaaS-доступ к современной LLM без администрирования GPU. Платим только за токены. |
| **Cloud Run**             | Быстрый деплой-to-URL, автоматическое масштабирование с 0 → N, поминутная тарификация. Подходит как для MVP, так и для продакшена. |
| **Cloud Firestore**       | Без-ops NoSQL БД, хватает для хранения сессий, истории генераций и метаданных пользователей. |
| **Cloud Storage**         | Статические ассеты, изображения, резервные копии. Дёшево и надёжно. |
| **Cloud Logging / Monitoring** | Нативный сбор логов и метрик, необходим для наблюдаемости, отладки и аналитики. |
| **Cloud Load Balancer**   | Распределяет трафик между инстансами Cloud Run, обеспечивает стабильность при высокой нагрузке. |
| **Memorystore (Redis)**   | Кеширует повторяющиеся запросы, снижает расходы на вызовы LLM и ускоряет отклик. |
| **BigQuery**              | Используется для аналитики пользовательского поведения и обработки больших объёмов данных. |


---


### 4. Экономическая модель

| Этап                     | Нагрузка (запросов в день) | Ключевые ресурсы                                                                                                                                       | Месячная оценка, USD |
|--------------------------|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| **MVP**                  | 100 req/day (тесты команды) | Vertex AI LLM: ≈ 450 K токенов → \$18<br>Cloud Run: 1 vCPU 512 MB × 4 ч → \$6<br>Firestore / Storage / Logs → \$3                                     | **\$27**             |
| **Партнёрское тестирование** | 1 000 req/day              | Vertex AI LLM: ≈ 4,5 M токенов → \$180<br>Cloud Run autoscale (~35 ч vCPU) → \$25<br>Firestore (5 GB), Storage → \$7<br>Cloud Logging / Monitoring → \$10 | **\$222**            |
| **Прод**                 | 20 000 req/day              | Vertex AI LLM: ≈ 90 M токенов → \$3 600<br>Cloud Run (автоматическое масштабирование) → \$40<br>Cloud Load Balancer → \$30<br>Memorystore (Redis) → \$60<br>Firestore (100 GB) → \$60<br>BigQuery аналитика → \$200<br>Monitoring & Logs → \$40 | **≈ \$4 030**         |





