# Características arquiteturais

Características Arquiteturais são atributos e aspectos específicos que são considerados intencionalmente durante o processo de desenvolvimento de software, a fim de garantir que o sistema atenda a requisitos não funcionais importantes. Essas características são fundamentais para garantir a qualidade, desempenho, segurança e confiabilidade do software, bem como para facilitar sua manutenção e evolução ao longo do tempo.

Podemos destacar alguns pontos importantes sobre Características Arquiteturais:

- Intencionalidade: As Características Arquiteturais são pensadas e projetadas de forma intencional durante a arquitetura e o desenvolvimento do software. Isso significa que elas não devem depender de sorte ou acontecer por acaso, mas sim serem planejadas e implementadas de maneira consciente.

- Requisitos Não Funcionais: As Características Arquiteturais são, em grande parte, relacionadas aos requisitos não funcionais do sistema, ou seja, os requisitos que não dizem respeito diretamente às funcionalidades, mas sim à qualidade, desempenho e outras propriedades do software.

- Checklists de Pontos Importantes: As Características Arquiteturais são tratadas como uma espécie de checklist de pontos importantes a serem considerados no desenvolvimento do software. Elas abrangem aspectos cruciais para o correto funcionamento do sistema e devem ser sempre levadas em conta.

- Divisão das Características Arquiteturais em três áreas: operacionais, estruturais e cross-cutting. As características operacionais estão relacionadas ao funcionamento geral do software, as características estruturais referem-se à organização e estrutura do sistema, enquanto as características cross-cutting permeiam todo o software e têm uma abrangência mais geral.

- Preparação para Problemas: O desenvolvedor deve estar preparado para enfrentar e solucionar determinados problemas de forma intencional. Ao considerar as Características Arquiteturais, o profissional se antecipa a questões cruciais e evita depender apenas da sorte para a solução de problemas.

- Literatura Recomendada: Livro "Fundamentos de Arquitetura de Software".

Em resumo, Características Arquiteturais são aspectos intencionais e planejados que permeiam o desenvolvimento do software, garantindo que o sistema atenda a requisitos não funcionais importantes e funcione de maneira eficiente, segura e confiável. Essas características são fundamentais para a construção de sistemas de qualidade, que possam se adaptar a situações diversas e evoluir de maneira consistente ao longo do tempo.

## Características Operacionais

Características operacionais referem-se a aspectos específicos que impactam diretamente na operação e funcionamento do software. Ao desenvolver um sistema, é fundamental considerar essas características para garantir a disponibilidade, confiabilidade, segurança, robustez e escalabilidade da aplicação.

Um dos principais pontos das características operacionais é a disponibilidade do software. É necessário determinar o tempo que o sistema ficará no ar, estabelecer acordos de nível de serviço (SLA) e objetivos de nível de serviço (SLO). Pensar de forma intencional sobre a disponibilidade permitirá gerenciar melhor a observabilidade do sistema e criar estratégias para lidar com incidentes e recuperação de desastres.

Outro aspecto importante é a performance do sistema, que engloba a latência (tempo de resposta) e o throughput (capacidade de receber requisições). É necessário definir o nível de performance desejado e projetar o sistema de acordo com essa exigência. Sistemas com diferentes demandas de performance exigirão abordagens distintas, como o uso de bancos de dados adequados e técnicas como CQRS (Command Query Responsibility Segregation).

A segurança e a confiabilidade também são aspectos cruciais das características operacionais. Sistemas de missão crítica devem considerar a proteção contra ataques e a garantia de que a operação do sistema não seja afetada por ameaças externas. É importante implementar medidas de proteção, como captchas, para evitar ações maliciosas, além de políticas de senhas e testes periódicos de backup.

A robustez do sistema é outro elemento relevante das características operacionais. Significa que o software deve ser projetado de forma que, mesmo diante de eventos adversos, ele continue funcionando adequadamente. Isso inclui a capacidade de escalar horizontalmente e garantir a continuidade do serviço, mesmo que haja falhas em data centers ou em zonas de disponibilidade.

Por fim, a escalabilidade é um ponto essencial a ser considerado. É importante que a aplicação seja capaz de escalar conforme a demanda cresce, tanto verticalmente (aumentando o recurso computacional em uma única máquina) quanto horizontalmente (adicionando mais máquinas). A adoção de boas práticas, como a criação de aplicações stateless e o cumprimento dos Twelve-Factor, contribui para a escalabilidade do sistema.

É crucial ter em mente que as características operacionais devem ser pensadas durante o processo de desenvolvimento, para garantir que o software possa ser operado eficientemente e com alto desempenho, além de atender aos requisitos de segurança e confiabilidade. Isso possibilita que a aplicação seja resiliente e mantenha um bom funcionamento mesmo diante de desafios operacionais.

### Twelve-Factor App

A Metodologia Twelve-Factor App (Aplicativo de Doze Fatores) é um conjunto de princípios e boas práticas para o desenvolvimento de aplicativos modernos, projetados para serem executados em ambientes de nuvem, escaláveis e flexíveis. Essa metodologia foi apresentada por Adam Wiggins e é amplamente utilizada na comunidade de desenvolvimento de software.

Os "Doze Fatores" (Twelve-Factor App) abrangem uma série de diretrizes que visam garantir que os aplicativos sejam construídos de forma consistente, independente de plataforma e facilmente escaláveis. Eles são especialmente relevantes para aplicativos baseados em microsserviços, onde cada componente do aplicativo é independente e pode ser dimensionado individualmente.

A seguir estão os doze fatores da metodologia:

1. Codebase (Código Base): Cada aplicativo deve ter um único código-base no controle de versão. Isso garante que a equipe de desenvolvimento esteja trabalhando com uma única versão do aplicativo.

2. Dependências: As dependências externas do aplicativo devem ser explicitamente declaradas e isoladas do código. Isso facilita a gestão das dependências e evita conflitos.

3. Configurações: As configurações do aplicativo, como variáveis de ambiente, devem ser armazenadas fora do código. Isso permite que o aplicativo seja configurado de forma flexível em diferentes ambientes.

4. Backing Services (Serviços de Suporte): Os serviços externos, como bancos de dados, devem ser tratados como recursos conectáveis. O aplicativo não deve depender de configurações específicas desses serviços.

5. Build, Release, Run (Build, Versão, Execução): O processo de build, criação de releases e execução do aplicativo deve ser separado. Isso permite que os builds sejam tratados como objetos imutáveis e facilita a implantação e o controle de versões.

6. Processos: O aplicativo deve ser executado como processos stateless (sem estado). Isso torna o aplicativo escalável e fácil de gerenciar.

7. Port Binding (Vinculação de Portas): O aplicativo deve exportar serviços através de portas definidas. Isso permite que ele seja acessado de maneira consistente.

8. Concorrência: O aplicativo deve ser projetado para ser escalável horizontalmente, adicionando mais instâncias para lidar com a carga. Ele deve dividir o trabalho em processos menores e independentes.

9. Descartabilidade: O aplicativo deve ser fácil de iniciar e encerrar rapidamente, permitindo escalonamento dinâmico e substituição de instâncias.

10. Dev/Prod Parity (Paridade entre Desenvolvimento e Produção): Os ambientes de desenvolvimento, teste e produção devem ser o mais semelhantes possível para evitar problemas relacionados a diferenças entre esses ambientes.

11. Logs: O aplicativo deve tratar logs como fluxo de eventos, permitindo que eles sejam facilmente coletados, analisados e depurados.

12. Admin Processes (Processos de Administração): Tarefas administrativas, como execução de scripts de banco de dados, devem ser tratadas como processos de uma única vez.

Ao seguir os princípios da metodologia Twelve-Factor App, os desenvolvedores podem criar aplicativos modernos, altamente escaláveis, independentes de plataforma e fáceis de manter, preparando-os para funcionar de forma eficiente em ambientes distribuídos, como a nuvem. Essa abordagem se tornou amplamente adotada na indústria de desenvolvimento de software e é considerada uma referência para a construção de aplicações robustas e resilientes.

## Características estruturais

As características estruturais referem-se a aspectos específicos relacionados ao desenvolvimento da aplicação e como ela é projetada para ser flexível, configurável e facilmente mantida. Essas características estão relacionadas à arquitetura e design do software, tornando-o mais adaptável, extensível e portátil. Vamos detalhar cada uma delas:

- **Configurável**: O software deve ser projetado de forma a permitir configurações fáceis e flexíveis. Isso inclui a capacidade de configurar conexões com bancos de dados, APIs externas e outros recursos do sistema sem a necessidade de alterações no código fonte. A configuração pode ser feita através de variáveis de ambiente, arquivos de configuração ou outras formas que facilitem as mudanças sem modificar o código base.

- **Extensível**: A aplicação deve ser pensada para crescer de forma que seja possível adicionar novos recursos e funcionalidades sem modificar a estrutura existente. Isso é alcançado através do uso de interfaces, adaptadores e outros padrões de design que permitem a integração de novos componentes de forma isolada, sem impactar outras partes do sistema.

- **Fácil Instalação**: A aplicação deve ser de fácil instalação em diferentes ambientes, como produção, teste e staging. A padronização do ambiente é importante para garantir que a aplicação funcione de forma consistente em diferentes cenários. O uso de containers, como Docker, pode ajudar a padronizar e simplificar o processo de instalação.

- **Reutilização de Componentes**: A reutilização de componentes facilita a manutenção do software, permitindo que partes comuns sejam compartilhadas entre diferentes projetos. Isso evita a duplicação de código e reduz a complexidade do sistema. Criar bibliotecas ou módulos reutilizáveis é uma abordagem comum para alcançar essa característica.

- **Internacionalização**: Se a aplicação tiver a necessidade de suportar diferentes idiomas e culturas, a internacionalização é uma característica importante a ser considerada. Isso envolve pensar na forma como os recursos serão traduzidos, como as moedas e valores serão tratados para diferentes regiões e como a aplicação vai se comportar em ambientes multilíngues.

- **Fácil Manutenção**: A manutenção do software deve ser facilitada através de um código bem estruturado e testes automatizados. O uso de princípios como SOLID e a adoção de boas práticas de design ajudam a tornar o código mais fácil de ser modificado e mantido ao longo do tempo.

- **Portabilidade**: O software deve ser projetado para ser portável, ou seja, ter a capacidade de ser executado em diferentes ambientes e plataformas sem grandes modificações. Isso envolve a redução da dependência de fornecedores específicos e a utilização de tecnologias que permitem a migração entre diferentes sistemas.

- **Observabilidade**: A observabilidade refere-se à capacidade de monitorar e entender o comportamento do software em tempo de execução. Isso inclui a geração de logs, métricas e o uso de ferramentas de observabilidade que permitem identificar e resolver problemas rapidamente.

Essas características estruturais são importantes para garantir que a aplicação seja flexível, adaptável e fácil de manter ao longo do tempo. Ao projetar e desenvolver um software, é essencial considerar esses aspectos para construir um sistema robusto e escalável.

## Características Cross-Cutting

Características cross-cutting são aspectos que atravessam e afetam diversas partes de uma aplicação de software, independentemente da sua estrutura ou arquitetura específica. Essas características têm um impacto geral na aplicação e geralmente não estão concentradas em uma única área funcional, mas se estendem por várias partes do sistema.

Algumas características cross-cutting:

- **Acessibilidade:** É uma característica que se aplica em diversos pontos da aplicação, especialmente no front-end. Acessibilidade refere-se à capacidade do sistema de ser utilizado por todas as pessoas, independentemente de suas capacidades físicas ou sensoriais. Isso envolve tornar a aplicação compatível com leitores de tela e dispositivos assistivos, além de fornecer uma interface de usuário que seja fácil de usar para todas as pessoas.

- **Retenção e recuperação de dados:** A gestão de dados é uma característica que atravessa muitas partes da aplicação. Isso inclui a decisão de quanto tempo os dados serão mantidos e a forma como eles serão armazenados, especialmente em ambientes de arquitetura distribuída onde o armazenamento de dados pode ser mais complexo.

- **Autenticação e Autorização:** Essa é uma característica que atravessa diversas partes da aplicação, especialmente em arquiteturas distribuídas com microsserviços. O gerenciamento de autenticação e autorização pode ser mais complexo nesses cenários, e é importante considerar a utilização de um servidor de identidade ou API Gateway para lidar com essas questões.

- **Conformidade Legal e Privacidade:** São aspectos que precisam ser considerados em várias partes da aplicação para garantir que a aplicação esteja em conformidade com as leis e regulamentações do país em que opera, especialmente no que diz respeito à privacidade e proteção de dados dos usuários.

- **Segurança:** Essa é uma característica que deve ser aplicada de forma ampla e abrangente, desde a borda da aplicação até o nível do banco de dados. É importante utilizar boas práticas de segurança em todas as camadas da aplicação e utilizar padrões abertos para autenticação e criptografia.

- **Usabilidade:** A usabilidade é outro aspecto cross-cutting que não se limita apenas à interface do front-end. Ela se estende também à API e outras partes do sistema, garantindo que a aplicação seja fácil de usar e ofereça uma boa experiência para o usuário em todas as suas interações.

Essas características cross-cutting são fundamentais para o desenvolvimento de aplicações modernas, seguras e eficientes, e devem ser consideradas em todas as etapas do desenvolvimento do software. Ao levar em conta esses aspectos, os desenvolvedores podem criar aplicações mais acessíveis, confiáveis, seguras e de alta qualidade para os usuários.