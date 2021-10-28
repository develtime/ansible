# Установка и настройка Elasticsearch, Kibana, Logstash и Filebeat

1. Плейбук `site.yml` устанавливает и настраивает Elasticsearch, Kibana и Filebeat
2. Параметры запуска `ansible-playbook site.yml -i inventory/prod.yml`
3. В инвентаре содержатся три группы хостов `elasticsearch`, `kibana`, `app` и `logstash`
4. В плейбуке содержатся тэги `elastic`, `kibana`, `filebeat` и `logstash`, примеры использования:
    - `ansible-playbook site.yml -i inventory/prod.yml --tags elastic` установит только `Elasticsearch`
    - `ansible-playbook site.yml -i inventory/prod.yml --tags kibana` установит только `Kibana`
    - `ansible-playbook site.yml -i inventory/prod.yml --tags filebeat` установит только `Filebeat`
    - `ansible-playbook site.yml -i inventory/prod.yml --tags logstash` установит только `Logstash`
    - `ansible-playbook site.yml -i inventory/prod.yml -e fb_setup_dashboards=true --tags filebeat` установит `Filebeat` и загрузит дашборды в `Kibana`
