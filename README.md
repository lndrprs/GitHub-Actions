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


</br>
</div>
</details>

----
