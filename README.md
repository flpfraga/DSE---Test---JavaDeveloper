![Confidencial](Aspose.Words.f67f4c56-e0dd-47f6-a176-84787d34ac8d.001.png)

**Nome:  Felipe Carlos Fraga**  **Data: 03/08/2025**

*Responda em português ou inglês.*

1\. **Write a Java program to solve the following problem:**

**You are tasked with creating a utility function for a text-processing application. The function must generate all possible anagrams from a given group of distinct letters. For example, the input {a, b, c} should return the output: abc, acb, bac, bca, cab, cba.**

**Additional Requirements:**

1\. **The program should accept any group of distinct letters as input and produce the correct result.**

1\. **Optimize for readability and clarity.**

1\. **Include basic validation (e.g., ensure the input is non-empty and contains only letters).**

1\. **Write unit tests to validate your function with at least three different test cases, including edge cases (e.g., input with a single letter or empty input).**

1\. **Document your code clearly, explaining the logic for generating anagrams.**

   **Resposta:**

   Repositório do Github com implementação: <https://github.com/flpfraga/Anagramas> 

1\. **Provide an example scenario where overriding the equals() method is necessary in Java. Explain the key considerations when implementing this method, such as ensuring it aligns with the hashCode() method. Include code examples if possible.**

**Resposta:** 

A sobrescrita da implementação do método equals() é geralmente feita em classes do tipo *model,* quando queremos definir para uma classe atributos lógicos que serão utilizados quando for feita alguma comparação entre objetos dessa classe. Por sua vez, uma classe que não tem a implementação de sobrescrita do método equals(), quando em uma comparação de seus objetos, utilizará o endereço de mémoria daquele objeto.

Já a sobrescrita do método hashCode() é necessária para definir e atribuir um novo código hash para aquela uma classe. Assim, recursos Java que utilizam comparação baseada em hash, como a Collection HashSet por exemplo, conseguem fazer comparações através hash gerado pelos atributos selecionados na sbrescrita deste método. Sempre que for feita a sobrescrita do método equals() também deve se fazer a sobrescrita do método hashCode(). 

Cenários de teste:

1\. QUANDO uma classe sobrescrever os métodos equals() e hashCode()

   `  `E for definido dois objetos com parâmetros diferentes

   `  `E for esses dois objetos forem inseridos em uma lista do tipo Set

   ENTÃO a comparação desses dois objetos deve retornar false

   `  `E a lista Set deve ter size() == 2

1\. QUANDO uma classe sobrescrever os métodos equals() e hashCode()

   `  `E for definido um objetos com parâmetros quisquer

   `  `E um outro objeto for definido e receber o o primeiro objeto criado

   `  `E for esses dois objetos forem inseridos em uma lista do tipo Set

   ENTÃO a comparação desses dois objetos deve retornar true

   `  `E a lista Set deve ter size() == 1

1\. QUANDO uma classe sobrescrever os métodos equals() e hashCode()

   `  `E for definido dois objetos com parâmetros iguais

   `  `E for esses dois objetos forem inseridos em uma lista do tipo Set

   ENTÃO a comparação desses dois objetos deve retornar true

   `  `E a lista Set deve ter size() == 1

1\. QUANDO uma classe sobrescrever o método equals() e não sobrescrevero método hashCode()

   `  `E for definido dois objetos com parâmetros diferentes

   `  `E for esses dois objetos forem inseridos em uma lista do tipo Set

   ENTÃO a comparação desses dois objetos deve retornar false

   `  `E a lista Set deve ter size() == 2

1\. QUANDO uma classe sobrescrever o método equals() e não sobrescrevero método hashCode()

   `  `E for definido um objetos com parâmetros quisquer

   `  `E um outro objeto for definido e receber o o primeiro objeto criado

   `  `E for esses dois objetos forem inseridos em uma lista do tipo Set

   ENTÃO a comparação desses dois objetos deve retornar true

   `  `E a lista Set deve ter size() == 1

1\. QUANDO uma classe sobrescrever o método equals() e não sobrescrevero método hashCode()

   `  `E for definido dois objetos com parâmetros iguais

   `  `E for esses dois objetos forem inseridos em uma lista do tipo Set

   ENTÃO a comparação desses dois objetos deve retornar true

   `  `E a lista Set deve ter size() == 2

1\. QUANDO uma classe não sobrescrever os métodos equals() e hashCode()

   `  `E for definido dois objetos com parâmetros diferentes

   `  `E for esses dois objetos forem inseridos em uma lista do tipo Set

   ENTÃO a comparação desses dois objetos deve retornar false

   `  `E a lista Set deve ter size() == 2

1\. QUANDO uma classe não sobrescrever os métodos equals() e hashCode()

   `  `E for definido um objetos com parâmetros quisquer

   `  `E um outro objeto for definido e receber o o primeiro objeto criado

   `  `E for esses dois objetos forem inseridos em uma lista do tipo Set

   ENTÃO a comparação desses dois objetos deve retornar true

   `  `E a lista Set deve ter size() == 1

1\. QUANDO uma classe não sobrescrever os métodos equals() e hashCode()

   `  `E for definido dois objetos com parâmetros iguais

   `  `E for esses dois objetos forem inseridos em uma lista do tipo Set

   ENTÃO a comparação desses dois objetos deve retornar false

   `  `E a lista Set deve ter size() == 2

   Exemplos no repositório: [https://github.com/flpfraga/exemplosCodigo/tree/master/src/main/java/org/example/model_equals_hash_code

   ](https://github.com/flpfraga/exemplosCodigo/tree/master/src/main/java/org/example/model_equals_hash_code)Teste unitários: <https://github.com/flpfraga/exemplosCodigo/tree/master/src/test/java> 

**

1\. **Explain how you would use a design pattern to decouple your code from a third-party library that might be replaced in the future. Describe the advantages and limitations of your chosen approach, and provide a small code snippet illustrating its application.**

**Resposta:**

Acredito que o padrão adpter seria um boa opção para criar uma camada intermediária entre o serviço precisamos utilizar e a biblioteca terceira.

Primeiramente criamos uma interface que vai definir os métodos necessários, de acordo com os requisitos do sistema. Em seguida, uma classe adapter que extenda dessa interface. É na classe adapter também que instanciamos a biblioteca externa, podendo até fazer alguns ajuste, caso necessário, para atender os requisitos do sistema. 

As funcionalidades possibilitadas pela biblioteca externa, apenas são acessadas pela interface. Deste modo, caso haja trocas futuras da biblioteca de terceiros, basta fazer a modificação dentro da classe adapter, com os devidos ajustes, caso necessário, que não haverá impactos para o sistema.

Essa abordagem desacopla o sistema da biblioteca externa, que depende apenas da interface. Ela também facilita permutar a biblioteca externa utilizada por uma outra, uma vez que o sistema não é sua depende e ainda permite fazer adaptações para a nova biblioteca funcionar conforme o sistema requer.

Como pontos negativos, isso gera uma camada adicional de código com a inclusão de uma nova camada. Também pode ser difícil a adaptação da nova biblioteca dentro do adapter e dos requisitos do sistema.

Exemplo no repositório: <https://github.com/flpfraga/exemplosCodigo/tree/master/src/main/java/org/example/design_patter>

1\. **Describe your experience with Angular, including its core features and use cases. Provide an example of a practical application where you used Angular and include a code snippet demonstrating a key feature, such as component communication, data binding, or service integration.**

   **Resposta:**

   Tenho algum conhecimento, mas não tenho experiência.

**

1\. **Discuss the techniques you use to prevent SQL injection attacks in web applications. Provide examples of code showing secure implementations, such as using parameterized queries or ORMs. Mention any additional measures you take to secure the database layer.**

**Resposta:**

Atualmente faço grande uso de ORMs para comunicação com o banco de dados, com JPA e Hibernate. Por si só o ORM traz bastante segurança contra a injeção SQL. No entanto, ao utilizar queries nativas ou dinâmicas, jamais faço a contatenação dos parâmetros na query. Para este fim faço uso da parametrização. Isto porque a** ao concatenar parâmetros em uma query, um atacante pode utilizar desse parâmetro para passar algum comando SQL, que ao ser concatenado, vai ser compilado como parte da query. Já ao utilizar de parametrização, os parâmetros são tratados apenas como parâmetros.

Exemplos:

1\. Query dinâmica:

   public Optional<Produto> buscarProdutoPorNome(String nome){

   `  `EntityManager entityManager = entityManagerFactory.createEntityManager();

   `  `Optional<Produto> produto = entityManager.createQuery("SELECT p FROM Produto p      WHERE p.nome = : nome", Produto.class)

     .setParameter("nome", nome)

     .getSingleResult();

   `  `return produtos;

   }

1\. Query Nativa:

   public Produto buscarProdutoPorNome(String nome){

   `  `EntityManager entityManager = entityManagerFactory.createEntityManager();

   `  `Query query = entityManager.createQuery("SELECT p FROM Produto p WHERE 

   `  `p.nome = : nome", Produto.class);

   `  `query.setParameter(1, nome);

   `  `return (Produto) query.getSingleResult();

   }

1\. Com Spring Data JPA

   @Query("SELECT p FROM Produto p WHERE p.nome = :nome")

   Produto buscarPorNome(@Param("nome") String nome);

Para garantir a segurança da camada do banco de dados, além das boas práticas para evitar a injeçào SQL, podemos tomar outras medidas. O acesso ao banco de dados deve ser evitado por usuários administrativos e deve ser pautado pelo princípio do privilêgio mínimo, ou seja, dar a usuários apenas a permissão necessára para desempenhar sua função, seja para inserir, consultar, deletar.

Fazer validação dos dados de entrada evita que dados inesperados sejam enviados para a consulta. Por exemplo, anotar uma parâmetros com @email vai garantir que apenas padrão de caracteres tipo email chegue na camada de banco de dados.

**

1\. **Describe the steps you would take to diagnose and improve the performance of a batch process that interacts with a database and an FTP server. Explain how you would identify bottlenecks, optimize database queries, improve logic execution, and enhance file transfer efficiency. Provide examples of tools or techniques you would use during the analysis.**

|**Salesperson**|**Customer** |

| :-: | :-: |

|||

|**ID** |**Name** |**Age** |**Salary** |

| :- | :- | :- | :- |

|1 |Abe |61 |140000 |

|2 |Bob |34 |44000 |

|5 |Chris |34 |40000 |

|7 |Dan |41 |52000 |

|8 |Ken |57 |115000 |

|11 |Joe |38 |38000 |

|||

| :- | :- |

|**ID** |**Name** |**City** |**Industry Type** |

| :- | :- | :- | :- |

|4 |Samsonic |Pleasant |J |

|6 |Panasung |Oaktown |J |

|7 |Samony |Jackson |B |

|9 |Orange |Jackson |B |

|||

| :- | :- |

|**Orders** |

| :-: |

||

|**ID** |**order\_date** |**customer\_id** |**salesperson\_id** |**Amount** |

| :- | :- | :- | :- | :- |

|10 |8/2/96 |4 |2 |540 |

|20 |1/30/99 |4 |8 |1800 |

|30 |7/14/95 |9 |1 |460 |

|40 |1/29/98 |7 |2 |2400 |

|50 |2/3/98 |6 |7 |600 |

|60 |3/2/98 |6 |7 |720 |

|70 |5/6/98 |9 |7 |150 |

| |

| :-: |

1\. **Given the tables above, write the SQL query that:**

   **a. Returns the names of all Salesperson that don't have any order with Samsonic.**

   SELECT s.Name 

   FROM Salesperson s 

   LEFT JOIN Orders o ON s.ID = o.salesperson\_id

   WHERE o.customer\_id != 4

   **

   **

   **b. Updates the names of Salesperson that have 2 or more orders. It's necessary to add an '\*' in the end of the name.**

   UPDATE Salesperson s

   SET s.Name = CONCAT(s.Name, '\*')

   WHERE s.ID IN (

   SELECT s.ID

   FROM Salesperson s

   JOIN Orders o ON s.ID = o.salesperson\_id

   GROUPY BY s.ID

   HAVING COUNT(o.ID) >= 2

   );

   **c. Deletes all Ssalesperson that placed orders to the city of Jackson.**

   **

   ` `DELETE FROM Salesperson s

   WHERE s.ID IN (

   SELECT DISTINCT s.ID

   FROM Salesperson s

   JOIN Orders o ON s.ID = o.salesperson\_id

   JOIN Customer c ON o.customer\_id = c.ID

   WHERE c.City = 'Jackson'

   );

   **

   **

   **d. The total sales amount for each Salesperson. If the salesperson hasn't sold anything, show zero.**

   SELECT s.Name, COALESCE(SUM(o.Amount), 0) AS total

   FROM Salesperson s

   LEFT JOIN Orders o ON s.ID = o.salesperson\_id

   GROUP BY s.Name;

1\. **The customer has a system called XYZ and intends to start updates split into 3 phases. The requirements for the first phase are as follows:**

1\. **Enable new data entries in the system, which will serve as input for the second phase.**

1\. **Implement functionality to create, update, delete, and search plants.**

   1. **Plants should have the following attributes:**

      1. **Code: Numeric only, mandatory, and unique.**

      1. **Description: Alphanumeric, up to 10 characters, optional.**

   1. **Only admin users can delete plants.**

1\. **Ensure that the system prevents duplication of plant codes.**

**Task:**

` `**Based on the above information:**

1\. **Write a use case or user story for this scenario, ensuring that it clearly addresses the requirements.**

1\. **Highlight any business rules or assumptions relevant to the solution.**

1\. **Describe any validations or security measures you would implement in the system.**

1\. **Suggest how you would test this functionality, including examples of edge cases.**

**Resposta:**

**Título: Inclusão de funcionalidade para gerenciamento de plantas**

1\. **Objetivo**

   1. **User Story**

      **Como** usuário administrador do sistema

      **Quero** criar, atualizar e buscar plantas

      **Para que** possa gerenciar todo o sistema de XYZ

   1. **Cenário Atual**

      Atualmente o sistema XYZ não dispõe de entrada de dados para plantas e de funcionalidades para gerenciar as plantas no sistema como persisitir, atualizar, buscar ou deletar.

   1. **Problema a ser resolvido**

      Deverá ser habilitado uma nova entrada de dados, onde serão informados dados relativos a planta, bem como funcionalidades de gerenciamento das informações relativas.

   1. **Regras de Negócio**

      1. **Objeto Planta**

         Uma planta qualquer pode ser descrita por dois atributos: código e descrição. Assim, o mecanismo de entrada de dados, bem como as funcionalidades de gerenciamento, devem ter suporte para tratamendo desses dois campos

      1. **Código da planta  - atributo**

         O código é o atributo do tipo numérico que identifica uma planta. É obrigatório ser informado e deve ser único para cada uma das plantas, ou seja, não poderão haver duas plantas com o mesmo código.

      1. **Descrição da planta -- atributo**

         A descrição é um breve comentário sobre aquela planta mas não é obrigatório ser informada. Deverá ser do tipo alfanumérico com tamanho máximo de 10 caracteres.

      1. **Atualização de dados**

         A funcionalidade de atualizar dados de uma planta deverá ser somente aplicada ao atributo descrição, sendo vedado modificar o código de uma planta já salva no sistema.

      1. **Prevenção a duplicidade de código**

         Como o código de uma planta deve ser um numérico **único**, sempre que houver uma solicitação de inclusão de nova planta, deve se garantir que o código do novo objeto não existe no sistema. Assim, antes de executar o salvamento da nova planta, será necessário compara o novo código com todos os demais já salvos. Caso não exista, procede o salvamento. Caso já exista, retorna mensagem de erro para o usuário, informando que o código já existe.

      1. **Permissões gerais**

         Qualquer usuário devidamente logado no sistema deve conseguir inserir nas entradas de dados as informações relativas a plantas. É permitido a esses usuários apenas criar novas plantas, atualizar dados e buscar plantas já cadastradas no sistema XYZ.

      1. **Permissões exclusivas**

         É exclusivo ao usuário com permissão de administrador, utilizar da funcionalidade de excluir plantas. Assim, estando o usuário logado, deve ser verificados se o mesmo tem permissão de administrador para ser habilitado ou não na entrada de dados, opção de deleção. Deverá ser também validado a permissão do usuário nas funcionalidades de gerenciamento, quando houver solicitação de deletar alguma planta.

      1. ` `**Validações do código**

         Quando houver solicitação para salvar uma nova planta no sistema, tanto a entrada de dados quanto as funcionalidades de gerenciamento, deverão implementar validações para certificar que:

         1. o Código não é nulo ou branco;

         1. o Código é do tipo numérico;

Caso essas validações falhem, a planta não deverá ser salva e deverá retornar mensagem de erro ao usuário, informado o problema.

1\. **Validações da descrição**

   Quando houver solicitação para salvar ou atualizar uma planta no sistema, tanto a entrada de dados quanto as funcionalidades de gerenciamento, deverão implementar validações para certificar que:

   1. a descrição é um código alfanumérico com letras e números, mas que não deve contér caracteres especiais, caracteres de controle e símbolos matemáticos;

   1. o descrição tem tamanho máximo de 10 caracteres;

Caso essas validações falhem, a planta não deverá ser salva ou atualizada e deverá retornar mensagem de erro ao usuário, informado o problema.

1\. **Teste de Funcionalidade**

   1. **Validações do código**

      1. **Caso de sucesso**

         1. O usuário consegue criar uma planta informando um código númerico, único e não nulo;

         1. O usuário consegue buscar uma planta informando um código de uma planta salva no sistema

      1. **Casos de Erro:**

         1. O usuário tenta criar uma planta com código nulo e obter o erro de campo obrigatório;

         1. O usuário tenta criar uma planta com um código alfanumérico e obtém o erro de tipo inválido;

         1. O usuário tenta criar uma planta com um código já existente no sistema e obtém o erro de duplicidade de código;

   1. **Validações da descrição**

      1. **Caso de sucesso**

         1. O usuário consegue criar uma planta informando a descrição no formato alfanumérico com 10 caracteres;

         1. O usuário consegue criar uma planta não informando a descrição;

         1. O usuário consegue atualizar uma planta informando um código de uma planta já existente no sistema e a descrição no formato alfanumérico com 10 caracteres;

         1. O usuário consegue atualizar uma planta informando um código de uma planta já existente no sistema e não informando a descrição;

      1. **Casos de erro**

         1. O usuário tenta criar uma planta informando símbolos matemáticos na descrição e obtém erro de tipo inválido;

         1. O usuário tenta criar uma planta informando caractéres especiais na descrição e obtém erro de tipo inválido;

         1. O usuário tenta criar uma planta informando descrição com 11 caractéres e obtém erro de tamanho inválido;

         1. O usuário tenta atualizar uma planta informando símbolos matemáticos na descrição e obtém erro de tipo inválido;

         1. O usuário tenta atualziar uma planta informando caractéres especiais na descrição e obtém erro de tipo inválido;

         1. O usuário tenta atualizar uma planta informando descrição com 11 caractéres e obtém erro de tamanho inválido;

   1. **Validação de permissão exclusivas**

      1. **Casos de sucesso**

         1. O usuário administrativo faz a deleção de uma planta informado um código existem no sistema;

      1. **Casos de erro**

         1. O usuário não administrativo faz login e o sistema não exibe a opção de deleção;

   1. **Validação de permissão geral**

      1. **Casos de sucesso**

         1. Um usuário administrativo ou não administrativo busca uma planta informando um código existente no sistema;

         1. Um usuário administrativo ou não administrativo cria uma nova planta informando um código novo e uma descrição;

         1. Um usuário administrativo ou não administrativo atualizar uma nova planta informando um código novo e uma descrição;

1\. **Cenários de teste**

   1. **Cenário 1 -- Criar planta com sucesso**

      **QUANDO** o usuário for criar uma nova planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2"**

      **ENTÃO** uma nova planta vai ser criada no sistema

   1. **Cenário 2 -- Atualizar planta com sucesso**

      **DADO** que a planta de código **123** está devidamente cadastrada no sistema

      **QUANDO** o usuário for atualizar uma planta

      `  `**E** inserir no campo o valor **123**

      `  `**E** inseri no campo descrição o valor "**c3d4**"

      **ENTÃO** a planta de campo 123 vai ter a descrição atualizada

   1. **Cenário 3 -- Buscar planta com sucesso**

      **DADO** que a planta de código **123** está devidamente cadastrada no sistema

      **QUANDO** o usuário for buscar uma planta

      `  `**E** inserir no campo de busca o valor **123**

      **ENTÃO** a planta de campo 123 vai ser exibida na tela

   1. **Cenário 4 -- Deletar planta com sucesso**

      **DADO** que a planta de código **123** está devidamente cadastrada no sistema

      **QUANDO** o usuário com permissões administrativas for deletar uma planta

      `  `**E** inserir no campo de busca o valor **123**

      **ENTÃO** a planta de campo 123 vai ser deletada

   1. **Cenário 5 -- Criar planta com erro tipo código**

      **QUANDO** o usuário for criar uma nova planta

      `  `**E** inserir no campo código o valor **123A**

      `  `**E** inserir no campo descrição o valor "**a1b2"**

      **ENTÃO** será retornado um erro informado que o código deve ser do tipo numérico

   1. **Cenário 6 -- Criar planta com erro código nulo**

      **QUANDO** o usuário for criar uma nova planta

      `  `**E** não inserir valor no campo código

      `  `**E** inserir no campo descrição o valor "**a1b2"**

      **ENTÃO** será retornado um erro informado que o código é obrigatório

   1. **Cenário 7 -- Criar planta com erro código duplicado**

      **DADO** que a planta de código **123** está devidamente cadastrada no sistema

      **QUANDO** o usuário for criar uma nova planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2"**

      **ENTÃO** será retornado um erro informado que o código da nova planta já existe

   1. **Cenário 8 -- Criar planta com erro tipo descrição**

      **QUANDO** o usuário for criar uma nova planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2+"**

      **ENTÃO** será retornado um erro informado que o texto da descrição contém caractéres inválidos

   1. **Cenário 9 -- Criar planta com erro tipo descrição**

      **QUANDO** o usuário for criar uma nova planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2@"**

      **ENTÃO** será retornado um erro informado que o texto da descrição contém caractéres inválidos

   1. **Cenário 10 -- Criar planta com erro tamanho descrição**

      **QUANDO** o usuário for criar uma nova planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2c3d4e5f"**

      **ENTÃO** será retornado um erro informado que o tamanho da descrição é maior que o permitido

   1. **Cenário 11 -- Atualizar planta com erro tipo descrição**

      **DADO** que a planta de código **123** está devidamente cadastrada no sistema

      **QUANDO** o usuário for atualizr uma planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2+"**

      **ENTÃO** será retornado um erro informado que o texto da descrição contém caractéres inválidos

   1. **Cenário 12 -- Atualizar planta com erro tipo descrição**

      **DADO** que a planta de código **123** está devidamente cadastrada no sistema

      **QUANDO** o usuário for atualizar uma planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2@"**

      **ENTÃO** será retornado um erro informado que o texto da descrição contém caractéres inválidos

   1. **Cenário 13 -- Atualizar planta com erro tamanho descrição**

      **DADO** que a planta de código **123** está devidamente cadastrada no sistema

      **QUANDO** o usuário for atualziar uma planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2c3d4e5f"**

      **ENTÃO** será retornado um erro informado que o tamanho da descrição é maior que o permitido

   1. **Cenário 14 -- Atualizar planta informando código não cadastrado**

      **DADO** que a planta de código **123** não está devidamente cadastrada no sistema

      **QUANDO** o usuário for atualziar uma planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2"**

      **ENTÃO** será retornado um erro informado que não existem plantas com o código informado

   1. **Cenário 15 -- Deletar uma planta com usuário administrativo**

      **DADO** que a planta de código **123** está devidamente cadastrada no sistema

      **QUANDO** o usuário administrativo logar no sistema

      `  `**E** for deletar uma planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2"**

      **ENTÃO** a planta será deletada com sucesso

   1. **Cenário 16 -- Deletar uma planta com usuário administrativo e informando código não cadastrado**

      **DADO** que a planta de código **123** não** está devidamente cadastrada no sistema

      **QUANDO** o usuário administrativo logar no sistema

      `  `**E** for deletar uma planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2"**

      **ENTÃO** será retornado um erro informado que não existem plantas com o código informado

   1. **Cenário 17 -- Deletar uma planta com usuário não administrativo**

      **DADO** que a planta de código **123** está devidamente cadastrada no sistema

      **QUANDO** o usuário não administrativo logar no sistema

      `  `**E** for deletar uma planta

      `  `**E** inserir no campo código o valor **123**

      `  `**E** inserir no campo descrição o valor "**a1b2"**

      **ENTÃO** será retornado uma mensgem de usuário proibido

1\. **Arquitetura**

1\. **Consider the following description of a system functionality:**

   ` `**User Registration**

- **A screen allows users to insert, delete, or update user information.**

- **Each user has properties: name, email, address, and phone, where name and email are mandatory fields.**

- **Emails must be unique across all users.**

- **Only admin users can delete other users.**

**Task:**

1\. **Describe the types of tests you would implement (e.g., unit, integration, or end-to-end tests) and explain the scenarios you would test to ensure the functionality works as expected.**

1\. **Provide examples of edge cases and how you would handle them.**

1\. **Include an example of a test case in code or pseudocode for one or more scenarios.**

**Resposta:**

- **Tipos de teste:**

  - **Testes unitários:** Os testes unitários são os testes básicos de qualquer código. Eles vão garantir o comportamento esperado de cada um dos métodos do sistema. Importante exigir uma cobertura de teste acima de 85%. Além da garantia de qualidadade, adotar técnicas como TDD acelera o desenvolvimento correto do sistema, evitando a ocorrência de bugs.

  - **Testes de funcionalidade:** Como forma de garantir que as regras do sistema estão corretamente implementadas utilizaria de testes funcionais. Aplicaria estes testes na garantia de que:

    - Apenas usuários administradores conseguem excluir outros usuários;

    - Não ha cadastro em duplicidade de emails;

    - Ao criar um novo usuário, os campos email e nome são válidos;

    - Usuários conseguem atuaizar suas informações

  - **Testes de integração:** As funcionalidades a serem implementadas envolvem vários componentes do sistema, como frontend, backend e banco de dados. Assim, será possível testar se os dados inseridos na interface do usuário foram corretamente enviado para o backend, se os usuários cadastrados, excluídos ou atualizados estão sendo inserido corretamente no sistema.

  - **Teste End-to-End:** Por fim implementaria um teste para verificar a funcionalidade de ponta a ponta, como verificar se um usuário informado na interface do usuário foi corretamente validado no backend e inserido no banco de dado. Esse teste vai garantir o correto comportamento das funcionalidade, do ponto de vista do usuário final.

- **Casos extremos:**

  - **Entradas muito grandes:** Campos como endereço e nome podem possuir um tamanho muito grande pois não existem regras que impeçam o tamanho de uma nome. Imagine um usuário da cidade Vila Bela da Santíssima Trindade, uma cidade que tem 32 caractéres. 

    Para controlar o tamanho dos nomes, faria a inserção regras de validação com tamanho máximo para essas entradas. Estas regras se aplicariam tanto na interface do usuário quando no backend, retornando ao usuário uma mensagem que a entrada excedeu o limite.

  - **Entradas com caractéres especiais:** Assim como nomes grandes, caractéres especiais podem gerar problemas de codificação no banco de dados. Assim, incluiria também validações para impedir essas entradas.

  - **Deleção de usuários em lote:** Como forma de impedir um ataque que vise deletar usuários do banco de dados, implantaria a exclusão lógica do usuário. Essa exclusão consiste em uma flag que indica se o usuário está ativo ou inativo. Assim, um ataque ao sistema através da funcionaludade de deleção, vai apenas inativar o usuário.

  - **Entrada de nomes muito curtos:** Diferente de nomes que podem ser muito grandes, nomes muito curtos podem indicar erro de inserção de dados. Assim, faria validação do número mínimo de caractéres e palavras para nomes, tanto na interface do usuário quando no backend, sempre retornando mensagem relativa ao usuário.

  - **Emails em formato incomum:** Inserir validações com um padrão que os emails submetidos devem ter.

  - **Excluir um usuário não cadastrado:** Antes de fazer a exclusão do usuário, faria uma busca pelo usuário para verificar se está presente no banco de dados. Caso não esteja, retorna mensagem de erro para o usuário.

- **Código de cenário de teste:**

  - **Cenário 1 -- Teste unitário criar usuário:**

    void testCriarUsuarioComSucesso(){

    `  `Usuario usuario = new Usuario ();

    `  `usuario.setNome("Alan Turing");

    `  `usuario.setEmail("alanTuring\_123@gmail.com");

    `  `usuario.setEndereco("Rua A, 12 -- Centro, Sao Paulo-SP");

    `  `usuario.setTelefone("11999990000");

    `  `resposta = usuarioService.cadastrar(usuario);

    `  `assertNotNull(resposta.getId());

    `  `assertEquals("Alan Turing", resposta.getNome());

    `  `assertEquals("alanTuring\_123@gmail.com ", resposta.getEmail);

    `  `assertEquals(" Rua A, 12 -- Centro, Sao Paulo-SP ", resposta.getEndereco());

    `  `assertEquals("11999990000", resposta.getTelefone());

    }

  - **Cenário 2 -- Teste funcional de excluir um usuário com role administrador**

    - Utilizar o postaman para gerar um token de um usuário administrador;

    - Fazer uma request para a URL de deletar usuário, informando no Header **Authorization = {token\_gerado}** e nos params o **email={email\_do\_usuario}**;

    - Verificar o retorno de sucesso do sistema;

    - Executar no banco de dados a query para buscar o usuário. Não deve retornar nenhuma linha:

      SELECT \* FROM Usuario u WHERE u.email = {email\_do\_usuario}

  - **Cenário 3 -- Teste funcional de excluir um usuário sem role administrador**

    - Utilizar o postaman para gerar um token de um usuário não administrador;

    - Fazer uma request para a URL de deletar usuário, informando no Header **Authorization = {token\_gerado}** e nos params o **email={email\_do\_usuario}**;

    - Verificar o retorno de erro do sistema;

    - Executar no banco de dados a query para buscar o usuário. Deve ser retornar uma linha com o usuário de email informado:

      SELECT \* FROM Usuario u WHERE u.email = {email\_do\_usuario}

![Confidencial](Aspose.Words.f67f4c56-e0dd-47f6-a176-84787d34ac8d.002.png)
