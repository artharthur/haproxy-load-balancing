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

## Задание 2

**Тема:** HTTP Weighted Round-Robin на L7 по домену example.local

**Файлы:**
- `05_hosts.png` — строка `127.0.0.1 example.local` в `/etc/hosts`  
- `06_servers.png` — три Python-сервера на портах 8000, 8001, 8002 (`ps aux | grep http.server`)  
- `07_haproxy_cfg2.png` — блок для задания 2 в `/etc/haproxy/haproxy.cfg` (HTTP-фронтенд перед TCP)  
- `08_test_example.png` — вывод теста с `Host: example.local`, показывающий пропорцию 2:3:4  
- `08_test_other.png` — вывод `curl -I http://localhost/`, где видно `HTTP/1.0 400 Bad Request`
