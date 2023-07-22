# Introdução a resiliência

Resiliência, quando aplicada a software, é um conjunto de estratégias intencionalmente adotadas para garantir a adaptação do sistema quando ocorrem falhas. Em outras palavras, é a capacidade do software de se recuperar e continuar operando de maneira aceitável mesmo diante de situações inesperadas ou eventos de erro.

Quando um sistema não é resiliente, qualquer falha ou exceção pode fazer com que o software pare de funcionar corretamente ou até mesmo falhe completamente, resultando em uma experiência negativa para o usuário e possíveis perdas para o negócio.

Ao projetar e desenvolver software com resiliência, os desenvolvedores planejam com antecedência as possíveis falhas que podem ocorrer e criam estratégias para lidar com elas. Em vez de apenas lançar exceções e encerrar a execução, o software resiliente pode tomar ações alternativas, como retornar respostas parciais ou temporárias, usar caches, alternar para serviços secundários ou adiar tarefas para uma execução posterior.

Um exemplo prático de resiliência seria o sistema de pagamentos de um site de comércio eletrônico. Se o gateway de pagamento estiver temporariamente indisponível, um sistema resiliente poderia ter um plano B, como armazenar as transações em fila e tentar processá-las novamente quando o gateway estiver de volta online. Dessa forma, mesmo durante uma falha temporária, o site pode continuar a funcionar, permitindo que os usuários façam compras e minimizando o impacto negativo nas vendas.

Em suma, a resiliência no software é fundamental para garantir uma experiência confiável aos usuários, minimizar perdas e impactos negativos causados por falhas e permitir que o sistema continue funcionando mesmo em condições adversas. Planejar, testar e implementar estratégias de resiliência é uma prática importante para qualquer aplicação crítica ou serviço online.

## Proteger e ser protegido

O conceito de "proteger e ser protegido" na resiliência de sistemas distribuídos refere-se à ideia de que cada sistema deve tomar medidas para se proteger contra falhas e, ao mesmo tempo, ser cuidadoso para não sobrecarregar outros sistemas do ecossistema, evitando o chamado "efeito dominó".

Para que um sistema seja resiliente, ele deve adotar mecanismos de auto-preservação, ou seja, garantir que, quando enfrentar dificuldades, ainda seja capaz de operar com qualidade e fornecer respostas adequadas, mesmo que de forma parcial ou temporária. Isso envolve a implementação de estratégias para lidar com possíveis falhas, como a capacidade de retornar códigos de erro adequados, avisando que está enfrentando problemas e que não pode atender a solicitação no momento.

Além de proteger a si mesmo, o sistema também deve considerar o impacto de suas ações nos demais sistemas que fazem parte do ecossistema distribuído. Ao fazer solicitações a outros sistemas, é importante que ele evite ser egoísta e não sobrecarregue os sistemas vizinhos com uma grande quantidade de requisições, especialmente se eles já estão enfrentando dificuldades. Isso significa que, em vez de insistir continuamente em obter uma resposta, um sistema resiliente pode optar por aguardar um tempo adequado antes de fazer uma nova tentativa, evitando o agravamento da situação e permitindo que o sistema vizinho se recupere.

O efeito dominó é um cenário a ser evitado, pois ocorre quando um sistema enfrenta problemas e sua lentidão ou falha afeta negativamente os sistemas que dependem dele, e por sua vez, isso impacta outros sistemas e assim por diante, criando uma cadeia de problemas que pode levar a uma falha generalizada de todo o ecossistema.

Portanto, proteger e ser protegido é uma abordagem de resiliência que visa promover a saúde e estabilidade do ecossistema como um todo. Cada sistema é responsável por se preservar e evitar a propagação de falhas aos demais sistemas, criando um ambiente colaborativo em que todos trabalham juntos para minimizar o impacto de falhas e garantir a disponibilidade e qualidade dos serviços oferecidos.

## Health check

O health check, ou checagem de saúde, é uma técnica usada em sistemas distribuídos para verificar regularmente o estado de um componente ou serviço e determinar se ele está saudável o suficiente para atender a novas requisições. É uma parte essencial da estratégia de resiliência, permitindo que os sistemas protejam a si mesmos e aos outros, conforme discutido anteriormente.

O objetivo do health check é monitorar os "sinais vitais" do sistema, como tempo de resposta, disponibilidade de recursos, capacidade de acesso ao banco de dados, entre outros parâmetros relevantes para o bom funcionamento da aplicação. Esses sinais vitais podem variar dependendo do tipo de sistema e do contexto em que ele opera.

A checagem de saúde é realizada periodicamente, geralmente em intervalos regulares, para garantir que os sistemas recebam feedback contínuo sobre o seu estado. Por exemplo, um sistema pode ser configurado para fazer uma verificação a cada 10 segundos para garantir que ele esteja operacional e saudável.

Um aspecto importante do health check é que ele permite que o sistema tome decisões inteligentes sobre como responder a novas requisições com base em seu estado atual. Se um sistema estiver enfrentando problemas, ele pode retornar um código de erro (como 500 - Internal Server Error) ou um sinal claro de que está com dificuldades temporárias. Isso evita que outros sistemas sobrecarreguem um componente já em dificuldades, impedindo que o efeito dominó ocorra e minimizando o impacto das falhas.

O health check também pode ser usado para acionar mecanismos de autorecuperação ou self-healing. Por exemplo, se o sistema perceber que está lento devido a problemas no banco de dados, ele pode tomar ações para tentar resolver o problema, como reiniciar a conexão com o banco ou realizar alguma limpeza de recursos. A auto-recuperação ajuda a restaurar o sistema à sua operação normal sem intervenção manual, aumentando a resiliência e a disponibilidade do serviço.

É importante configurar o health check de forma adequada, certificando-se de que os sinais vitais monitorados refletem a saúde real do sistema e não apenas uma resposta superficial de que está "no ar". Com um health check bem projetado e implementado, os sistemas podem garantir uma operação mais estável, proteger-se de sobrecargas e ajudar a manter o ecossistema distribuído funcionando de forma harmoniosa.

## Rate limiting

O rate limiting é uma estratégia utilizada para proteger sistemas e serviços contra sobrecarga e abusos de requisições. Ele impõe um limite na quantidade de solicitações que um cliente pode fazer em um determinado intervalo de tempo. O objetivo é evitar que um cliente ou um conjunto de clientes exceda a capacidade de processamento e recursos do sistema, garantindo que o serviço permaneça disponível e funcional para todos os usuários.

A principal função do rate limiting é garantir que o sistema opere dentro de seus limites projetados. Quando um sistema é desenvolvido e implantado, geralmente são feitos testes de desempenho e estresse para determinar a capacidade máxima de requisições que ele pode atender sem degradar a qualidade do serviço. Esse valor de capacidade máxima se torna a base para definir o limite de rate limiting.

Por exemplo, se um sistema consegue lidar com 100 requisições por segundo com qualidade, o rate limiting pode ser configurado para permitir apenas até 100 requisições por segundo por cliente. Se um cliente tentar fazer mais de 100 requisições por segundo, o rate limiting entra em ação e começa a retornar respostas com erros, como um código de status 500, para indicar que o limite de requisições foi excedido.

O rate limiting é útil para evitar problemas como:

- Sobrecarga de recursos: Limitar a quantidade de requisições ajuda a evitar que os recursos do sistema, como CPU, memória e conexões com bancos de dados, sejam esgotados.

- Ataques de negação de serviço (DoS): Impede que atacantes sobrecarreguem o sistema com um grande número de requisições maliciosas, tornando-o inacessível para outros usuários.

- Garante a qualidade do serviço: Ao manter o tráfego dentro dos limites suportados, o sistema pode fornecer um nível de serviço consistente para todos os usuários, evitando quedas e tempos de resposta lentos.

Além disso, é importante destacar que o rate limiting pode ser configurado de forma mais granular, permitindo limites diferenciados para diferentes clientes ou tipos de clientes. Isso é útil para garantir que sistemas mais críticos ou clientes prioritários tenham acesso garantido mesmo em situações de alto tráfego.

O rate limiting é uma das estratégias fundamentais para a implementação de sistemas resilientes, contribuindo para a proteção contra falhas e garantindo a disponibilidade e a qualidade do serviço em ambientes de alto volume de requisições.

## Circuit breaker

O circuit breaker é uma estratégia de resiliência utilizada em sistemas distribuídos para protegê-los contra falhas e evitar que um problema em um serviço afete negativamente outros serviços que dependem dele. Essa estratégia é inspirada nos disjuntores elétricos, que protegem circuitos elétricos contra sobrecargas, evitando danos aos equipamentos.

No contexto dos sistemas de software, o circuit breaker age como um interruptor que monitora constantemente a saúde de um serviço ou sistema. Ele opera em três estados principais: fechado, aberto e meio aberto.

1. Circuito Fechado: Nesse estado, o circuit breaker permite que as requisições fluam normalmente entre os serviços, e tudo funciona como esperado. As requisições são atendidas pelo serviço de destino sem interrupções.

2. Circuito Aberto: Quando ocorre um problema em um serviço (por exemplo, ele começa a responder lentamente ou falhar), o circuit breaker entra em ação e abre o circuito. Isso significa que qualquer nova requisição direcionada a esse serviço será recusada imediatamente, sem que a requisição chegue ao serviço com problemas. Em vez disso, o circuit breaker responde com um erro 500 ou algum outro código de erro indicando a indisponibilidade temporária do serviço.

3. Meio Aberto: Após o circuit breaker abrir o circuito, ele pode permitir um número limitado de requisições para verificar se o serviço voltou ao normal. Se essas requisições forem bem-sucedidas, o circuit breaker pode fechar novamente o circuito, permitindo que o tráfego normal seja restaurado. Caso contrário, o circuito permanecerá aberto, evitando que as requisições sobrecarreguem ainda mais o serviço com problemas.

O circuit breaker é uma medida proativa para evitar que serviços sejam sobrecarregados e entrem em estado de degradação total. Ele ajuda a prevenir o chamado "efeito dominó", onde uma falha em um serviço leva a uma cascata de falhas em outros serviços dependentes, resultando em uma queda generalizada do sistema.

Além disso, o circuit breaker permite a rápida detecção e recuperação de falhas, reduzindo o tempo de espera para os usuários e diminuindo o impacto das indisponibilidades temporárias.

Essa estratégia pode ser implementada de forma manual, através de código, em sistemas mais simples. No entanto, em ambientes mais complexos, como os que envolvem arquiteturas de microserviços e service mesh, o circuit breaker pode ser configurado e gerenciado por recursos mais avançados e automatizados, como políticas de rede definidas por software.

## API Gateway

O API Gateway é um componente essencial em arquiteturas de microsserviços e sistemas distribuídos que atua como um intermediário entre os clientes (como aplicativos, dispositivos ou outros serviços) e os microsserviços subjacentes. Sua principal função é centralizar o recebimento de todas as requisições que chegam à aplicação, permitindo aplicar regras, políticas, autenticações e transformações antes de encaminhar as requisições para os microsserviços apropriados.

As principais funcionalidades e importância do API Gateway:

- **Centralização e Roteamento de Requisições:** Todas as requisições feitas à aplicação passam pelo API Gateway, que age como um ponto de entrada único para a infraestrutura de microsserviços. Isso simplifica a lógica de roteamento e distribuição de requisições entre os diferentes microsserviços, permitindo que cada um deles foque em sua própria funcionalidade específica.

- **Aplicação de Regras e Políticas:** O API Gateway é capaz de aplicar regras de negócio, políticas de acesso e autorização em todas as requisições que chegam à aplicação. Por exemplo, ele pode exigir autenticação antes de permitir o acesso a determinadas rotas ou recursos.

- **Validação e Transformação de Dados:** O API Gateway pode validar o formato dos dados enviados nas requisições e, se necessário, realizar transformações para garantir que os dados estejam em um formato adequado para os microsserviços que irão processá-los. Por exemplo, ele pode converter XML em JSON ou vice-versa.

- **Rate Limiting:** O API Gateway pode controlar a taxa de requisições recebidas, aplicando limites de taxa por cliente, IP ou outros critérios. Isso evita sobrecargas nos microsserviços e protege-os contra ataques de negação de serviço.

- **Health Check:** O API Gateway pode realizar verificações de saúde (health checks) ativas nos microsserviços, para garantir que eles estejam em funcionamento adequado antes de encaminhar as requisições. Caso um microsserviço apresente problemas, o API Gateway pode parar de direcionar tráfego para ele temporariamente, ajudando na resiliência do sistema.

- **Segurança:** O API Gateway é uma camada de defesa, ajudando a proteger os microsserviços ao aplicar políticas de segurança, filtragem de dados, controle de acesso e autenticação.

- **Log e Monitoramento:** O API Gateway pode registrar informações relevantes sobre as requisições e respostas que passam por ele, facilitando o monitoramento e análise do tráfego para fins de depuração, análise de desempenho e segurança.

- **Integração com Service Mesh:** Em arquiteturas mais complexas, como aquelas que usam um Service Mesh, o API Gateway pode ser integrado a essas infraestruturas, fornecendo funcionalidades adicionais de gerenciamento de tráfego e segurança em ambientes distribuídos.

O API Gateway desempenha um papel fundamental em garantir a resiliência, segurança e escalabilidade das aplicações baseadas em microsserviços. Ele oferece uma camada de abstração entre os clientes e os microsserviços subjacentes, permitindo que os desenvolvedores concentrem-se em suas funcionalidades específicas, enquanto o API Gateway cuida das preocupações comuns relacionadas ao gerenciamento de tráfego, segurança e transformação de dados. Além disso, sua flexibilidade e capacidade de aplicar regras específicas para cada serviço tornam-no uma peça valiosa no quebra-cabeça da arquitetura de microsserviços.

## Service Mesh

O Service Mesh é uma camada de infraestrutura que fornece recursos de gerenciamento de comunicação e controle de tráfego em ambientes distribuídos baseados em microsserviços. Ele é projetado para lidar com desafios complexos associados à comunicação entre microsserviços, como resiliência, segurança, monitoramento, controle de tráfego e resolução de problemas.

Os principais pontos sobre o Service Mesh:

- **Controle de Tráfego:** O Service Mesh atua como um intermediário entre os microsserviços, permitindo que a comunicação ocorra através de proxies (sidecars). Esses proxies gerenciam todo o tráfego entre os serviços, garantindo que as requisições sejam roteadas corretamente e fornecendo uma visão completa de como os serviços se comunicam.

- **Medição e Observabilidade:** O Service Mesh é capaz de coletar dados sobre a comunicação entre os microsserviços, como métricas de latência, erros e taxas de transferência. Essa observabilidade ajuda a detectar problemas, identificar gargalos e tomar decisões informadas sobre a infraestrutura.

- **Resiliência:** Ao controlar o tráfego de rede, o Service Mesh pode aplicar políticas como rate limiting, circuit breaking e retry policies. Isso permite que o Service Mesh proteja os microsserviços contra sobrecargas, falhas de comunicação e ajude a garantir a resiliência do sistema como um todo.

- **Segurança:** O Service Mesh pode fornecer criptografia de comunicação entre os microsserviços, garantindo que as mensagens sejam transmitidas de forma segura. Além disso, pode aplicar políticas de autenticação e autorização para controlar o acesso aos serviços.

- **Service Discovery:** O Service Mesh facilita a descoberta e registro automático de microsserviços na infraestrutura, permitindo que novos serviços sejam adicionados ou removidos dinamicamente sem afetar a comunicação entre os outros componentes.

- **Múltiplas Opções de Implementação:** Existem várias soluções e implementações de Service Mesh disponíveis no mercado, como Istio, Linkerd e Envoy. Cada uma possui suas características específicas, mas todas compartilham o objetivo de fornecer recursos avançados de gerenciamento de comunicação em ambientes distribuídos.

- **Facilidade de Configuração:** O Service Mesh abstrai muitas das complexidades associadas à comunicação entre microsserviços, permitindo que desenvolvedores e equipes de operações configurem políticas de tráfego e segurança com facilidade, sem a necessidade de modificar o código dos microsserviços.

## Comunicação assíncrona

A comunicação assíncrona é uma abordagem de troca de informações entre sistemas em que o remetente não precisa aguardar a resposta imediata do destinatário para prosseguir com suas operações. Em vez disso, o remetente envia a mensagem para um intermediário, que armazena temporariamente a mensagem até que o destinatário esteja disponível para processá-la. Essa abordagem é comparada ao conceito de entrar em uma fila de espera em uma agência bancária ou em um supermercado, onde você pode continuar com suas atividades enquanto aguarda sua vez de ser atendido.

Os principais aspectos da comunicação assíncrona:

- **Vantagens da Comunicação Assíncrona:** A comunicação assíncrona permite que os sistemas continuem operando e recebendo novas requisições, mesmo que não consigam processar imediatamente todas as solicitações recebidas. Isso evita a sobrecarga do sistema e a perda de dados, pois as mensagens são armazenadas temporariamente até que o destinatário esteja pronto para processá-las.

- **Exemplo de Comunicação Assíncrona:** um exemplo é o banco ou supermercado, onde os clientes entram em filas de espera para serem atendidos. Eles não precisam ser atendidos imediatamente, mas podem prosseguir com suas atividades enquanto aguardam sua vez. Da mesma forma, na comunicação assíncrona, os remetentes enviam mensagens e continuam suas operações sem esperar uma resposta imediata.

- **Utilização em Sistemas:** A comunicação assíncrona é particularmente útil em cenários em que os sistemas podem receber um grande número de requisições e não têm recursos para processá-las todas instantaneamente. Ao adotar a abordagem assíncrona, os sistemas podem receber as mensagens e armazená-las temporariamente, garantindo que as requisições não sejam perdidas e que sejam processadas em momentos mais adequados.

- **Message Broker:** Para implementar a comunicação assíncrona, é comum utilizar um intermediário conhecido como "message broker". O message broker recebe as mensagens dos remetentes e as armazena em filas ou tópicos, aguardando que os destinatários estejam prontos para processá-las. Exemplos de message brokers são RabbitMQ, Kafka e Amazon SQS.

- **Garantia de Entrega:** Embora a comunicação assíncrona seja eficiente em evitar a perda de dados, é essencial entender como funciona o mecanismo de garantia de entrega do message broker que está sendo utilizado. Isso pode envolver configurações de confirmações de recebimento (acknowledgment) e políticas de retry para assegurar que as mensagens sejam entregues com sucesso ao destinatário.

- **Resiliência:** A comunicação assíncrona é considerada uma prática resiliente porque, mesmo quando um sistema está temporariamente indisponível, as mensagens são armazenadas em filas pelo message broker e processadas posteriormente quando o sistema estiver novamente online. Isso reduz o risco de perda de dados e contribui para a resiliência do sistema como um todo.

## Garantia de entrega com Retry

A garantia de entrega com "retry" é uma estratégia importante para alcançar resiliência em sistemas distribuídos. Quando uma requisição é enviada para outro sistema, é essencial ter mecanismos para garantir que a mensagem seja entregue com sucesso, mesmo em situações em que o destinatário esteja temporariamente indisponível, lento ou enfrentando problemas de processamento.

Os principais aspectos da garantia de entrega com "retry":

- **Política de Retry:** A estratégia de retry envolve tentar enviar a mensagem novamente se a resposta não for recebida dentro de um determinado período de tempo. Ao enviar a mensagem novamente, o sistema emissor espera que o destinatário esteja disponível para processá-la em algum momento futuro.

- **Exponential Backoff:** O "exponential backoff" é uma técnica que implica em aumentar o intervalo de tempo entre as tentativas de retry de forma exponencial. Em vez de fazer novas tentativas em intervalos fixos, a estratégia de exponential backoff aumenta o tempo entre as tentativas progressivamente.

- **Jitter:** Para evitar múltiplas tentativas de retry simultâneas de diferentes sistemas, a adição de "jitter" (ruído) é recomendada. Com a utilização de jitter, os sistemas adicionam um pequeno valor aleatório ao intervalo de retry. Isso faz com que as tentativas de retry aconteçam em momentos diferentes, reduzindo a probabilidade de congestionamento e aumentando a chance de sucesso nas entregas.

- **Resiliência Melhorada:** A política de retry, especialmente quando combinada com exponential backoff e jitter, aumenta a probabilidade de que a mensagem seja entregue com sucesso, mesmo em cenários em que o destinatário esteja temporariamente indisponível ou sobrecarregado. Essa abordagem ajuda a garantir a resiliência do sistema como um todo e evita a perda de dados.

- **Implementação Consciente:** É importante implementar o retry com cuidado e ter em mente que, embora a estratégia possa melhorar a resiliência, não é garantido que todas as tentativas de retry tenham sucesso. É essencial definir um limite para o número de tentativas de retry e considerar cenários em que a mensagem pode ser descartada após várias tentativas sem sucesso.

- **Escolha do Message Broker:** Em cenários de comunicação assíncrona, é comum utilizar um message broker para garantir a entrega das mensagens. Ao escolher um message broker, é importante entender como ele lida com as políticas de retry e se ele suporta exponential backoff e jitter para melhorar a garantia de entrega.

## Garantia de entrega com Kafka

A garantia de entrega com Kafka é uma estratégia para garantir a resiliência e a confiabilidade na troca de mensagens entre sistemas utilizando o Apache Kafka como message broker. O Kafka é uma plataforma de streaming distribuída que permite o armazenamento e a transmissão de fluxos de dados em tempo real.

Os seguintes pontos-chave relacionados à garantia de entrega com Kafka:

- **Política de Acknowledgment (Ack):** No Kafka, ao enviar uma mensagem para um tópico (um canal de comunicação), o produtor pode optar por diferentes níveis de garantia de entrega, especificando o Ack. 
Existem três opções principais:
   
   - **Ack 0 (Fire and Forget):** O produtor envia a mensagem e não espera nenhuma confirmação (Acknowledgment) do broker de que a mensagem foi recebida com sucesso. Essa abordagem é útil para cenários em que a alta velocidade de envio é mais importante do que a garantia de entrega completa. No entanto, há o risco de perder algumas mensagens caso ocorram falhas no processo.
   
   - **Ack 1 (Leader Ack):** O produtor recebe uma confirmação (Acknowledgment) do broker líder (leader) assim que a mensagem é recebida e persistida pelo broker líder. Essa opção fornece uma garantia moderada de entrega, pois a mensagem estará disponível enquanto o broker líder estiver ativo. Se o broker líder falhar antes de replicar a mensagem para os outros brokers, pode ocorrer perda de dados.
   
   - **Ack All (Replica Ack):** O produtor recebe uma confirmação (Acknowledgment) após a replicação da mensagem em todos os brokers do cluster. Essa opção oferece a maior garantia de entrega, pois a mensagem estará disponível mesmo que um dos brokers falhe. No entanto, também é a opção mais lenta, pois requer que todas as réplicas recebam a mensagem antes de confirmar o Acknowledgment.

- **Alta Disponibilidade e Replicação:** O Kafka fornece alta disponibilidade usando replicação. Os dados dos tópicos são replicados em vários brokers dentro de um cluster Kafka. Se um broker falhar, outro broker com uma cópia replicada dos dados pode assumir. A replicação é fundamental para garantir que as mensagens não sejam perdidas em caso de falha de um broker.

- **Trade-off entre Velocidade e Garantia de Entrega:** A escolha da política de Ack depende das necessidades específicas do sistema. Se a alta velocidade de envio for prioritária, Ack 0 pode ser adequado. Se houver preocupação em não perder nenhuma mensagem importante, Ack 1 ou Ack All podem ser mais apropriados, com Ack All oferecendo a maior garantia de entrega, mas com maior latência.

- **Conhecimento do Message Broker:** Para garantir uma resiliência eficaz e a melhor escolha de Ack, é importante entender profundamente o Kafka ou qualquer outro message broker em uso. Compreender como os dados são replicados, a arquitetura do cluster e as políticas de Ack disponíveis é essencial para tomar decisões bem informadas sobre a garantia de entrega a ser adotada.

## Situações complexas e decisões de alto nível

Situações complexas e decisões de alto nível relacionadas à resiliência na arquitetura de software, com algumas provocações e considerações importantes:

- **Resiliência como Prioridade:** resiliência é extremamente importante e deve ser considerada desde o início do desenvolvimento de sistemas. Garantir que o sistema possa se recuperar de falhas, ser tolerante a erros e manter a disponibilidade dos serviços é fundamental para a estabilidade e confiabilidade do sistema.

- **Situações Complexas:** situações complexas e possíveis falhas no sistema, como o que acontece se o message broker (Kafka, SQS ou Rabbitmq) cair. Nesse contexto, surgem questões sobre a perda de mensagens, o comportamento do sistema e como garantir a resiliência em situações inusitadas.

- **Single Point of Failure:** a importância de evitar "single points of failure", que são componentes críticos do sistema em que toda a resiliência é baseada. Por exemplo, se todo o sistema depende exclusivamente do Kafka, uma falha nesse componente pode causar a paralisação de todo o sistema.

- **Trade-off entre Resiliência e Custo:** A resiliência não é uma tarefa simples e envolve custos adicionais, como o aumento do esforço dos desenvolvedores e recursos de hardware. É necessário encontrar um equilíbrio entre o nível de resiliência desejado e os recursos disponíveis, e essa decisão é de alto nível e estratégica, envolvendo CTOs e CEOs.

- **Gerenciamento de Riscos:** a definição do nível de resiliência é uma decisão estratégica relacionada ao gerenciamento de riscos do negócio. Cabe aos C-levels compreender o risco associado à falta de resiliência e tomar decisões informadas sobre os investimentos necessários para garantir a confiabilidade do sistema.

- **Comunicação entre Sistemas e Retries:** No nível dos desenvolvedores, a atenção à comunicação entre sistemas e o uso adequado de políticas de retry podem ajudar a garantir que as informações sejam entregues de forma confiável e que falhas momentâneas não resultem em perda de dados.

- **Visão Geral da Arquitetura de Software:** O texto conclui que entender a resiliência, escalabilidade, performance e outros aspectos é fundamental para uma visão mais abrangente sobre arquitetura de software. Embora o tema seja teórico e complexo, é essencial para o desenvolvimento de sistemas robustos e confiáveis.
