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

| Компонент             | Почему выбираем |
|-----------------------|-------------------------|
| **Vertex AI LLM API** | SaaS-доступ к современной LLM без администрирования GPU. Платим только за токены. |
| **Cloud Run**        | Быстрое деплой-to-URL, автоматическое масштабирование с 0 → N, поминутная тарификация. |
| **Cloud Firestore**  | Без-ops NoSQL БД, хватит для сессий и истории генераций. |
| **Cloud Storage**    | Статические ассеты и резервные копии данных. |
| **Cloud Logging / Monitoring** | Нативная observability, нужна на всех этапах. |
| **GKE Autopilot** (прод) | Стабильно выдерживает нагрузку >> 1000 запросов в секунду, подходит для взрослой версии продукта. |

---

# 4. Экономическая модель

| Этап | Нагрузка (запросов в день) | Ключевые ресурсы | Месячная оценка, USD |
|------|---------------------------|------------------|----------------------|
| **MVP** | 100 req/day (тесты команды) | Vertex AI LLM: ≈ 450 K токенов → \$18<br>Cloud Run: 1 vCPU 512 MB × 4 ч → \$6<br>Firestore/Storage/Logs → \$3 | **\$27** |
| **Партнёрское тестирование** | 1 000 req/day | Vertex AI LLM: ≈ 4,5 M токенов → \$180<br>Cloud Run autoscale (~35 ч vCPU) → \$25<br>Firestore (5 GB), Storage → \$7<br>Cloud Logging/Monitoring → \$10 | **\$222** |
| **Прод** | 20 000 req/day | Vertex AI LLM: ≈ 90 M токенов → \$3 600<br>GKE Autopilot (3 nodes n2d-4) → \$750<br>Cloud Load Balancer → \$30<br>Firestore (100 GB) → \$60<br>BigQuery аналитика → \$200<br>Monitoring & Logs → \$40 | **≈ \$4 680** |  


---

# 5. Как растём  

| Этап | Что меняется | Почему |
|------|--------------|--------|
| **MVP** | Один контейнер в Cloud Run, внешняя LLM API. | Самое быстрое и дешевое время-to-market. |
| **Тестирование** | Добавляется Firestore для истории, Cloud Scheduler (ночные экспорт-backup). Cloud Run остаётся. | Нужно хранить результаты, сохранять логи, делать аналитику партнёрских сценариев. |
| **Прод** | Перепрыгиваем на GKE Autopilot + Cloud Load Balancer; вводим BigQuery и Memorystore для кеширования. | Высокая QPS, нужна горизонтальная масштабируемость A/B-deployment и дешёвый аналитический storage. |

---

# 6. Риски и пути снижения затрат

* **Основная статья расходов** – вызовы Vertex AI.  
  → кешировать популярные промпты, использовать температурные и токен-лимиты.  
* **Логи** быстро растут.  
  → жизненный цикл: автоснижение до Coldline через 30 дней.  
* **Сетевые расходы**.  
  → хранить медиа в том же регионе, где крутится compute, настроить CDN для статических страниц.

---





