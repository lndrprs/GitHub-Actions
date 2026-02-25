<div align="Center"> 
<br>

<h4>

░█████╗░░█████╗░████████╗██╗░█████╗░███╗░░██╗░██████╗
██╔══██╗██╔══██╗╚══██╔══╝██║██╔══██╗████╗░██║██╔════╝
███████║██║░░╚═╝░░░██║░░░██║██║░░██║██╔██╗██║╚█████╗░
██╔══██║██║░░██╗░░░██║░░░██║██║░░██║██║╚████║░╚═══██╗
██║░░██║╚█████╔╝░░░██║░░░██║╚█████╔╝██║░╚███║██████╔╝
╚═╝░░╚═╝░╚════╝░░░░╚═╝░░░╚═╝░╚════╝░╚═╝░░╚══╝╚═════╝░
</div>

----

<details>
  <summary><b> 1. Tópicos </b></summary>
<div align="Left">  
<br>  

A1.1 - Introdução
 > - Plataforma de CI/CD, que permite automatizar a construção, teste e provisionamento de pipeline;
 > - Permite a criação de Workflows que executam testes sempre que há uma mudança no repositório.
 > 
 > - GitHub fornece workflows pré-configurados que podem ser usados para criar workflows customizados:
 >   - CI: https://github.com/actions/starter-workflows/tree/main/ci
 >   - Deployments: https://github.com/actions/starter-workflows/tree/main/deployments
 >   - Automação: https://github.com/actions/starter-workflows/tree/main/automation
 >   - Code Scanning: https://github.com/actions/starter-workflows/tree/main/code-scanning
 >   - Pages: https://github.com/actions/starter-workflows/tree/main/pages
 >   - Lista Completa: https://github.com/actions/starter-workflows
 >
 > - GitHub providencia máquinas virtuais Linux, Windows e macOS para executar os workflows; 
 >   - Também é possível usar os seus próprios "runners", dentro da sua nuvem ou data center. 

A1.2 - Componentes do Actions 
 > - É possível configurar um workflow para que seja executado quando um evento ocorre num repositório - como pull request ou issue; 
 >   - O Workflow contém um ou mais "jobs", que podem ser executados em ordem sequencial, ou em paralelo; 
 >   - Cada "job" executa dentro de sua própria máquina virtual runner, ou dentro de um contêiner;
 >     - E também possuem um ou mais passos / processos (que podem ser um script ou ação).
 >
 > - Workflows 
 >   - É um processo automatizado e configurável, que executa um ou mais jobs;
 >   - São definidos por um arquivo YAML no seu repositório, e são executados quando engatilhados por um evento - ou manualmente / agendado;
 >   - Ficam dentro do repositório, no diretório: .github/workflows;
 >     - Um repositório pode ser múltiplos workflows, que podem performar diferentes conjuntos de tarefas. 
 >
 > - Events
 >   - Evento é uma atividade específica em um repositório, que engatilha uma execução de workflow; 
 >     - Essa atividade pode ser um pull request, uma abertura de issue, ou commit;
 >     - Também pode ser agendado, ou por post de API REST, ou manualmente.
 >     - Para uma lista completa de eventos: https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows  
 > 
 > - Jobs
 >   - Conjunto de processos de um workflow, que é executado no mesmo runner; 
 >   - Cada processo é um script, ou uma ação; 
 >   - Processos são executados em ordem, e são dependentes um do outro;
 >   - É possível compartilhar dados entre processos - por serem executados no mesmo runner; 
 >   - Também é possível usar "matrix", para executar o mesmo job múltiplas vezes, com diferentes combinações de variáveis. 
 >
 > - Actions 
 >   - "Action" é um conjunto de jobs predefinidos e reutilizáveis que performam tarefas específicas em um workflow;
 >   - Isso ajuda a reduzir a quantidade de códigos repetidos que se digita em um arquivo de workflow;
 >   - As ações podem ser customizadas, e executadas diretamente numa máquina ou em um contêiner Docker;
 >     - É possível definir as ações de input, output e variáveis de ambiente. 
 >
 > - Runner 
 >   - Runner é um servidor que executa workflows quando são engatilhados; 
 >   - Cada runner pode executar um job por vez;
 >   - GitHub fornece runners Linux, Windows e macOS para execução dos workflows;
 >   - Cada workflow é executado em uma máquina virtual "nova";
 >     - Caso seja necessário sistemas operacionais diferentes, ou hardwares específicos, é possível hospedar seus próprios runners. 
 >
 > - Variáveis
 >   - Servem para armazenar ou reusar informações de configuração, não sensíveis; 
 >   - Possível armazenar qualquer dado de configuração, como flags de compilação, usuários, servidores, etc; 
 >   - As variáveis ficam no Runner que executa o workflow; 
 >     - Para definir a variável em um workflow, usa o "env"; 
 >     - Para definir uma variável entre múltiplos workflows, configura no nível de organização, repositório ou ambiente. 
 >
 > - Contextos 
 >   - Maneira de acessar informação sobre execuções de workflow, variáveis, ambientes de runners, jobs, e processos / jobs;
 >   - Cada contexto é um objeto que contém propriedades, que podem ser strings ou outros objetos.
 >
 > - Expressões
 >   - Expressões podem ser usadas programaticamente para definir variáveis de ambiente em arquivos de workflow e contextos de acesso; 
 >   - Uma expressão pode ser qualquer combinação de valores literais, referências de contexto ou funções; 
 >   - É possível combinar literais, referências de contexto, e funções usando operadores;
 >   - Normalmente usam condicionais "if", para definir se um processo deve ser executado - quando "true", o processo é executado. 
 >
 > - Workflows Reutilizáveis 
 >   - Reutilizar workflows evita duplicação - sendo melhor para manter e criar novos workflows rapidamente;
 >   - Um workflow que usa outro workflow se chama workflow "caller" - e o workflow chamado se chama "called" workflow; 
 >   - Um caller pode user múltiplos called - e cada called é referenciado em uma única linha;
 >     - Enquanto um Workflow Reutilizável permite usar um workflow inteiro, o Composite Actions combina múltiplos processos dentro de um processo;
 >
 > - Environments 
 >   - Ambientes são usados para descrever o alvo de provisionamento, como produção, staging e desenvolvimento;
 >   - Nos ambientes, é possível definir:
 >     - Requisitos de aprovação para procedência de job;
 >     - Restringir gatilhos de workflow;
 >     - Regras de proteção; 
 >     - Limitar acessos.
 >   - Cada job em um workflow pode referenciar apenas um ambiente. 
 >
 > - Workflow Artifacts 
 >   - Artefato é um arquivo ou coleção de arquivos produzidos durante a execução de um workflow; 
 >   - Arfetatos permitem a persistência de dados depois que um job é completado, e compartilha esses dados com outro job no mesmo workflow.
 >   - Tipos comuns de artefatos:
 >     - Arquivos de Log;
 >     - Core Dumps;
 >     - Resultados de testes, falhas, e screenshots;
 >     - Binários ou arquivos comprimidos; 
 >     - Performance de teste de estresse, e resultados de código. 

A1.3 - Continuous Integration 
 > - Prática de software que requer commitar código frequentemente à um repositório compartilhado; 
 >   - GitHub executa testes de CI e providencia resultados de cada teste, para verificar introduções de erros;
 >   - Quando todos os testes de CI em um workflow são validados, as mudanças são empurradas para serem revisionadas por um membro do time, ou unificadas; 
 >     - Quando se monta um CI no repositório, o GitHub analisa o código no repositório e recomenda workflows de CI baseados na linguagem e framework do repositório;

A1.4 - Continuous Deployment 
 > - Prática de automação para publicação e provisionamento de updates no software; 
 >   - O código é automaticamente construído e testado antes do provisionamento; 
 >   - CD frequentemente é usado em conjunto com CI. 

A1.5 - Actions vs Apps 
 > - GitHub Marketplace oferta Actions e Aps, cada um com ferramentas úteis para automação e workflows. 
 >
 > - GitHub Apps 
 >   - Executa persistentemente e reage a eventos rapidamente; 
 >   - Funciona bem quando dados persistentes são necessários;
 >   - Funciona melhor com requisições API, que não consomem tanto tempo;
 >   - Executado em um servidor ou infraestrutura que você providencia. 
 >
 > - GitHub Actions
 >   - Providencia automação que performa CI e CD;
 >   - Pode ser executado em máquinas runners ou contêineres Docker;
 >   - Pode incluir um clone do repositório, permitindo ferramentas de provisionamento, e publicação, formatadores de código, e command line;
 >   - Não precisa provisionar código ou servir uma aplicação;
 >   - Possui interface simples para criar e usar segredos, que permite ações interagirem com serviços terceiros. 

A1.6 - GitHub-Hosted Runners 
 > - Runners são máquinas que executam jobs em um workflow do Actions; 
 >   - Um runner pode clonar o repositório localmente, instalar software de teste, e executar comandos para avaliar o código;
 >   - Existem dois tipos de Runners:
 >     - Single-CPU runners, que são hospedados em contêineres; 
 >     - Cada Runner hospedado no Github é uma nova máquina virtual;
 >   - Cada runner possui aplicações e outras ferramentas pré-instaladas.
 >
 > - Runner Images 
 >   - GitHub mantém um conjunto de imagens de VM para o runner hospedado padrão; 
 >   - As imagens podem ser vistas nessas duas URLs:
 >     - GitHub: https://github.com/actions/runner-images
 >     - Parceiros: https://github.com/actions/partner-runner-images
 >
 > - Custom Images
 >   - GitHub fornece uma imagem base, e permite você construir sua própria imagem de VM, customizada para os workflows
 >   - Imagens customizadas podem possuir:
 >     - Código de repositório;
 >     - Imagens de contêineres; 
 >     - Binários;
 >     - Certificados; 
 >     - Entre outros. 
 >   - Imagens customizadas podem ser usadas apenas com "Larger Runners". 
 >
 > - Cloud Hosts 
 >   - GitHub hospeda runners Linux e Windows em máquinas virtuais no Microsoft Azure;
 >   - A aplicação do runner é um fork do agente do Azure Pipeline;
 >   - GitHub hospeda macOS runners nos data centers do Azure. 

A1.7 - Larger Runners 
 > - Larger Runners são disponibilizados para Organizações e Empresas  usando  o GitHub Team ou planos de GitHub Enterprise Cloud;
 >   - As características diferenciais de Larger Runners, são:
 >     - RAM, CPU e espaço de armazenamento;
 >     - IP estático;
 >     - Rede Privada da Azure;
 >     - Agrupamento de Runners;
 >     - Dimensionamento automático (Autoscaling);
 >     - Runners com suporte a GPU. 
 >   - Larger Runners são cobrados por minuto pela quantidade de time de execução do workflow. 

A1.8 - Self-Hosted Runners 
 > - Runners Auto-Hospedados permitem mais controle de hardware, S.O, e ferramentas de software;
 > - Permite usar máquinas e serviços que a empresa já mantém e paga para usar; 
 > - Gratuito para usar com o GitHub Actions, mas é responsabilidade da empresa o custo para manter as máquinas runners;
 > - Permite criar configurações de hardware customizadas; 
 > - Pode ser físico, virtual, em contêiner, on-premises, ou em nuvem. 

A1.9 - Private Networking
 > - Runners no GitHub possuem acesso para internet pública; 
 > - Com a Rede Privada, você configura runners para se conectar exclusivamente com a rede privada e recursos; 
 > - Para configurar esse acesso, existem algumas formas:
 >   - API Gateway com OIDC (OpenID Connect);
 >   - WireGuard;
 >   - VNET (Azure Virtual Network). 

A1.10 - Runner Groups 
 > - Grupos de Runners são usados para coletar conjuntos de runners e criar um limite de segurança entre eles;
 > - Runners só podem ficar em um grupo por vez; 
 > - É possível mover runner de um grupo para outro;
 > - Opcionalmente, é possível atribuir políticas de acesso ao grupo de Runners.  

A1.11 - Runner Scale Sets 
 > - Scale Set é um grupo de runners homogêneos, que podem ter jobs atribuídos do Actions;
 > - O número de runners ativos é propriedade do Runner Scale Set, que pode ser controlado pelo auto-dimensionamento ARC - Actions Runner Controller. 
 > - É possível utilizar Runner Groups para gerenciar Runner Scale Sets; 
 > - Você pode adicionar Runner Scale Sets em grupos de Runners já existentes;
 >   - Porém, Runner Scale Sets podem pertencer a apenas um runner group de cada vez, e só podem ter um label atribuído à eles. 

A1.12 - Actions Runner Controller (ARC)
 > - Operador Kubernetes que orquestra e escala Runners Self-Hosted para o Actions; 
 > - Com o ARC, é possível criar Runner Scale Sets que automaticamente escalam baseados no número de workflows no repositório / organização / empresas; 
 > - ARC é instalado usando charts Helm.

A1.13 - Secrets 
 > - Permite armazenar informações sensíveis na organização, repositório, ou ambientes;
 > - Segredos são variáveis que você cria usando o Workflow do Actions;
 > - Actions pode apenas ler um segredo, se você explicitamente incluir o segredo no workflow.  
 > 
 > - Organization-Level Secrets 
 >   - Permite compartilhar segredos entre múltiplos repositórios, que reduz a necessidade de criar segredos duplicados; 
 >   - Atualizando um segredo organizacional, afeta os workflows que usam esse mesmo segredo;
 >   - Para permitir um segredo disponível num action, precisa definir o segredo como input ou variável de ambiente no arquivo workflow.

A1.14 - GITHUB_TOKEN
 > - No começo de cada workflow, o GitHub automaticamente cria um Token único, para usar no workflow;
 > - O GITHUB_TOKEN pode ser usado para autenticar no workflow; 
 > - As permissões do Token são limitadas ao repositório que contém o workflow; 
 > - O Token expira quando o job finaliza, ou depois de 24 horas. 


</br>
</div>
</details>

----
