# Arquitetura MVC

Ponderada de Programação da Semana 1

## 1. Descrição do Projeto

- **Nome do Projeto:** Abandono Zero (PsicoPets)
- **Descrição:** O projeto consiste em
- **Arquitetura:** MVC (Model-View-Controller)
- **Ferramenta de Diagramação:** A ferramenta de diagramação utilizada foi o draw.io
<br>

## 2. Introdução

&nbsp;&nbsp;&nbsp;&nbsp;A origem da arquitetura MVC remonta à década de 1970, quando foi introduzida no contexto do desenvolvimento de interfaces gráficas de usuário no Xerox PARC (Palo Alto Research Center), um centro de pesquisa da Xerox Corporation. Inventada pelo cientista da computação norueguês Trygve Reenskaug, o objetivo inicial era separar a lógica de apresentação da aplicação da lógica de negócios, tornando o código mais modular e mais fácil de manter.

&nbsp;&nbsp;&nbsp;&nbsp;A arquitetura MVC (Model-View-Controller) é um padrão de arquitetura de software que organiza uma aplicação em três componentes principais: Modelo, Visão e Controlador. Cada um desses componentes desempenha um papel específico na aplicação, permitindo uma separação clara de preocupações e facilitando o desenvolvimento e a manutenção do código.

- **_Modelo (Model):_** O Modelo representa os dados e a lógica de negócios da aplicação. Ele é responsável por gerenciar o estado dos dados, responder a consultas sobre esses dados e processar as atualizações dos mesmos. O Modelo é independente da Visão e do Controlador, o que significa que ele pode ser reutilizado em diferentes contextos sem alterações.

- **_Visão (View):_** A Visão é responsável por apresentar a interface gráfica ao usuário. Ela exibe os dados do Modelo ao usuário e encaminha as interações do usuário para o Controlador. A Visão é passiva e não contém lógica de negócios; ela apenas exibe as informações fornecidas pelo Modelo.

- **_Controlador (Controller):_** O Controlador atua como intermediário entre o Modelo e a Visão. Ele interpreta as entradas do usuário, manipula as operações do Modelo e atualiza a Visão de acordo com as mudanças no Modelo. O Controlador contém a lógica de aplicação e coordena as interações entre o Modelo e a Visão.

&nbsp;&nbsp;&nbsp;&nbsp;A arquitetura MVC promove a separação de preocupações ao dividir uma aplicação em três componentes distintos, cada um responsável por uma área específica da aplicação. Isso torna o código mais modular, facilitando a manutenção e o teste da aplicação. Além disso, a arquitetura MVC é altamente escalável, permitindo que novos recursos sejam adicionados à aplicação sem afetar os componentes existentes. [1]
<br>

## 3. Arquitetura do Projeto

&nbsp;&nbsp;&nbsp;&nbsp;O projeto tem como objetivo desenvolver uma aplicação web que correlaciona dados sobre comportamentos humanos e as relações destes com a compra, adoção, preterimento de adquirir ou até o desinteresse no adquirimento de cachorros através de formulários e armazenar essas respostas em um banco de dados, de forma que esses dados possam ser acessados e disponibilizados para downloads, sendo que apenas o administrador tenha acesso a essas informações.

&nbsp;&nbsp;&nbsp;&nbsp;Para facilitar o entendimento da aplicação essa arquitetura foi dividida em duas partes: do administrador, que terá acesso aos gráficos e dados, e o usuário, que irá responder um dos quatro formulários.

<div align="center" width="100%">

<sub>Figura 1 - Arquitetura MVC: Admin</sub>

<img src="assets/mvc-admin.png">

<sup>Fonte: Material produzido pelo autor (2024).</sup>

</div>

&nbsp;&nbsp;&nbsp;&nbsp;A primeira arquitetura (figura 1) representa o acesso à plataforma e acesso aos gráficos, possuindo alguns elementos:

### Modelos (Models):

&nbsp;&nbsp;&nbsp;&nbsp;Em modelos foram estabelecidas cinco, a view de user que tem como elementos:

- ***id:*** o número de identificação associado ao conjunto de dados;
- ***nome:*** nome atrelado aos dados de login;
- ***e-mail:*** e-mail do admin;
- ***senha:*** senha do admin;
- ***role:*** o papel/acessos atribuídos aos usuários. 

Já o segundo deles, o formulárioTem, será o modelo de perguntas baseado em usuários que já possuem cachorro(s):
- ***listaDeInfos:*** todas as perguntas foram resumidas apenas por uma propriedade aqui na arquitetura por conta de questões de ilegibilidade pois a letra ficaria pequena, segue o documento que constam todas os dados a serem coletados:

<div align="center" width="100%">

<sub>Figura 3 - Página com perguntas do formulárioTem (parte 1)</sub>

<img src="assets/forms1.png">

<sup>Fonte: Material disponibilizado pelo stakeholder (2024).</sup>

</div>

<div align="center" width="100%">

<sub>Figura 4 - Página com perguntas do formulárioTem (parte 2)</sub>

<img src="assets/forms2.png">

<sup>Fonte: Material disponibilizado pelo stakeholder (2024).</sup>

</div>

O terceiro deles, o formulárioTeve, será o modelo de perguntas baseado em usuários que já possuíram cachorro(s):
- ***listaDeInfos:*** todas as perguntas foram resumidas apenas por uma propriedade aqui na arquitetura por conta de questões de ilegibilidade pois a letra ficaria pequena, ainda não há documentos disponibilizados que constam os exatos dados que precisam ser coletados com esse formulário.

O quarto, o formulárioQuerTer, será o modelo de perguntas baseado em usuários que estão pensando em adquirir cachorros, seja por meio da adoção ou da compra:
- ***listaDeInfos:*** todas as perguntas foram resumidas apenas por uma propriedade aqui na arquitetura por conta de questões de ilegibilidade pois a letra ficaria pequena, ainda não há documentos disponibilizados que constam os exatos dados que precisam ser coletados com esse formulário.

O último, o formulárioNãoQuer, será o modelo de perguntas baseado em usuários que não cogitam ter um cachorro e nem tiveram um:
- ***listaDeInfos:*** todas as perguntas foram resumidas apenas por uma propriedade aqui na arquitetura por conta de questões de ilegibilidade pois a letra ficaria pequena, ainda não há documentos disponibilizados que constam os exatos dados que precisam ser coletados com esse formulário.

### Controladores (Controllers):

&nbsp;&nbsp;&nbsp;&nbsp;Os controladores serão responsáveis por intermediar os processos entre o view e o model. Há dois métodos, sendo o primeiro o users:

- **gravar:** grava os dados de um usuário no banco de dados. como o INSPA irá intermediar essa parte do acesso admin, ainda não foi delimitado alguma maneira de cadastrar um admin diretamente pela aplicação;
- **buscar:** busca um usuário no banco de dados;
- **exibir:** irá direcionar para outra página caso os dados sejam validados, que será, nesse caso, o página de dashboard.

Já o segundo é o formulários: 
- **buscar:** busca um dos 4 formulários no banco de dados;
- **exibir:** irá direcionar para os gráficos específicos de acordo com os dados requisitados já na página do dashboard.

### Views (Views):

&nbsp;&nbsp;&nbsp;&nbsp;Nas views há dois elementos, sendo o primeiro deles o login, responsável por coletar dados específicos e mandar para a validação e, eventualmente, a interface com os dados:
- ***header:*** elemento visual (no wireframe do projeto, a navbar com os acessos às outras partes do site estará dentro da header)
- ***inputUsuário:*** nome do usuário;
- ***inputSenha:*** senha;
- ***botãoLogin:*** botão que inicia a requisição;
- ***footer:***  rodapé com informações adicionais, como informações de contato, links de política de privacidade ou direitos autorais.

Já o segundo é o dashboard que exibirá os gráficos e dados requisitados, que tem as seguintes propriedades:
- ***header:*** elemento visual (no wireframe do projeto, a navbar com os acessos às outras partes do site estará dentro da header)
- ***gráficos:*** gráficos plotados de acordo com a seleção dos filtros;
- ***caixaSeleção:*** caixa de selecão que faz a filtragem dos dados;
- ***botão:*** botão que inicia a requisição;
- ***footer:***  rodapé com informações adicionais, como informações de contato, links de política de privacidade ou direitos autorais.

### Fluxo de Operações

&nbsp;&nbsp;&nbsp;&nbsp;Seguindo essa arquitetura o fluxo de operações segue a seguinte linha de execução:

***linhas verdes escuras:***
1. O administrador acessa a página de login e se depara com a view Login.
2. O administrador preenche suas informações de acesso e clica no botao para validação.
3. Ao controlador aciona o método buscar em "users".
4. O controlador users usa o modelo de mesmo nome para verificar as informações no banco de dados.
5. Se as credenciais estiverem corretas, o controlador invoca utiliza a propriedade "exibir" para carregar a interface do dashboard.
6. A view do dashboard é apresentada ao administrador, possivelmente com informações personalizadas obtidas através do modelo usuarios.
<br>

***linhas rosas:***
1. Através das caixas de seleção e do botão do dashboard, uma requisição é aberta para filtrar as informações dos 4 formulários.
2. O botão aciona o método buscar do controlador formulários.
3. O controlador formulários utiliza dos modelos de cada formulário para puxar informações do banco de dados.
<br>

***linhas azuis:***
1. Assim, as informações coletadas no banco de dados são retornadas para a parte dos gráficos do dashboard, passando por cada um dos componentes.

<br><br>

<div align="center" width="100%">

<sub>Figura 5 - Arquitetura MVC: Usuário</sub>

<img src="assets/mvc-usuario.png">

<sup>Fonte: Material produzido pelo autor (2024).</sup>

</div>

&nbsp;&nbsp;&nbsp;&nbsp;Essa segunda arquitetura (figura 5) representa a parte do usuário e possui como elementos:

### Modelos (Models):

&nbsp;&nbsp;&nbsp;&nbsp;Em modelos foram estabelecidas cinco, a view de user que tem como elementos:

- ***id:*** o número de identificação associado ao conjunto de dados;
- ***nome:*** nome atrelado aos dados de login;
- ***e-mail:*** e-mail do usuário;
- ***senha:*** senha do usuário;
- ***role:*** o papel/acessos atribuídos aos usuários. 

Já o segundo deles, o formulárioTem, será o modelo de perguntas baseado em usuários que já possuem cachorro(s):
- ***listaDeInfos:*** todas as perguntas foram resumidas apenas por uma propriedade aqui na arquitetura por conta de questões de ilegibilidade pois a letra ficaria pequena, o documento com as perguntas equivalentes é o mesmo já apresentado nas figuras 3 e 4.

O terceiro deles, o formulárioTeve, será o modelo de perguntas baseado em usuários que já possuíram cachorro(s):
- ***listaDeInfos:*** todas as perguntas foram resumidas apenas por uma propriedade aqui na arquitetura por conta de questões de ilegibilidade pois a letra ficaria pequena, ainda não há documentos disponibilizados que constam os exatos dados que precisam ser coletados com esse formulário.

O quarto, o formulárioQuerTer, será o modelo de perguntas baseado em usuários que estão pensando em adquirir cachorros, seja por meio da adoção ou da compra:
- ***listaDeInfos:*** todas as perguntas foram resumidas apenas por uma propriedade aqui na arquitetura por conta de questões de ilegibilidade pois a letra ficaria pequena, ainda não há documentos disponibilizados que constam os exatos dados que precisam ser coletados com esse formulário.

O último, o formulárioNãoQuer, será o modelo de perguntas baseado em usuários que não cogitam ter um cachorro e nem tiveram um:
- ***listaDeInfos:*** todas as perguntas foram resumidas apenas por uma propriedade aqui na arquitetura por conta de questões de ilegibilidade pois a letra ficaria pequena, ainda não há documentos disponibilizados que constam os exatos dados que precisam ser coletados com esse formulário.

### Controladores (Controllers):

&nbsp;&nbsp;&nbsp;&nbsp;Os controladores serão responsáveis por intermediar os processos entre o view e o model. Há dois métodos, sendo o primeiro o users:

- **gravar:** grava os dados de um usuário no banco de dados;
- **buscar:** busca um usuário no banco de dados;
- **exibir:** irá direcionar para outra página caso os dados sejam validados, que será, nesse caso, o página com os formulários.

Já o segundo é o formulários: 
- **gravar:** grava os dados do formulário respondido no banco de dados.

### Views (Views):

&nbsp;&nbsp;&nbsp;&nbsp;Como Views foi estabelecida apenas uma, a view de login que tem como elementos:

- **navbar:** que é a barra de navegação;
- **formulario:** que é o formulário de login;
- **linkdeCadastro:** que é o link que redireciona para a página de cadastro;
- **botao:** que é o botão que irá enviar as informações para o controller.

### Fluxo de Operações

&nbsp;&nbsp;&nbsp;&nbsp;Seguindo essa arquitetura o fluxo de operações segue a seguinte linha de execução:

1. O administrador acessa a página de login e é apresentado com a view Login.
2. O administrador preenche suas credenciais no formulario e clica no botao para submeter o formulário.
3. A submissão do formulário aciona o método buscar no controlador usuarios.
4. O controlador usuarios usa o modelo usuarios para verificar as credenciais no banco de dados.
5. Se as credenciais estiverem corretas, o controlador invoca o método exibir para carregar o dashboard.
6. A view do dashboard é apresentada ao administrador, possivelmente com informações personalizadas obtidas através do modelo usuarios.

### Infraestrutura:

&nbsp;&nbsp;&nbsp;&nbsp;Considerando todas as informações apresentadas anteriormente, a aqruitetura MVC será implementada por meio do framework Sails.js, que proporcionará uma estrutura organizada para o desenvolvimento dessa aplicação. Além disso, os componentes a serem utilizados nessa aplicação consistem em:

**Sails.js**

&nbsp;&nbsp;&nbsp;&nbsp;O Sails.js é um framework MVC para Node.js que permite a criação de aplicações web e APIs e implementa o padrão MVC, oferencendo diversas configurações de rotas e suportando diversos bancos de dados, como o PostgreSQL. Dessa forma, esse framework foi escolhido com o intuito de acelerar o desenvolvimento do projeto e pelo fato da sua arquitetura promover a manutenção e a escalabilidade.

**Banco de Dados PostgreSQL**

&nbsp;&nbsp;&nbsp;&nbsp;O PostgreSQL é um sistema de gerenciamento de banco de dados relacional, sendo conhecido por ser robusto e confiável, além disso, ele pode ser integrado com o framework Sails.js o que irá facilitar no desenvolvimento da aplicação.

**Render**

&nbsp;&nbsp;&nbsp;&nbsp;O Render é um serviço de hospedagem de aplicações web que permite a criação de aplicações web e APIs, dessa forma será utilizado para hospedar a aplicação em Sails.js e o banco de PostgreSQL, de forma que esses possam ser escalados de acordo com a demanda, e que o processo de monitoramento da aplicaçãos seja facilitado.

**API dos Correios**

&nbsp;&nbsp;&nbsp;&nbsp;A API dos Correios é uma API que permite a consulta de CEPs e endereços, sendo utilizada para garantir a padronização das respostas nos formulários, de forma que os dados não sejam corrompidos.

&nbsp;&nbsp;&nbsp;&nbsp;Com base nessas tecnologias, no Sails.js, os models representam a estrutura de dados da aplicação e são usados para interagir com o PostgreSQL, definindo as regras de negócios e validações que são aplicadas antes que os dados sejam enviados ao banco de dados e garantindo a integridade e a qualidade dos dados persistidos. Enquanto, as views no Sails.js são geradas no lado do servidor e enviadas para o cliente, sendo responsáveis por apresentar a interface do usuário de forma dinâmica e interativa, utilizando os dados fornecidos pelos controladores. Por fim, os controladores no Sails.js lidam com a lógica de processamento de entrada de dados, manipulação de modelos e seleção de views. Eles atuam como o intermediário entre os models e as views, garantindo que as ações do usuário sejam tratadas corretamente e que as respostas adequadas sejam fornecidas.

### Justifique as escolhas feitas e como elas impactam o projeto.

&nbsp;&nbsp;&nbsp;&nbsp;A escolha do Sails.js como framework de desenvolvimento permite que a aplicação seja desenvolvida de forma mais rápida e organizada e que os dados sejam persistidos de forma segura e confiável. Além disso, A combinação do Sails.js com o PostgreSQL e o Render fornece uma base sólida para uma aplicação escalável e segura. Por fim, a API dos Correios complementa essa infraestrutura ao melhorar a qualidade dos dados e a experiência do usuário final.

#### Implicações da Arquitetura:

&nbsp;&nbsp;&nbsp;&nbsp;Com base em todas as escolhas definidas anteriormente, é esperado que o projeto apresente as seguintes implicações:

- **Escalabilidade:** A arquitetura MVC, em conjunto com o Sails.js e o Render, proporciona uma capacidade de escalar, garantindo que a aplicação possa lidar com um número crescente de usuários e dados sem uma perda de performance.

- **Manutenção:** O uso do framework baseado em MVC facilita a manutenção e atualizações da aplicação, sendo que as alterações em uma parte do sistema (Model, View ou Controller) podem ser feitas com um mínimo de impacto nas outras partes, reduzindo as falhas na aplicação.

- **Testabilidade:** Como o Sails.js suporta testes de unidade e integração, os testes automatizados são simplificados e podem ser executados com maior frequência.

- **Segurança:** A estrutura MVC do Sails.js ajudam a proteger a aplicação contra vulnerabilidades comuns ao encapsular as operações de banco de dados e ao separar a lógica de aplicação da apresentação do usuário. Além disso, o PostgreSQL oferece recursos de segurança que são fundamentais para a proteção de dados sensíveis.

- **Qualidade dos Dados:** A utilização da API dos Correios para validação dos dados de endereço aumenta a qualidade dos dados coletados e evita divergências nesses dados.

# Referências

[1] Introdução ao Padrão MVC: Primeiros passos na Arquitetura MVC. Disponível em: <https://www.devmedia.com.br/introducao-ao-padrao-mvc/29308>.

### Recursos Adicionais:

Documentação do Sails.js: https://github.com/balderdashy/sails
Tutorial do draw.io: https://m.youtube.com/watch?v=w3zm-wbmlpc
Exemplos de diagramas MVC: https://www.lucidchart.com/pages/templates
