# Дипломный проект Netology

## Цель проекта

Развертывание отказоустойчивой инфраструктуры сайта в Yandex Cloud.

## Используемые технологии

- Yandex Cloud
- Terraform
- Ansible
- Nginx
- Application Load Balancer
- Zabbix
- Elasticsearch
- Kibana
- Filebeat
- NAT Gateway
- Snapshot Backup

## Состав инфраструктуры

### Виртуальные машины

| Имя | Назначение |
|-------|------------|
| bastion | SSH-доступ во внутренний контур |
| web-1 | Веб-сервер nginx |
| web-2 | Веб-сервер nginx |
| elasticsearch | Хранилище логов |
| kibana | Визуализация логов |
| zabbix-server | Мониторинг |

## Схема сети
```
Internet
    |
ALB
 /   \
web1 web2
  \   /
 Elasticsearch
      |
   Kibana

Zabbix
Bastion
```
Инфраструктура состоит из публичного и приватного сегмента.

Публичный сегмент:
- Bastion
- Kibana
- Zabbix
- Application Load Balancer

Приватный сегмент:
- web-1
- web-2
- Elasticsearch

Доступ в интернет из приватного сегмента осуществляется через NAT Gateway.

## Отчет

Подробный отчет расположен в:

[docs/report.md](docs/report.md)
