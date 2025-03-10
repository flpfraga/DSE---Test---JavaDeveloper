**Nome: [Felipe Carlos Fraga]{.underline}** **Data: 03/08/2025**

<br></br>
---
---
<br></br>


**Questão 1 - Anagramas**

Resposta:\
[Repositório do Github com implementação](https://github.com/flpfraga/Anagramas)

<br></br>
---
---
<br></br>

**Questão 2 - equals e hashCode**

**Resposta:**

A sobrescrita da implementação do método equals() é geralmente feita em
classes do tipo *model,* quando queremos definir para uma classe
atributos lógicos que serão utilizados quando for feita alguma
comparação entre objetos dessa classe. Por sua vez, uma classe que não
tem a implementação de sobrescrita do método equals(), quando em uma
comparação de seus objetos, utilizará o endereço de mémoria daquele
objeto.

Já a sobrescrita do método hashCode() é necessária para definir e
atribuir um novo código hash para aquela uma classe. Assim, recursos
Java que utilizam comparação baseada em hash, como a Collection HashSet
por exemplo, conseguem fazer comparações através hash gerado pelos
atributos selecionados na sbrescrita deste método. Sempre que for feita
a sobrescrita do método equals() também deve se fazer a sobrescrita do
método hashCode().\
Cenários de teste:

1.  QUANDO uma classe sobrescrever os métodos equals() e hashCode()\
    E for definido dois objetos com parâmetros diferentes\
    E for esses dois objetos forem inseridos em uma lista do tipo Set\
    ENTÃO a comparação desses dois objetos deve retornar false\
    E a lista Set deve ter size() == 2

2.  QUANDO uma classe sobrescrever os métodos equals() e hashCode()\
    E for definido um objetos com parâmetros quisquer\
    E um outro objeto for definido e receber o o primeiro objeto criado\
    E for esses dois objetos forem inseridos em uma lista do tipo Set\
    ENTÃO a comparação desses dois objetos deve retornar true\
    E a lista Set deve ter size() == 1

3.  QUANDO uma classe sobrescrever os métodos equals() e hashCode()\
    E for definido dois objetos com parâmetros iguais\
    E for esses dois objetos forem inseridos em uma lista do tipo Set\
    ENTÃO a comparação desses dois objetos deve retornar true\
    E a lista Set deve ter size() == 1

4.  QUANDO uma classe sobrescrever o método equals() e não sobrescrevero
    método hashCode()\
    E for definido dois objetos com parâmetros diferentes\
    E for esses dois objetos forem inseridos em uma lista do tipo Set\
    ENTÃO a comparação desses dois objetos deve retornar false\
    E a lista Set deve ter size() == 2

5.  QUANDO uma classe sobrescrever o método equals() e não sobrescrevero
    método hashCode()\
    E for definido um objetos com parâmetros quisquer\
    E um outro objeto for definido e receber o o primeiro objeto criado\
    E for esses dois objetos forem inseridos em uma lista do tipo Set\
    ENTÃO a comparação desses dois objetos deve retornar true\
    E a lista Set deve ter size() == 1

6.  QUANDO uma classe sobrescrever o método equals() e não sobrescrevero
    método hashCode()\
    E for definido dois objetos com parâmetros iguais\
    E for esses dois objetos forem inseridos em uma lista do tipo Set\
    ENTÃO a comparação desses dois objetos deve retornar true\
    E a lista Set deve ter size() == 2

7.  QUANDO uma classe não sobrescrever os métodos equals() e hashCode()\
    E for definido dois objetos com parâmetros diferentes\
    E for esses dois objetos forem inseridos em uma lista do tipo Set\
    ENTÃO a comparação desses dois objetos deve retornar false\
    E a lista Set deve ter size() == 2

8.  QUANDO uma classe não sobrescrever os métodos equals() e hashCode()\
    E for definido um objetos com parâmetros quisquer\
    E um outro objeto for definido e receber o o primeiro objeto criado\
    E for esses dois objetos forem inseridos em uma lista do tipo Set\
    ENTÃO a comparação desses dois objetos deve retornar true\
    E a lista Set deve ter size() == 1

9.  QUANDO uma classe não sobrescrever os métodos equals() e hashCode()\
    E for definido dois objetos com parâmetros iguais\
    E for esses dois objetos forem inseridos em uma lista do tipo Set\
    ENTÃO a comparação desses dois objetos deve retornar false\
    E a lista Set deve ter size() == 2\
    \
    Exemplos nos repositórios:
    
    [Implementação](https://github.com/flpfraga/exemplosCodigo/tree/master/src/main/java/org/example/model_equals_hash_code)
    
    [Testes unitários](https://github.com/flpfraga/exemplosCodigo/tree/master/src/test/java)

<br></br>
---
---
<br></br>


**Questão 3 - Design Patterns**

**Resposta:**\
Acredito que o padrão adpter seria um boa opção para criar uma camada
intermediária entre o serviço precisamos utilizar e a biblioteca
terceira.

Primeiramente criamos uma interface que vai definir os métodos
necessários, de acordo com os requisitos do sistema. Em seguida, uma
classe adapter que extenda dessa interface. É na classe adapter também
que instanciamos a biblioteca externa, podendo até fazer alguns ajuste,
caso necessário, para atender os requisitos do sistema.\
As funcionalidades possibilitadas pela biblioteca externa, apenas são
acessadas pela interface. Deste modo, caso haja trocas futuras da
biblioteca de terceiros, basta fazer a modificação dentro da classe
adapter, com os devidos ajustes, caso necessário, que não haverá
impactos para o sistema.

Essa abordagem desacopla o sistema da biblioteca externa, que depende
apenas da interface. Ela também facilita permutar a biblioteca externa
utilizada por uma outra, uma vez que o sistema não é sua depende e ainda
permite fazer adaptações para a nova biblioteca funcionar conforme o
sistema requer.

Como pontos negativos, isso gera uma camada adicional de código com a
inclusão de uma nova camada. Também pode ser difícil a adaptação da nova
biblioteca dentro do adapter e dos requisitos do sistema.\
\
[Exemplo no repositório](https://github.com/flpfraga/exemplosCodigo/tree/master/src/main/java/org/example/design_patter)

<br></br>
---
---
<br></br>

**Questão 4 - Angular**
    **Resposta:**\
    Tenho algum conhecimento, mas não tenho experiência.

<br></br>
---
---
<br></br>

**Questão 5 - Otimização de processo batch com banco de dados e FTP**

**Resposta:**

O primeiro passo para um diagnóstico possíveis problemas é monitorar os sistema para possibilitar entender seu comportamento. Neste caso em específicos podemos identificar três processos, processamento batch, interação com banco de 
dados e interação com servidor FTP. Assim, é preciso gerar logs e dados de métricas para cada um desses processos separadamente e também para o processo como um todo. Isto é possível com Splunk para monitorar logs, Promethues para coletar e armazenar dados de métricas e o Grafana, que recebe dados de métricas e possibilita, através de dashboards, visualização do comportamento do sistema. Para estes processos seria importante monitorar uso de CPU e memória, tempo de execução de cada um dos processos separados, taxa de erros, número de consultas ao banco de dados, número de interações com o processo FTP.

O monitoramento é a chave para atuar na melhoria do sistema. Com ele é possível identificar gargalos criados por:
- uso excessivo de memória e CPU que podem afetar a velocidade do processamento
- horários de maior latência na interação com processo FTP
- número de consultas ao banco de dados
- processos que estão gerando muitos erros
- processos que alto tempo de execução

Para otimizar as consulta de banco de dados algumas possíveis soluções seria:
- Criar um pool de conexões para evitar que o sistema tenha que abrir e fechar diversas conexões com o banco de dados;
- Utilizar do Redis para possibilitar que consultas repetitivas seja realizada no cache e não no banco de dados;
- Utilizar de Store procedures para a execução de múltiplas queries, melhorando o desempenho e reduzindo a latência, uma vez que procedures ficam armazenadas na memória do banco
- Indexação para reduzir tempo de busca;

A execução lógica é a melhoria do código em si, valendo para isto também do uso de recursos da linguagem de programação. Deve ser observado no código:
- Evitar aninhamentos de laços de repetição. Essa prática aumenta as ordens de grandezas dos algoritmos, que por sua vez, levam mais tempo para processar.
- Verificar a possibilidade do HashMap que tem tempo de busca otimizado através de chaves.
- Uso de paralelismo através de threads e parallelStream
- Utilizar ferramentas como SonarQube que identifica pontos de melhoria no código.

A melhoria da interação com o processo FTP está fortemente condicionada a limitações da internet. Assim algumas práticas podem melhorar essa interação:
- Compressão dos arquivos a serem enviados, diminui o número de pacotes e também o tempo de transmissão;
- Escolha de horários de menor latência para a execução dos processos batch. Horários noturnos e outros que podem ser identificados através do monitoramento, tendem a ter menor tráfego de rede e reduzir a latência.
- Identificar as interações que podem ser feitas de forma assíncrona. Deste modo, não bloqueamos o sistema para continuar sua execução.

<br></br>
---
---
<br></br>

**Questão 6 - SQL Injection**

**Resposta:**

Atualmente faço grande uso de ORMs para comunicação com o banco de
dados, com JPA e Hibernate. Por si só o ORM traz bastante segurança
contra a injeção SQL. No entanto, ao utilizar queries nativas ou
dinâmicas, jamais faço a contatenação dos parâmetros na query. Para este
fim faço uso da parametrização. Isto porque a ao concatenar parâmetros
em uma query, um atacante pode utilizar desse parâmetro para passar
algum comando SQL, que ao ser concatenado, vai ser compilado como parte
da query. Já ao utilizar de parametrização, os parâmetros são tratados
apenas como parâmetros.

Exemplos:

1.  Query dinâmica:

        public Optional<Produto> buscarProdutoPorNome(String nome){
        EntityManager entityManager = entityManagerFactory.createEntityManager();
        Optional<Produto> produto = entityManager.createQuery(
            "SELECT p FROM Produto p WHERE p.nome = : nome", Produto.class)
            .setParameter("nome", nome)
            .getSingleResult();
        return produtos;
        }

2.  Query Nativa:

        public Produto buscarProdutoPorNome(String nome){
        EntityManager entityManager = entityManagerFactory.createEntityManager();
        Query query = entityManager.createQuery(
            "SELECT p FROM Produto p WHERE p.nome = : nome", Produto.class);
        query.setParameter(1, nome);
        return (Produto) query.getSingleResult();
        }

3.  Com Spring Data JPA

        @Query("SELECT p FROM Produto p WHERE p.nome = :nome")
        Produto buscarPorNome(@Param("nome") String nome);

Para garantir a segurança da camada do banco de dados, além das boas
práticas para evitar a injeçào SQL, podemos tomar outras medidas. O
acesso ao banco de dados deve ser evitado por usuários administrativos e
deve ser pautado pelo princípio do privilêgio mínimo, ou seja, dar a
usuários apenas a permissão necessára para desempenhar sua função, seja
para inserir, consultar, deletar.

Fazer validação dos dados de entrada evita que dados inesperados sejam
enviados para a consulta. Por exemplo, anotar uma parâmetros com \@email
vai garantir que apenas padrão de caracteres tipo email chegue na camada
de banco de dados.

<br></br>
---
---
<br></br>

**Questão 7 - Queries SQL**

a. Returns the names of all Salesperson that don't have any order with Samsonic.**
    
    SELECT s.Name
    FROM Salesperson s
    LEFT JOIN Orders o ON s.ID = o.salesperson_id
    WHERE o.customer_id != 4

b. Updates the names of Salesperson that have 2 or more orders. It's necessary to add an '\*' in the end of the name.

    UPDATE Salesperson s
    SET s.Name = CONCAT(s.Name, '*')
    WHERE s.ID IN (
        SELECT s.ID
        FROM Salesperson s
        JOIN Orders o ON s.ID = o.salesperson_id
        GROUPY BY s.ID
        HAVING COUNT(o.ID) >= 2
    );

c. Deletes all Ssalesperson that placed orders to the city of Jackson.

    DELETE FROM Salesperson s
    WHERE s.ID IN (
        SELECT DISTINCT s.ID
        FROM Salesperson s
        JOIN Orders o ON s.ID = o.salesperson_id
        JOIN Customer c ON o.customer_id = c.ID
        WHERE c.City = 'Jackson'
    );

d. The total sales amount for each Salesperson. If the salesperson hasn't sold anything, show zero.

    SELECT s.Name, COALESCE(SUM(o.Amount), 0) AS total
    FROM Salesperson s
    LEFT JOIN Orders o ON s.ID = o.salesperson_id
    GROUP BY s.Name;

<br></br>
---
---
<br></br>

**Questão 8 - História do usuário**

**Resposta:**

**Título: Inclusão de funcionalidade para gerenciamento de plantas**

1.  **Objetivo**

    1.  **User Story**
        > **Como** usuário administrador do sistema\
        > **Quero** criar, atualizar e buscar plantas\
        > **Para que** possa gerenciar todo o sistema de XYZ

    2.  **Cenário Atual**
        > Atualmente o sistema XYZ não dispõe de entrada de dados para
        > plantas e de funcionalidades para gerenciar as plantas no
        > sistema como persisitir, atualizar, buscar ou deletar.

    3.  **Problema a ser resolvido**
        > Deverá ser habilitado uma nova entrada de dados, onde serão
        > informados dados relativos a planta, bem como funcionalidades
        > de gerenciamento das informações relativas.

    4.  **Regras de Negócio**

        1.  **Objeto Planta**\
            Uma planta qualquer pode ser descrita por dois atributos:
            código e descrição. Assim, o mecanismo de entrada de dados,
            bem como as funcionalidades de gerenciamento, devem ter
            suporte para tratamendo desses dois campos

        2.  **Código da planta - atributo**\
            O código é o atributo do tipo numérico que identifica uma
            planta. É obrigatório ser informado e deve ser único para
            cada uma das plantas, ou seja, não poderão haver duas
            plantas com o mesmo código.

        3.  **Descrição da planta -- atributo**\
            A descrição é um breve comentário sobre aquela planta mas
            não é obrigatório ser informada. Deverá ser do tipo
            alfanumérico com tamanho máximo de 10 caracteres.

        4.  **Atualização de dados**\
            A funcionalidade de atualizar dados de uma planta deverá ser
            somente aplicada ao atributo descrição, sendo vedado
            modificar o código de uma planta já salva no sistema.

        5.  **Prevenção a duplicidade de código**\
            Como o código de uma planta deve ser um numérico **único**,
            sempre que houver uma solicitação de inclusão de nova
            planta, deve se garantir que o código do novo objeto não
            existe no sistema. Assim, antes de executar o salvamento da
            nova planta, será necessário compara o novo código com todos
            os demais já salvos. Caso não exista, procede o salvamento.
            Caso já exista, retorna mensagem de erro para o usuário,
            informando que o código já existe.

        6.  **Permissões gerais**\
            Qualquer usuário devidamente logado no sistema deve
            conseguir inserir nas entradas de dados as informações
            relativas a plantas. É permitido a esses usuários apenas
            criar novas plantas, atualizar dados e buscar plantas já
            cadastradas no sistema XYZ.

        7.  **Permissões exclusivas**\
            É exclusivo ao usuário com permissão de administrador,
            utilizar da funcionalidade de excluir plantas. Assim,
            estando o usuário logado, deve ser verificados se o mesmo
            tem permissão de administrador para ser habilitado ou não na
            entrada de dados, opção de deleção. Deverá ser também
            validado a permissão do usuário nas funcionalidades de
            gerenciamento, quando houver solicitação de deletar alguma
            planta.

        8.  **Validações do código**\
            Quando houver solicitação para salvar uma nova planta no
            sistema, tanto a entrada de dados quanto as funcionalidades
            de gerenciamento, deverão implementar validações para
            certificar que:
            -   o Código não é nulo ou branco;
            -   o Código é do tipo numérico;

            Caso essas validações falhem, a planta não deverá ser salva e deverá
            retornar mensagem de erro ao usuário, informado o problema.

        9.  **Validações da descrição**\
            Quando houver solicitação para salvar ou atualizar uma planta no
            sistema, tanto a entrada de dados quanto as funcionalidades de
            gerenciamento, deverão implementar validações para certificar que:

            -   a descrição é um código alfanumérico com letras e números, mas
                que não deve contér caracteres especiais, caracteres de controle
                e símbolos matemáticos;

            -   o descrição tem tamanho máximo de 10 caracteres;

            Caso essas validações falhem, a planta não deverá ser salva ou
            atualizada e deverá retornar mensagem de erro ao usuário, informado o
            problema.

    5.  **Teste de Funcionalidade**

        1.  **Validações do código**

            -   **Caso de sucesso**

                -   O usuário consegue criar uma planta informando um código
                    númerico, único e não nulo;

                -   O usuário consegue buscar uma planta informando um
                    código de uma planta salva no sistema

            -   **Casos de Erro:**

                -   O usuário tenta criar uma planta com código nulo e obter
                    o erro de campo obrigatório;

                -   O usuário tenta criar uma planta com um código
                    alfanumérico e obtém o erro de tipo inválido;

                -   O usuário tenta criar uma planta com um código já
                    existente no sistema e obtém o erro de duplicidade de
                    código;

        2.  **Validações da descrição**

            -   **Caso de sucesso**

                -   O usuário consegue criar uma planta informando a
                    descrição no formato alfanumérico com 10 caracteres;

                -   O usuário consegue criar uma planta não informando a
                    descrição;

                -   O usuário consegue atualizar uma planta informando um
                    código de uma planta já existente no sistema e a
                    descrição no formato alfanumérico com 10 caracteres;

                -   O usuário consegue atualizar uma planta informando um
                    código de uma planta já existente no sistema e não
                    informando a descrição;

            -   **Casos de erro**

                -   O usuário tenta criar uma planta informando símbolos
                    matemáticos na descrição e obtém erro de tipo inválido;

                -   O usuário tenta criar uma planta informando caractéres
                    especiais na descrição e obtém erro de tipo inválido;

                -   O usuário tenta criar uma planta informando descrição
                    com 11 caractéres e obtém erro de tamanho inválido;

                -   O usuário tenta atualizar uma planta informando símbolos
                    matemáticos na descrição e obtém erro de tipo inválido;

                -   O usuário tenta atualziar uma planta informando
                    caractéres especiais na descrição e obtém erro de tipo
                    inválido;

                -   O usuário tenta atualizar uma planta informando
                    descrição com 11 caractéres e obtém erro de tamanho
                    inválido;

        3.  **Validação de permissão exclusivas**

            -   **Casos de sucesso**

                -   O usuário administrativo faz a deleção de uma planta
                    informado um código existem no sistema;

            -   **Casos de erro**

                -   O usuário não administrativo faz login e o sistema não
                    exibe a opção de deleção;

        4.  **Validação de permissão geral**

            -   **Casos de sucesso**

                -   Um usuário administrativo ou não administrativo busca
                    uma planta informando um código existente no sistema;

                -   Um usuário administrativo ou não administrativo cria uma
                    nova planta informando um código novo e uma descrição;

                -   Um usuário administrativo ou não administrativo
                    atualizar uma nova planta informando um código novo e
                    uma descrição;

    6.  **Cenários de teste**

        1.  **Cenário 1 -- Criar planta com sucesso**\
            **QUANDO** o usuário for criar uma nova planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2"**\
            **ENTÃO** uma nova planta vai ser criada no sistema

        2.  **Cenário 2 -- Atualizar planta com sucesso**\
            **DADO** que a planta de código **123** está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário for atualizar uma planta\
            **E** inserir no campo o valor **123**\
            **E** inseri no campo descrição o valor "**c3d4**"\
            **ENTÃO** a planta de campo 123 vai ter a descrição atualizada

        3.  **Cenário 3 -- Buscar planta com sucesso**\
            **DADO** que a planta de código **123** está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário for buscar uma planta\
            **E** inserir no campo de busca o valor **123**\
            **ENTÃO** a planta de campo 123 vai ser exibida na tela

        4.  **Cenário 4 -- Deletar planta com sucesso**\
            **DADO** que a planta de código **123** está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário com permissões administrativas for deletar
            uma planta\
            **E** inserir no campo de busca o valor **123**\
            **ENTÃO** a planta de campo 123 vai ser deletada

        5.  **Cenário 5 -- Criar planta com erro tipo código**\
            **QUANDO** o usuário for criar uma nova planta\
            **E** inserir no campo código o valor **123A**\
            **E** inserir no campo descrição o valor "**a1b2"**\
            **ENTÃO** será retornado um erro informado que o código deve ser
            do tipo numérico

        6.  **Cenário 6 -- Criar planta com erro código nulo**\
            **QUANDO** o usuário for criar uma nova planta\
            **E** não inserir valor no campo código\
            **E** inserir no campo descrição o valor "**a1b2"**\
            **ENTÃO** será retornado um erro informado que o código é
            obrigatório

        7.  **Cenário 7 -- Criar planta com erro código duplicado**\
            **DADO** que a planta de código **123** está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário for criar uma nova planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2"**\
            **ENTÃO** será retornado um erro informado que o código da nova
            planta já existe

        8.  **Cenário 8 -- Criar planta com erro tipo descrição**\
            **QUANDO** o usuário for criar uma nova planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2+"**\
            **ENTÃO** será retornado um erro informado que o texto da
            descrição contém caractéres inválidos

        9.  **Cenário 9 -- Criar planta com erro tipo descrição**\
            **QUANDO** o usuário for criar uma nova planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2@"**\
            **ENTÃO** será retornado um erro informado que o texto da
            descrição contém caractéres inválidos

        10. **Cenário 10 -- Criar planta com erro tamanho descrição**\
            **QUANDO** o usuário for criar uma nova planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2c3d4e5f"**\
            **ENTÃO** será retornado um erro informado que o tamanho da
            descrição é maior que o permitido

        11. **Cenário 11 -- Atualizar planta com erro tipo descrição**\
            **DADO** que a planta de código **123** está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário for atualizr uma planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2+"**\
            **ENTÃO** será retornado um erro informado que o texto da
            descrição contém caractéres inválidos

        12. **Cenário 12 -- Atualizar planta com erro tipo descrição**\
            **DADO** que a planta de código **123** está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário for atualizar uma planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2@"**\
            **ENTÃO** será retornado um erro informado que o texto da
            descrição contém caractéres inválidos

        13. **Cenário 13 -- Atualizar planta com erro tamanho descrição**\
            **DADO** que a planta de código **123** está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário for atualziar uma planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2c3d4e5f"**\
            **ENTÃO** será retornado um erro informado que o tamanho da
            descrição é maior que o permitido

        14. **Cenário 14 -- Atualizar planta informando código não
            cadastrado**\
            **DADO** que a planta de código **123** não está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário for atualziar uma planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2"**\
            **ENTÃO** será retornado um erro informado que não existem
            plantas com o código informado

        15. **Cenário 15 -- Deletar uma planta com usuário administrativo**\
            **DADO** que a planta de código **123** está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário administrativo logar no sistema\
            **E** for deletar uma planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2"**\
            **ENTÃO** a planta será deletada com sucesso

        16. **Cenário 16 -- Deletar uma planta com usuário administrativo e
            informando código não cadastrado**\
            **DADO** que a planta de código **123** não está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário administrativo logar no sistema\
            **E** for deletar uma planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2"**\
            **ENTÃO** será retornado um erro informado que não existem
            plantas com o código informado

        17. **Cenário 17 -- Deletar uma planta com usuário não
            administrativo**\
            **DADO** que a planta de código **123** está devidamente
            cadastrada no sistema\
            **QUANDO** o usuário não administrativo logar no sistema\
            **E** for deletar uma planta\
            **E** inserir no campo código o valor **123**\
            **E** inserir no campo descrição o valor "**a1b2"**\
            **ENTÃO** será retornado uma mensgem de usuário proibido

    7.  **Arquitetura**

    ![image](https://github.com/user-attachments/assets/9d6c3ab3-0183-4bca-80e8-f0b63c6ae958)

<br></br>
---
---
<br></br>

**Questão 9 - Descrição de testes para funcionalidade usuário**

**Resposta:**

-   **Tipos de teste:**

    -   **Testes unitários:** Os testes unitários são os testes básicos
        de qualquer código. Eles vão garantir o comportamento esperado
        de cada um dos métodos do sistema. Importante exigir uma
        cobertura de teste acima de 85%. Além da garantia de
        qualidadade, adotar técnicas como TDD acelera o desenvolvimento
        correto do sistema, evitando a ocorrência de bugs.

    -   **Testes de funcionalidade:** Como forma de garantir que as
        regras do sistema estão corretamente implementadas utilizaria de
        testes funcionais. Aplicaria estes testes na garantia de que:

        -   Apenas usuários administradores conseguem excluir outros
            usuários;

        -   Não ha cadastro em duplicidade de emails;

        -   Ao criar um novo usuário, os campos email e nome são
            válidos;

        -   Usuários conseguem atuaizar suas informações

    -   **Testes de integração:** As funcionalidades a serem
        implementadas envolvem vários componentes do sistema, como
        frontend, backend e banco de dados. Assim, será possível testar
        se os dados inseridos na interface do usuário foram corretamente
        enviado para o backend, se os usuários cadastrados, excluídos ou
        atualizados estão sendo inserido corretamente no sistema.

    -   **Teste End-to-End:** Por fim implementaria um teste para
        verificar a funcionalidade de ponta a ponta, como verificar se
        um usuário informado na interface do usuário foi corretamente
        validado no backend e inserido no banco de dado. Esse teste vai
        garantir o correto comportamento das funcionalidade, do ponto de
        vista do usuário final.

-   **Casos extremos:**

    -   **Entradas muito grandes:** Campos como endereço e nome podem
        possuir um tamanho muito grande pois não existem regras que
        impeçam o tamanho de uma nome. Imagine um usuário da cidade Vila
        Bela da Santíssima Trindade, uma cidade que tem 32 caractéres.\
        Para controlar o tamanho dos nomes, faria a inserção regras de
        validação com tamanho máximo para essas entradas. Estas regras
        se aplicariam tanto na interface do usuário quando no backend,
        retornando ao usuário uma mensagem que a entrada excedeu o
        limite.

    -   **Entradas com caractéres especiais:** Assim como nomes grandes,
        caractéres especiais podem gerar problemas de codificação no
        banco de dados. Assim, incluiria também validações para impedir
        essas entradas.

    -   **Deleção de usuários em lote:** Como forma de impedir um ataque
        que vise deletar usuários do banco de dados, implantaria a
        exclusão lógica do usuário. Essa exclusão consiste em uma flag
        que indica se o usuário está ativo ou inativo. Assim, um ataque
        ao sistema através da funcionaludade de deleção, vai apenas
        inativar o usuário.

    -   **Entrada de nomes muito curtos:** Diferente de nomes que podem
        ser muito grandes, nomes muito curtos podem indicar erro de
        inserção de dados. Assim, faria validação do número mínimo de
        caractéres e palavras para nomes, tanto na interface do usuário
        quando no backend, sempre retornando mensagem relativa ao
        usuário.

    -   **Emails em formato incomum:** Inserir validações com um padrão
        que os emails submetidos devem ter.

    -   **Excluir um usuário não cadastrado:** Antes de fazer a exclusão
        do usuário, faria uma busca pelo usuário para verificar se está
        presente no banco de dados. Caso não esteja, retorna mensagem de
        erro para o usuário.

-   **Código de cenário de teste:**

    -   **Cenário 1 -- Teste unitário criar usuário:**
        
            void testCriarUsuarioComSucesso(){
            Usuario usuario = new Usuario ();
            usuario.setNome("Alan Turing");
            usuario.setEmail("alanTuring_123@gmail.com");
            usuario.setEndereco("Rua A, 12 -- Centro, Sao Paulo-SP");
            usuario.setTelefone("11999990000");
            
            resposta = usuarioService.cadastrar(usuario);
            
            assertNotNull(resposta.getId());
            assertEquals("Alan Turing", resposta.getNome());
            assertEquals("alanTuring_123@gmail.com ", resposta.getEmail);
            assertEquals(" Rua A, 12 -- Centro, Sao Paulo-SP ", resposta.getEndereco());
            assertEquals("11999990000", resposta.getTelefone());
            
            }

    -   **Cenário 2 -- Teste funcional de excluir um usuário com role
        administrador**

        -   Utilizar o postaman para gerar um token de um usuário
            administrador;

        -   Fazer uma request para a URL de deletar usuário, informando
            no Header **Authorization = {token_gerado}** e nos params o
            **email={email_do_usuario}**;

        -   Verificar o retorno de sucesso do sistema;

        -   Executar no banco de dados a query para buscar o usuário.
            Não deve retornar nenhuma linha:
            
                SELECT * FROM Usuario u WHERE u.email = {email_do_usuario}

    -   **Cenário 3 -- Teste funcional de excluir um usuário sem role
        administrador**

        -   Utilizar o postaman para gerar um token de um usuário não
            administrador;

        -   Fazer uma request para a URL de deletar usuário, informando
            no Header **Authorization = {token_gerado}** e nos params o
            **email={email_do_usuario}**;

        -   Verificar o retorno de erro do sistema;

        -   Executar no banco de dados a query para buscar o usuário.
            Deve ser retornar uma linha com o usuário de email
            informado:
            
                SELECT * FROM Usuario u WHERE u.email = {email_do_usuario}
