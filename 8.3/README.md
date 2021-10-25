# Установка и настройка Elasticsearch, Kibana и Filebeat

1. Плейбук `site.yml` устанавливает и настраивает Elasticsearch, Kibana и Filebeat
2. Параметры запуска `ansible-playbook site.yml -i inventory/prod.yml`
3. В инвентаре содержатся три группы хостов `elasticsearch`, `kibana` и `filebeat`
4. В плейбуке содержатся тэги `elastic`, `kibana`, `filebeat` и `filebeat_setup`, примеры использования:
    - `ansible-playbook site.yml -i inventory/prod.yml --tags elastic` установит только `Elasticsearch`
    - `ansible-playbook site.yml -i inventory/prod.yml --tags kibana` установит только `Kibana`
    - `ansible-playbook site.yml -i inventory/prod.yml --tags filebeat` установит только `Filebeat`
    - `ansible-playbook site.yml -i inventory/prod.yml --skip-tags filebeat_setup` установит все, пропустив загрузку дашбордов в `Kibana`
5. Переменные имеющиеся в плейбуке:
   - `elk_stack_version` - задает значение устанавливаемой версии `ELK`
   - `elk_es_port` - порт по умолчанию для `Elasticsearch`
   - `elk_kbn_port` - порт по умолчанию для `Kibana`
   - `elk_es_addresses` - содержит массив IP адресов формирующийся из хостов группы `elasticsearch`
   - `es_master_node` - имя мастер ноды `Elasticsearch`
   - `es_node_name` - задает имя ноды `Elasticsearch` для текущего хоста
   - `es_package_name` и `es_package_url` - задает значение имени пакета и ссылки на него для `Elasticsearch`
   - `kbn_package_name` и `kbn_package_url` - задает значение имени пакета и ссылки на него для `Kibana`
   - `fb_package_name` и `fb_package_url` - задает значение имени пакета и ссылки на него для `Filebeat`
   - `fb_modules` - задает список модулей для `Filebeat`