# Elastic Stack (Kibana + ElasticSearch + Filebeats + MetricBeat, HeartBeat, APM)


#### Subir docker com imagens locais atualizadas
```
docker-compose up -d --build
```

#### Acessar Kibana (se aparecer kibana not yet ready, aguarde um pouco)
[http://localhost:5601/]

- Acessar Analytics/Discover (Ignorar erro de timestamp porque de inicio não tera dados de log)
- Metrics e APM já cria index, mas pode criar outros por exemplo filebeat-* e escolher @timestamp
- Analytics/Dashboard e possivel criar e baixar paineis personalizados 
- No menu Observability é possível ver os dados de forma geral e detalhada sobre Logs, metricas, APM, etc


#### Derrubar containers e remover volumes
```
docker-compose down -v
```

#### Caso queira modificar a versão do filebeat

##### Baixar filebeat para buscar arquivo caso não tenha configurado
- Escolher versão: https://www.elastic.co/pt/downloads/beats/filebeat
- curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-{VERSAO}-x86_64.tar.gz
- tar xzvf filebeat-{VERSAO}-x86_64.tar.gz
- copie o arquivo da filebeat.yml da pasta raiz para o seu projeto

##### Configurações básicas no arquivo filebeat.yml
setup.kibana:host: "kibana:5601"
output.elasticsearch:hosts: ["es01:9200"]
output.elasticsearch:username: "elastic"
output.elasticsearch:password: "changeme"

##### Mudar no arquivo Dockerfile o link da versão Debian do filebeats e atualizar imagem
```
docker build -t amsousa95/nginx-beats .
```

#### Subir projeto com imagens locais atualizadas
```
docker-compose up -d --build
```
