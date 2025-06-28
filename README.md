# HAProxy Load Balancing

**Домашнее задание 1**  
**Тема:** Кластеризация и балансировка нагрузки  
**Задание:**  
1. Запуск двух простых Python-серверов на портах 8000 и 8001  
2. Установка и настройка HAProxy  
3. Конфигурация нагрузочного балансировщика на уровне TCP (Layer 4) с алгоритмом round-robin  
4. Проверка работоспособности (скриншоты конфига, прослушиваемого порта и теста)

## Файлы

- `02_haproxy_cfg.png` — конфигурационный файл HAProxy  
- `03_haproxy_listen.png` — вывод `ss -tunlp | grep haproxy`  
- `04_haproxy_test.png` — результат теста round-robin  

## Запуск

```bash
# Запуск Python-серверов
python3 -m http.server 8000 --directory ~/srv1 &
python3 -m http.server 8001 --directory ~/srv2 &

# Перезапуск HAProxy
sudo systemctl restart haproxy

# Тест round-robin
./test_haproxy.sh
