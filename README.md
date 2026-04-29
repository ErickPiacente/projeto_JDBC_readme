# projeto_JDBC_readme
TRABALHO FASE 1
integrantes: Erick Piacente, Kauã de Lira, Enzo Bicalho.

EXPLICAÇÃO SOBRE DAO (com exemplos)

Na criação sistemas que utilizam banco de dados, é preferível que o código seja compreensível, seguro, simples e de fácil manutenção. Nesse contexto, surgem padrões e tecnologias que auxiliam na organização. Entre eles, destacam-se o padrão DAO (Data Access Object), que organiza o acesso de dados

O DAO é um padrão de projeto que tem como principal objetivo separar a lógica de acesso a dados da lógica de negócio da aplicação. Ele centraliza as operações de persistência, como CRUD e consultas, em uma camada própria, isolando o restante da aplicação da forma como os dados são armazenados, em termos práticos, isso ajuda a manter o sistema mais legível e facilita a evolução da tecnologia de banco de dados usada.

A utilização do padrão DAO traz benefícios, como:

melhor organização do código
facilidade de manutenção
reutilização de código
maior segurança
desacoplamento entre camadas

Exemplo: Nesse cenário, existe uma entidade chamada Cliente, que representa os dados armazenados no banco, como nome e e-mail. A aplicação pode possuir uma classe chamada ClienteDao, responsável por realizar operações como inserir, buscar, atualizar e excluir clientes no banco de dados. A camada de serviço chama esse DAO, e o DAO cuida do SQL e do mapeamento entre registros do banco e objetos da aplicação.

ciclo de vida da conexão JDBC

O JDBC (Java Database Connectivity) é uma API que permite que aplicações Java se conectem a bancos de dados relacionais, sendo o fluxo básico é registrar o driver, abrir a conexão, executar comandos SQL, processar resultados e encerrar a conexão.

O processo segue uma sequência simples: abrir a conexão, preparar o SQL, executar, tratar o resultado (se houver) e fechar tudo no final. Em sistemas maiores, esse ciclo pode ser otimizado com o uso de pool de conexões, evitando abrir e fechar conexões o tempo todo.
Parte do Erick:

PRATICAS DE SEGURANÇA
As praticas de segurança são feitas para deixar o caminho do programa com o banco mais seguro e evitando coisas como vazamento de dado ou a exclusão de informações.
Com isso temos uma falha que é a SQL Injection, ela é uma falha de segurança que gera problemas como os vazamentos de dados.
Então ai entra a PreparedStatement, ele resolve o problema de SQL injection separando comandos SQL dos valores inseridos, ele para de ser entendido como SQL e começa a ser visto como dado.
Então sempre deve se lembrar de usar o PreparedStatement, outra coisa importante é validar as entradas do usuário para poder verificar se o usuário fez algo de estranho, e poder encontrar quem foi.

CHECKLIST DE QUALIDADE
Primeira coisa, você deve sempre lembrar de fechar o PreparedStatement, Statement etc, se acabar se esquecendo pode ocorrer coisas como vazamento de memória ou pode travar o seu sistema, então lembrar de fechar é algo necessário.
Segundo, tratar exceções, se algo acontecer e esse algo não estava plabejado, como uma informações colocada errada, você deve incrubir essa excessão e sempre lembrar de mostrar mensagens informando sobre o erro.

ORGANIZAÇÃO DO CÓDIGO
O recomendado é que você crie classes especificas(DAO) para deixar a organização do seu código boa e facil de se ler.
Sempre lembre tambem de evitar a repitição de codigos, como fazer uma linha que já faz algo que outra faz, você não precisa que ela faça a mesma coisa, então é sempre bom verificar o código para ver se não tem nenhuma parte repetida.

FONTES

DEVMEDIA:
https://www.devmedia.com.br/introducao-ao-jdbc/43900
ALURA:
https://www.alura.com.br/artigos/conhecendo-o-jdbc?
srsltid=AfmBOoqt4XmCnuU6JRZvvJLe-L0EQM5ZO79eUGjq_WDhu-QIW8b6FtK-
IBM:
https://www.ibm.com/docs/pt-br/cics-ts/6.x?topic=server-java-database-connectivity-jdbc
DIO:
https://www.dio.me/articles/jdbc-java-database-connectivity-uma-visao-geral-57b6b447ec8d(Não usamos muito)


Parte do Kauã:

 MAPA CONCEITUAL — Persistência de Dados em Java
  DAO (Data Access Object)
Padrão de projeto que separa a lógica de acesso a dados da lógica de negócio.
Responsável por realizar operações como:
create (inserir)
read (buscar)
update (atualizar)
delete (remover)
Facilita:
Manutenção
Testes
Reutilização de código
       Relação:
Usa JDBC para acessar o banco
Depende da ConnectionFactory para conexões

  JDBC (Java Database Connectivity)
API padrão do Java para conectar e manipular bancos de dados.
Permite executar comandos SQL:
SELECT
INSERT
UPDATE
DELETE
Componentes principais:
Connection → conexão com o banco
PreparedStatement → execução de SQL
ResultSet → resultado das consultas
       Relação:
Base para implementação do DAO
Utiliza conexões fornecidas pela ConnectionFactory

 ConnectionFactory
Classe responsável por criar e gerenciar conexões com o banco.
Centraliza:
URL do banco
Usuário
Senha
Vantagens:
Evita repetição de código
Facilita manutenção (mudança de banco, por exemplo)
      Relação:
Fornece Connection para o DAO
Trabalha diretamente com JDBC

  ResultSet Mapping
Processo de converter dados do banco (ResultSet) em objetos Java.
Exemplo:
Tabela usuario → objeto Usuario
Etapas:
Executa consulta (SELECT)
Recebe ResultSet
Percorre os dados (while(rs.next()))
Mapeia para objeto
      Relação:
Usado dentro do DAO
Depende do JDBC

 Exceptions (Exceções)
Tratamento de erros durante acesso ao banco.
Tipos comuns:
SQLException
Erros de conexão
Erros de sintaxe SQL
Boas práticas:
Usar try-catch
Encapsular exceções em exceções personalizadas
Não expor detalhes sensíveis
       Relação:
Ocorrem em operações com JDBC
Devem ser tratadas no DAO

🔹 Transactions (Transações)
Conjunto de operações que devem ser executadas como uma unidade única.
Propriedades (ACID):
Atomicidade → tudo ou nada
Consistência → mantém regras do banco
Isolamento → não interfere em outras transações
Durabilidade → dados persistem após commit
Comandos:
commit() → confirma alterações
rollback() → desfaz alterações
    Relação:
Controladas via Connection (JDBC)
Usadas dentro do DAO