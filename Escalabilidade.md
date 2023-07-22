# Escalabilidade

Escalabilidade refere-se à capacidade de um sistema suportar o aumento ou a redução de workloads (cargas de trabalho) de forma eficiente, aumentando ou diminuindo a capacidade computacional em proporções adequadas. O objetivo da escalabilidade é garantir que o sistema possa lidar com variações de demanda sem comprometer seu desempenho ou disponibilidade.

Existem dois tipos principais de escalabilidade:

1. Escalabilidade Vertical: Nesse tipo de escalabilidade, o aumento da capacidade do sistema é alcançado adicionando mais recursos a uma única máquina ou servidor. Isso envolve aumentar a quantidade de memória, CPU, disco e velocidade de disco em uma única máquina. Por exemplo, se o servidor está ficando sobrecarregado, pode-se melhorar sua escalabilidade vertical adicionando mais memória RAM ou processadores mais rápidos.

2. Escalabilidade Horizontal: Já nesse tipo de escalabilidade, o aumento da capacidade é alcançado adicionando mais máquinas ao sistema, em vez de investir em recursos individuais para uma única máquina. Isso é frequentemente realizado através da replicação do sistema em várias máquinas e usando um load balancer ou proxy reverso para distribuir as solicitações entre elas. Se a demanda aumenta, basta adicionar mais máquinas para aumentar a capacidade global do sistema.

A vantagem da escalabilidade horizontal é que ela permite que o sistema seja dimensionado facilmente, adicionando mais máquinas conforme necessário, evitando os limites físicos que uma única máquina pode ter. Além disso, ela também oferece maior redundância, uma vez que se uma máquina falhar, outras ainda estarão disponíveis para lidar com as solicitações, garantindo maior disponibilidade e tolerância a falhas.

Em contrapartida, a escalabilidade vertical pode enfrentar limitações físicas, como o máximo de recursos que uma máquina pode suportar, além de ter uma maior vulnerabilidade a falhas, já que uma única máquina é responsável por todo o sistema.

No geral, a escalabilidade é uma característica importante para garantir que os sistemas possam crescer e se adaptar às demandas crescentes dos usuários ou às variações nas cargas de trabalho, mantendo o desempenho e a disponibilidade adequados. A escolha entre escalabilidade vertical e horizontal dependerá das necessidades e características específicas do sistema em questão.

## Escalando aplicações

Escalonamento de aplicações refere-se ao processo de dimensionar e distribuir recursos de uma aplicação para lidar com a demanda crescente de usuários ou cargas de trabalho. O objetivo é garantir que o sistema possa ser facilmente expandido ou reduzido, adicionando ou removendo máquinas conforme necessário, mantendo a disponibilidade e o desempenho adequados.

Os pontos-chave para escalonar horizontalmente (adicionar mais máquinas) uma aplicação são:

- **Disco Efêmero**: Significa que o que é salvo em disco na máquina é temporário e pode ser apagado a qualquer momento. Essa abordagem exige que a aplicação seja projetada para armazenar dados permanentes em locais externos, como serviços de armazenamento em nuvem (por exemplo, Amazon S3), em vez de depender apenas do disco local da máquina.

- **Servidor de Aplicação vs. Servidor de Assets**: Separação entre o servidor de aplicação (que lida com a lógica da aplicação) e o servidor de ativos (como imagens, arquivos CSS, arquivos estáticos etc.). Ao escalar a aplicação, é necessário focar na escalabilidade do servidor de aplicação, pois o servidor de ativos pode ser servido por outros servidores externos, de forma que a aplicação possa ser destruída e criada sem perder esses ativos.

- **Cache Centralizado**: O cache (dados temporariamente armazenados para melhorar o desempenho) não deve ficar na máquina local. Em vez disso, deve ser centralizado em um servidor externo compartilhado, permitindo que todas as máquinas da aplicação acessem o mesmo cache, independentemente de qual delas atende ao usuário.

- **Sessões Centralizadas**: Quando as sessões são usadas (como no caso de um usuário fazer login em um site), elas devem ser centralizadas e armazenadas em um servidor externo para que o usuário possa acessar as mesmas informações independentemente de qual máquina do cluster está sendo usada.

- **Aplicação Stateless**: A aplicação deve ser projetada como "stateless", o que significa que não armazena informações de estado na máquina local. Todo estado relevante deve ser armazenado externamente, permitindo que a aplicação seja facilmente replicada ou removida sem perder informações importantes.

Em resumo, o escalonamento de aplicações requer a descentralização de dados, cache, sessões e outros elementos-chave, garantindo que a aplicação possa ser dimensionada horizontalmente, adicionando ou removendo máquinas conforme necessário. Isso permite que a aplicação seja mais flexível, resiliente e capaz de lidar com picos de demanda sem comprometer o desempenho.

## Escalando bancos de dados

O escalonamento de banco de dados é uma tarefa complexa que envolve garantir que o sistema possa lidar com o aumento de carga e demanda, mantendo o desempenho adequado. 

Algumas estratégias e considerações importantes para escalar bancos de dados de forma eficiente são:

- **Aumento de Recursos Computacionais**: Inicialmente, é possível escalar verticalmente o banco de dados, aumentando a capacidade de recursos computacionais, como CPU, memória e disco. No entanto, esse tipo de escalonamento tem limitações e, eventualmente, é necessário considerar outras abordagens.

- **Segregação de Responsabilidades**: Para enfrentar gargalos e distribuir melhor a carga, é recomendável considerar a segregação de responsabilidades no banco de dados. Por exemplo, criar bancos de dados específicos para leitura e escrita separadamente. Dessa forma, os dados gravados em um banco de dados de escrita são replicados e consultas podem ser feitas no banco de leitura, o que ajuda a distribuir as tarefas.

- **Escalonamento Horizontal**: À medida que a demanda cresce, é necessário considerar a escalabilidade horizontal, que envolve adicionar mais máquinas de leitura ou repensar o formato do banco de dados. Isso pode incluir o uso de shards (particionamento de dados) ou o uso de bancos de dados especializados para determinadas tarefas, como o Cassandra para muita escrita ou o Neo4j para trabalhar com gráficos.

- **Opções de Bancos de Dados**: Atualmente, há diversas opções de bancos de dados disponíveis, e é importante entender as necessidades da aplicação para escolher o banco de dados mais adequado. Além disso, a adoção de soluções serverless, em que o provedor de nuvem gerencia automaticamente a infraestrutura do banco de dados, pode ser uma alternativa interessante para simplificar o gerenciamento e a escalabilidade.

- **Otimização do Banco de Dados**: Antes de escalar o banco de dados, é importante realizar otimizações. Isso inclui trabalhar com índices adequados para consultas, analisar o desempenho das queries usando ferramentas de monitoramento (APM - Application Performance Monitoring) e considerar a adoção de padrões como CQRS (Command Query Responsibility Segregation), que separam as operações de leitura e escrita para melhorar a performance.

Em resumo, o escalonamento de banco de dados requer um cuidadoso planejamento e compreensão das necessidades da aplicação, bem como das soluções disponíveis. A adoção de estratégias como escalonamento horizontal, segregação de responsabilidades e otimização do banco de dados pode ajudar a garantir um desempenho adequado e uma experiência positiva para os usuários, mesmo em cenários de alta demanda.

## Proxy Reverso

Um proxy reverso é um servidor que atua como intermediário entre os clientes e os servidores web. Ele fica na frente dos servidores web e recebe as solicitações dos clientes, como navegadores web, encaminhando-as para os servidores web apropriados com base em regras de redirecionamento predefinidas. Em contraste com um proxy normal, que redireciona as solicitações do cliente para outros destinos, um proxy reverso redireciona as solicitações do cliente para servidores específicos.

Quando um cliente envia uma solicitação para um site, o proxy reverso analisa a URL solicitada e, com base em suas regras de redirecionamento, encaminha a solicitação para o servidor apropriado que hospeda o conteúdo desse site específico. Dessa forma, o proxy reverso pode ser usado para distribuir o tráfego entre vários servidores, realizar balanceamento de carga (load balancing) e melhorar o desempenho geral do site, direcionando as solicitações para os servidores menos ocupados.

O proxy reverso também pode funcionar como um ponto de entrada único para vários servidores, permitindo que os administradores ocultem a estrutura interna do servidor e melhorem a segurança, uma vez que o cliente só precisa se comunicar com o proxy e não diretamente com os servidores de back-end.

Algumas soluções populares de proxy reverso incluem o Nginx, HAProxy e Traefik. Essas ferramentas são frequentemente utilizadas para melhorar a escalabilidade, disponibilidade e desempenho de aplicativos e sites da web, especialmente em ambientes com alto tráfego e múltiplos servidores. O Nginx é especialmente conhecido por suas capacidades de proxy reverso e é amplamente utilizado em cenários de balanceamento de carga e redirecionamento de tráfego em ambientes de servidor web.