# Config Server

Este repositório contém os arquivos de configuração externa usados pelos serviços do projeto [Microservices Demo](https://github.com/Lucas-319/microservices-demo
).

## O que é
- Armazena propriedades consumidas pelo Spring Cloud Config Server (hospedado no módulo [service-main](https://github.com/Lucas-319/service-main)).
- As propriedades aqui são versionadas e aplicadas aos serviços em tempo de inicialização.

## Estrutura
- `service-task.properties`: propriedades do serviço de tarefas.
- `service-notification.properties`: propriedades do serviço de notificação.

## Como se integra no projeto
Este repositório fornece os arquivos de configuração consumidos pelo Config Server hospedado em [service-main](https://github.com/Lucas-319/service-main). O fluxo é:

1. O [service-main](https://github.com/Lucas-319/service-main) sobe o Spring Cloud Config Server e o Eureka.
2. O [service-task](https://github.com/Lucas-319/service-task) e o [service-notification](https://github.com/Lucas-319/service-notification) configuram `spring.config.import=configserver:http://service-main:8888/config` para buscar as propriedades deste repositório.
3. Em tempo de inicialização, cada serviço carrega as propriedades conforme seu `spring.application.name` e perfil ativo.