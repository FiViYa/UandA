##### Passo a passo de como rodar o programa UandA Web em PCs



* Passo 1 – certifique-se de ter a JVM (Java Virtual Machine) instalada em seu dispositivo e que esteja na versão 25 ou superior;
* Passo 2 – dê duplo clique no executável de nome "UandA Web Launcher.jar" presente nesta pasta;
* Passo 3 – abra o seu navegador web e acesse a barra de pesquisa;
* Passo 4 – digite exatamente a URL "http://localhost:8080/uanda/", sem as aspas.





##### Como encerrar a execução do programa UandA Web em PCs



**Usando o Gerenciador de Tarefas do Windows:**

* Passo 1 – abra o Gerenciador de Tarefas com o atalho Ctrl + Shift + Esc ou clicando com o botão direito do mouse sobre a barra de tarefas selecionando o Gerenciador de Tarefas;
* Passo 2 – localize, na aba Processos, a tarefa de nome "Java(TM) Platform SE binary";
* Passo 3 – clique com o botão direito sobre o processo e selecione "Finalizar tarefa".



**Usando o Prompt de Comando:**

* Passo 1 – acesse a barra de pesquisa do Windows e digite "cmd", sem as aspas;
* Passo 2 – execute o Prompt de Comando como administrador;
* Passo 3 – digite e rode o comando "netstat -ano | findstr 8080", sem as aspas, para descobrir o PID na porta 8080 (sua máquina local);
* Passo 4 – copie o número que aparece na última coluna dos resultados "logo após LISTENING";
* Passo 5 – digite e rode o comando "taskkill /F /PID numero", sem as aspas, substituindo "numero" pelo número PID copiado anteriormente.

