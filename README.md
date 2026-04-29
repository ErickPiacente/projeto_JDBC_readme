# projeto_JDBC_readme
Parte do Enzo:

Parte do Erick:

PRATICAS DE SEGURANÇA
As praticas de segurança são feitas para deixar o caminho do programa com o banco mais seguro e evitando coisas como vazamento de dado ou a exclusão de informações.
Com isso temos uma falha que é a SQL Injection, ela é uma falha de segurança que gera problemas como os vazamentos de dados.
Então ai entra a PreparedStatement, ele resolve o problema de SQL injection separando comandos SQL dos valores inseridos, ele para de ser entendido como SQL e começa a ser visto como dado.
Então sempre deve se lembrar de usar o PreparedStatement, outra coisa importante é validar as entradas do usuário para poder verificar se o usuário fez algo de estranho, e poder encontrar quem foi.

CHECKLIST DE QUALIDADE
Primeira coisa, você deve sempre lembrar de fechar o PreparedStatement, Statement etc, se acabar se esquecendo pode ocorrer coisas como vazamento de memória ou pode travar o seu sistema, então lembrar de fechar é algo necessário.
Segundo, tratar exceções, se algo acontecer e esse algo não estava plabejado, como uma informações colocada errada, você deve incrubir essa exceção e sempre lembrar de mostrar mensagens informando sobre o erro.

ORGANIZAÇÃO DO CÓDIGO
O recomendado é que você crie classes especificas(DAO) para deixar a organização do seu código boa e facil de se ler.
Sempre lembre tambem de evitar a repitição de codigos, como fazer uma linha que já faz algo que outra faz, você não precisa que ela faça a mesma coisa, então é sempre bom verificar o código para ver se não tem nenhuma parte repetida.




Parte do Kauã:
