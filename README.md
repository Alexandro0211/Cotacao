# Manual de Instalação - Sistema de Cotação

![](https://www.cotacao.com.br/wp-content/themes/cotacao_2018/images/logo_cotacao.png)


## Requisitos para instalação
  * [Java JDK](https://www.oracle.com/technetwork/pt/java/javase/downloads/jdk8-downloads-2133151.html) - Instalador do Java JDK
   * [Apache Tomcat](https://tomcat.apache.org/download-90.cgi) - Instalador do Apache Tomcat 9
   * Projeto Cotacao (Copiar a seguinte pasta para algum local do servidor)
        ```sh
          Z:\Instaladores Ultra\Cotacao Web
        ```
  

## Instruções

#### 1) Instalação do Java JDK (8 ou superior)
* Entrar no Link descrito na aba ```#Requisitos para Instalação```
* Procurar a aba Java SE Development Kit 8u"Version", onde "Version" é o código da última versão, por exemplo ele irá aparecer assim: ```Java SE Development Kit 8u211```
* Clique em "Accept License Agreement"
* Na aba "Download", selecione a opção mais apropriada para instalação, Win32 ou Win64 (caso seja Windows)
* Na hora de baixar o executável, irá solicitar login e senha, usar as credenciais abaixo:
  ```sh
    User: contato@ultrasistemas.com.br
    Password: Contato123
    ```
* Depois de baixado execute o instalador e siga os passos de instalação.

#### 2) Instalação do Apache Tomcat (9 ou superior)
* Entrar no link descrito na aba ```#Requisistos para Instalação```
* Caso seja Windows, baixar o arquivo com esse nome
    ```sh
    32-bit/64-bit Windows Service Installer 
    ```
* Depois de baixado, executar o .exe como administrador
* Não trocar o caminho de instalação, deixar como sugerido pelo .exe
* Na instalação, avançar até a aba ```Configuration```
* Caso deseje alterar a porta de execução do Tomcat, mudar a propriedade abaixo, por default, ele será instalado na porta 8080: 
   ```sh
    HTTP/1.1 Connector Port
    ```
* Será necessário criar um usuário para efetuar login e posterior deploy da aplicação
* Na aba Tomcat Administrator login, usar as seguintes informações
   ```sh
    User Name: ultra
    Password: ultra
    roles: admin-gui, admin-script, manager-gui, manager-script
    ```
* Clicar em avançar e conclua o processo de instalação
* Em serviços do Windows, procure por Apache Tomcat 9.0, botão direito/propriedades e marque o tipo de inicialização como Automático (para iniciar junto com o Windows).

#### 3) Deploy da aplicação
* Dentro da pasta ```Cotacao Web``` copiar a pasta ```Cotacao``` para a pasta ```webapps``` do Tomcat, se não foi alterado na instalação, o diretório estará em:
  ```sh
    C:\Program Files\Apache Software Foundation\Tomcat 9.0\webapps
    ```
* Em seguida, Abra o navegador com o seguinte endereço:
* OBS: ``` Caso você tenha alterado a porta no momento da instalação, ela será usada ao invés da 8080```
   ```sh
    http://localhost:8080
    ```
* Clique no botão ```Manager App```
* Irá solicitar login e senha, use as credenciais criadas na aba ```#Tomcat Administrator login```
* Depois de efetuado o login, procure a aba:
   ```sh
     WAR file to deploy
   ```
* Clique em Escolher arquivo e busque o arquivo ```CotacaoREST.war``` (Dentro da pasta Cotacao Web)
* Depois clique em Deploy

#### 4) Configuração do Banco de Dados
##### Feito o processo de deploy das aplicações, será necessário configurar o caminho do banco de dados, para isso:
* Pare o Serviço do Tomcat no Windows.
* Acesse a pasta ```CotacaoREST\META-INF``` dentro de webapps, se não foi alterada na instalação, ela estará em:
  ```sh
    C:\Program Files\Apache Software Foundation\Tomcat 9.0\webapps\CotacaoREST\META-INF
  ```
* Edite o arquivo ```context.xml``` colocando o caminho do banco corretamente, exemplo:
  ```sh
    # Windows 
    url="jdbc:firebirdsql:localhost/3050:C:\\ultra\\banco\\Gestao.fdb?encoding=ISO8859_1"
    # Linux
    url="jdbc:firebirdsql:localhost:/var/firebird/GESTAO.FDB?encoding=ISO8859_1"
  ```
* Inicie o serviço do Apache Tomcat novamente.

![](https://cdn4.iconfinder.com/data/icons/simplicio/128x128/notification_done.png)



