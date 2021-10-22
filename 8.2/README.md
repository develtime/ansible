# Установка и настройка Elasticsearch и Kibana

1. Плейбук `site.yml` устанавливает и настраивает Elasticsearch и Kibana
2. Параметры запуска `ansible-playbook site.yml -i inventory/prod.yml`
3. В инвентаре содержатся две группы хостов `elasticsearch` и `kibana`
4. В плейбуке содержатся тэги `java` `elastic` и `kibana`, примеры использования:
    - `ansible-playbook site.yml -i inventory/prod.yml --tags java` установит только `Java JDK`
    - `ansible-playbook site.yml -i inventory/prod.yml --tags elastic` установит только `Elasticsearch`
    - `ansible-playbook site.yml -i inventory/prod.yml --tags kibana` установит только `Kibana`
5. Переменные имеющиеся в плейбуке:
   - `java_jdk_version` - задает значение устанавливаемой версии `Java JDK`
   - `elastic_version` - задает значение устанавливаемой версии `Elasticsearch`
   - `kibana_version` - задает значение устанавливаемой версии `Kibana`
   - `elastic_url` - задает URL до сервиса `Elasticsearch`, применяется к хостам `kibana`