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
 >   - Isso ajuda a reduzir a quantidade de códigos repetidos que se digita em um arquivo de workflow. 
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
 >   - 

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

</br>
</div>
</details>

----
