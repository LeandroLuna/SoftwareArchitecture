# Perspectivas para arquitetar um software

As características principais a serem consideradas na arquitetura de um software são:

- **Performance:** A perspectiva de performance refere-se à eficiência e velocidade do sistema em processar operações e responder às solicitações dos usuários. É importante identificar e otimizar os gargalos de desempenho, garantindo que o software seja capaz de lidar com a carga de trabalho esperada sem perder eficiência. Métricas, como tempo de resposta, throughput e latência, são essenciais para medir e avaliar o desempenho do sistema.

- **Escalabilidade:** A perspectiva de escalabilidade diz respeito à capacidade do software de crescer e lidar com um aumento no número de acessos e usuários, sem comprometer seu desempenho. Uma arquitetura escalável permite adicionar recursos (como servidores ou instâncias) conforme a demanda aumenta, garantindo que o sistema possa atender a um maior número de solicitações sem falhar.

- **Resiliência:** A resiliência é a capacidade do software de se recuperar de falhas e problemas inesperados. É importante projetar o software de forma que ele possa lidar com erros, panes de rede, quedas de servidores, entre outros cenários adversos, minimizando o impacto no usuário final. Planos de contingência e estratégias de recuperação são fundamentais para garantir a resiliência do sistema.

Essas três perspectivas (performance, escalabilidade e resiliência) são essenciais para o sucesso de um software. Elas devem ser consideradas desde o início do processo de arquitetura e ao longo do desenvolvimento, para que o sistema seja capaz de enfrentar os desafios do mundo real e oferecer uma experiência confiável e satisfatória aos usuários.

## Métricas de performance

As métricas de performance que podem ser utilizadas para medir a performance do software são:

- **Latência (Response Time):** A latência refere-se ao tempo que leva para que uma ação ou requisição seja processada e o resultado seja retornado ao usuário. É medido em milissegundos e representa o tempo de resposta da aplicação. Diminuir a latência é essencial para melhorar a performance do software, garantindo que as requisições sejam atendidas de forma rápida.

- **Throughput:** O throughput é a quantidade de requisições que o software consegue lidar simultaneamente. Quanto maior o throughput, mais requisições o sistema pode atender em um determinado período de tempo. Aumentar o throughput é uma forma de melhorar a capacidade do sistema de lidar com maior demanda de acessos e garantir maior eficiência.

É importante considerar que a latência e o throughput estão relacionados. Uma alta latência pode afetar o throughput, pois conexões presas ou requisições demoradas podem impedir que o sistema lide com mais acessos simultâneos.

Para medir a performance do software, é necessário monitorar e analisar constantemente essas métricas. Identificar gargalos de latência, como chamadas externas lentas ou problemas de rede, é fundamental para otimizar o desempenho. Além disso, trabalhar na capacidade de aumentar o throughput do sistema permitirá que ele lide com maior carga de trabalho.

A busca por melhor performance deve ser uma preocupação constante, pois um software performático oferece uma experiência mais satisfatória aos usuários e é essencial para garantir o sucesso do sistema quando em produção.

## Checklist para aumento de performance

Pode-se criar um checklist para aumento de performance de uma aplicação. O checklist inclui os principais pontos que podem causar baixa performance e também estratégias para melhorar a eficiência e desempenho do sistema:

1. **Processamento Ineficiente:**
   - Revisar algoritmos e lógicas de processamento para garantir que estão otimizados.
   - Identificar e corrigir partes do código que estejam causando gargalos ou processamentos desnecessários.

2. **Recursos Computacionais Limitados:**
   - Analisar os recursos de hardware disponíveis e identificar possíveis gargalos.
   - Considerar a possibilidade de investir em hardware mais poderoso, se necessário.
   - Avaliar a relação custo-benefício entre o hardware utilizado e a performance alcançada.

3. **Programação Bloqueante:**
   - Evitar programação bloqueante que impede o processamento simultâneo de múltiplas requisições.
   - Utilizar técnicas de programação não bloqueantes ou assíncronas para melhorar o throughput do sistema.

4. **Acesso Serial aos Recursos:**
   - Identificar partes do código onde o acesso aos recursos é feito de forma serial.
   - Trabalhar com concorrência ou paralelismo para lidar com diversas tarefas ao mesmo tempo.

5. **Capacidade Computacional e Análise de Gargalos:**
   - Analisar a capacidade computacional do sistema em relação a CPU, disco, memória e largura de banda de rede.
   - Identificar gargalos e pontos críticos que limitam o desempenho e tomar ações para melhorá-los.

6. **Melhorar Algoritmos e Overhead de Framework:**
   - Otimizar algoritmos e queries para reduzir o número de operações ineficientes.
   - Evitar overhead desnecessário de frameworks e bibliotecas.

7. **Otimização de Banco de Dados:**
   - Escolher o banco de dados adequado para o problema específico.
   - Criar índices e utilizar ferramentas de profiling para otimizar queries.
   - Utilizar caching para reduzir a carga no banco de dados.

8. **Caching:**
   - Implementar estratégias de caching para armazenar resultados e dados frequentemente acessados.
   - Utilizar memória cache ou cache externo para acelerar o acesso a informações já processadas.

## Escala, concorrência e paralelismo

- **Escala Vertical:** Refere-se ao aumento da capacidade computacional de uma única máquina ou servidor, geralmente envolvendo a adição de recursos mais poderosos, como CPU, memória ou disco. Ao escalar verticalmente, a aplicação é capaz de lidar com mais requisições e processar mais dados sem a necessidade de adicionar mais máquinas ao ambiente.

- **Escala Horizontal:** Consiste em aumentar a capacidade do sistema adicionando mais máquinas ou servidores em paralelo. Essa abordagem distribui o processamento entre várias instâncias, permitindo que cada máquina ou servidor compartilhe a carga de trabalho e atenda a um número maior de requisições. Escalar horizontalmente é uma estratégia comum para sistemas que exigem alta disponibilidade, resiliência e suporte a grandes volumes de tráfego.

- **Concorrência:** Refere-se à capacidade de um sistema lidar com várias tarefas ou processos simultaneamente, mesmo que apenas uma única tarefa seja executada em cada momento. Isso pode ser alcançado por meio de técnicas assíncronas ou não bloqueantes, onde o sistema pode iniciar uma tarefa e passar para outra antes que a primeira seja concluída. Dessa forma, várias tarefas podem ser tratadas ao mesmo tempo, mesmo que apenas uma esteja em andamento em um dado momento.

- **Paralelismo:** É a execução simultânea de várias tarefas em diferentes núcleos de processamento ou máquinas distintas. O paralelismo permite que várias tarefas sejam executadas verdadeiramente ao mesmo tempo, resultando em um aumento significativo do poder de processamento e do desempenho. Em sistemas com suporte a paralelismo, várias tarefas podem ser executadas simultaneamente, melhorando a eficiência e a velocidade geral do processamento.

Em resumo, escala vertical e escala horizontal são abordagens para aumentar a capacidade computacional de um sistema. A concorrência permite lidar com várias tarefas ao mesmo tempo, mesmo que cada uma seja processada em sequência, enquanto o paralelismo possibilita a execução simultânea de várias tarefas em diferentes núcleos ou máquinas, alcançando um maior poder de processamento e desempenho.

## Caching

Caching (ou cache) é uma técnica utilizada para melhorar o desempenho e a eficiência de sistemas, especialmente em aplicações web. O cache armazena temporariamente dados que são frequentemente acessados ou processados para que possam ser recuperados rapidamente quando necessários novamente, em vez de serem recalculados ou buscados de suas fontes originais, como bancos de dados ou servidores.

O caching é uma forma essencial para aumentar a performance do sistema, diminuindo o tempo de resposta (response time) e aumentando a taxa de processamento (throughput). Algumas das principais aplicações de caching mencionadas incluem:

- **Cache na Borda (Edge Computing):** Esse tipo de cache é colocado em servidores localizados próximos ao usuário final. Ele armazena e fornece recursos estáticos, como HTML, CSS, JavaScript e imagens. Isso permite que os usuários acessem esses recursos rapidamente sem a necessidade de bater no servidor principal, melhorando a experiência do usuário e reduzindo a latência.

- **Cache de Dados Estáticos:** Dados estáticos, como imagens e arquivos CSS, que não mudam frequentemente, podem ser armazenados em cache para evitar buscas repetidas ao servidor sempre que forem solicitados. Isso reduz a carga no servidor e acelera o tempo de resposta para o usuário.

- **Cache de Páginas Web:** O cache de páginas web pode ser feito tanto na borda como no servidor principal. Páginas web frequentemente acessadas ou com conteúdo que muda menos podem ser pré-processadas e armazenadas em cache por um período de tempo determinado. Assim, quando um usuário solicitar a página novamente, o servidor pode retornar o HTML já pronto, economizando tempo e recursos.

- **Cache de Resultados de Algoritmos Pesados:** Para algoritmos complexos ou cálculos pesados que produzem resultados que não mudam com frequência, é possível armazenar em cache os resultados obtidos. Isso evita que o sistema tenha que repetir esses cálculos repetidamente, melhorando a eficiência e reduzindo a carga no servidor e banco de dados.

- **Cache de Objetos:** Para objetos ou dados que requerem processamento considerável para serem obtidos, é possível armazená-los em cache para reutilização futura. Isso é particularmente útil para sistemas ORM (Object-Relational Mapping) que fazem mapeamento de classes para o banco de dados.

É importante observar que o cache pode ser implementado de diferentes formas e pode ser compartilhado ou exclusivo em relação às máquinas ou servidores. O cache exclusivo é localizado em uma única máquina, o que permite baixa latência, mas pode levar à duplicação de recursos se vários servidores estiverem envolvidos. O cache compartilhado, por outro lado, é centralizado e pode ser acessado por várias máquinas, o que evita a duplicação, mas pode resultar em maior latência ao acessar o cache centralizado.

O uso adequado de caching pode ser crucial para otimizar a performance de um sistema, reduzir a sobrecarga em servidores e melhorar a experiência do usuário, especialmente em ambientes onde o tempo de resposta e a disponibilidade são críticos, como aplicações web de alto tráfego.

### Caching: edge Computing

Caching: Edge Computing é uma abordagem em que o cache é colocado mais próximo do usuário, permitindo que os dados sejam armazenados e recuperados mais rapidamente, evitando longas distâncias de tráfego pela internet. Edge Computing é especialmente útil em cenários com grande volume de acessos e tráfego, como aplicações de streaming de vídeo, onde a distribuição geográfica de servidores é essencial para fornecer conteúdo aos usuários com baixa latência.

## Princípios do Caching: Edge Computing

1. **Redução da Latência:** A ideia central do Edge Computing é trazer o cache mais próximo do usuário final. Isso reduz a latência, ou seja, o tempo que leva para que os dados sejam transferidos entre o servidor e o usuário. Ao armazenar o cache em servidores localizados próximos ao usuário, os dados podem ser acessados mais rapidamente, melhorando a experiência do usuário e reduzindo a sobrecarga nos servidores principais.

2. **Distribuição Geográfica:** No contexto de aplicações com alto tráfego global, como a Netflix, é fundamental espalhar o conteúdo em uma Content Delivery Network (CDN) ou malha de servidores distribuídos geograficamente. Assim, quando um usuário acessa um vídeo ou recurso, ele é servido a partir do datacenter mais próximo, evitando congestionamentos na rede e melhorando o desempenho.

3. **Economia de Recursos:** Ao utilizar Edge Computing e espalhar o cache em diferentes localidades, as empresas podem reduzir a sobrecarga em seus servidores principais e evitar a necessidade de transferir grandes quantidades de dados por longas distâncias. Isso resulta em economia de recursos e maior eficiência na entrega de conteúdo.

4. **Cloudflare Workers e Vercel:** Exemplos de plataformas são Cloudflare Workers e Vercel, que permitem implementar aplicações em Edge Computing, possibilitando o deploy de aplicações estáticas e o processamento de código em locais mais próximos dos usuários, proporcionando uma experiência mais rápida e eficiente.

5. **Cache de Arquivos Estáticos:** Arquivos estáticos, como imagens, CSS e HTML, podem ser facilmente armazenados em Edge Computing através de CDN ou plataformas como o Cloudflare. Isso permite que esses recursos sejam entregues rapidamente aos usuários, sem a necessidade de acessar os servidores principais.

6. **Custos e Experiência do Usuário:** Embora o uso de Edge Computing possa envolver alguns custos adicionais, como taxas de banda para distribuição de cache, o investimento é compensado pela melhoria na experiência do usuário. A entrega mais rápida de conteúdo e a redução da latência resultam em uma experiência mais agradável para o usuário final.