# Confidencial

## Nome: Felipe Carlos Fraga  
**Data:** 03/08/2025  

Responda em português ou inglês.

## Questões

### 1. Write a Java program to solve the following problem:

Você deve criar uma função utilitária para um aplicativo de processamento de texto que gere todos os anagramas possíveis a partir de um grupo de letras distintas. Por exemplo, a entrada `{a, b, c}` deve retornar a saída: `abc, acb, bac, bca, cab, cba`.

#### Requisitos Adicionais:
- O programa deve aceitar qualquer grupo de letras distintas como entrada e produzir o resultado correto.
- Otimize para legibilidade e clareza.
- Inclua validações básicas (ex: garantir que a entrada não esteja vazia e contenha apenas letras).
- Escreva testes unitários para validar sua função com pelo menos três casos de teste diferentes, incluindo casos extremos (ex: entrada com uma única letra ou entrada vazia).
- Documente claramente o código, explicando a lógica para geração de anagramas.

**Resposta:**
Repositório do Github com implementação: [GitHub - Anagramas](https://github.com/flpfraga/Anagramas)

---

### 2. Provide an example scenario where overriding the `equals()` method is necessary in Java.

#### Explicação:
A sobrescrita do método `equals()` é geralmente feita em classes do tipo model, quando queremos definir atributos lógicos para comparação de objetos. Caso contrário, a comparação será feita pelo endereço de memória.

Já a sobrescrita do método `hashCode()` é necessária para definir um novo código hash para a classe. Recursos do Java como `HashSet` dependem do hash gerado pelos atributos selecionados na sobrescrita deste método.

Sempre que `equals()` for sobrescrito, `hashCode()` também deve ser.

#### Cenários de Teste:

1. **Objetos diferentes inseridos em um `Set`**
   - Se dois objetos têm parâmetros diferentes e são inseridos em um `Set`, a comparação deve retornar `false` e `size() == 2`.

2. **Objetos referenciados sendo iguais**
   - Se um objeto é atribuído a outro e ambos inseridos em um `Set`, a comparação deve retornar `true` e `size() == 1`.

3. **Objetos com atributos iguais inseridos em um `Set`**
   - Se dois objetos possuem os mesmos valores, a comparação deve retornar `true` e `size() == 1`.

Exemplos de código: [GitHub - equals & hashCode](https://github.com/flpfraga/exemplosCodigo/tree/master/src/main/java/org/example/model_equals_hash_code)

Testes unitários: [GitHub - Testes](https://github.com/flpfraga/exemplosCodigo/tree/master/src/test/java)

---

### 3. Explain how you would use a design pattern to decouple your code from a third-party library.

#### Padrão Utilizado: Adapter

Criamos uma **interface** definindo os métodos necessários. Em seguida, uma **classe adapter** que estende essa interface e instancia a biblioteca externa. Isso desacopla o sistema, permitindo trocar a biblioteca no futuro sem impacto.

**Vantagens:**
- Facilidade para trocar a biblioteca externa.
- Permite ajustes para atender os requisitos do sistema.

**Limitações:**
- Introduz uma camada adicional de código.
- Pode ser difícil adaptar novas bibliotecas.

Exemplo no repositório: [GitHub - Adapter Pattern](https://github.com/flpfraga/exemplosCodigo/tree/master/src/main/java/org/example/design_patter)

---

### 4. Discuss the techniques you use to prevent SQL injection attacks.

#### Técnicas Utilizadas:
- Uso de ORMs como JPA e Hibernate.
- **Queries parametrizadas**, ao invés de concatenação de strings.
- Controle de permissões baseado no **princípio do privilégio mínimo**.
- **Validação de entrada** de dados.

#### Exemplos:

##### Query Dinâmica:
```java
public Optional<Produto> buscarProdutoPorNome(String nome){
    EntityManager entityManager = entityManagerFactory.createEntityManager();
    return entityManager.createQuery("SELECT p FROM Produto p WHERE p.nome = :nome", Produto.class)
        .setParameter("nome", nome)
        .getSingleResult();
}
```

##### Query Nativa:
```java
public Produto buscarProdutoPorNome(String nome){
    EntityManager entityManager = entityManagerFactory.createEntityManager();
    Query query = entityManager.createNativeQuery("SELECT * FROM Produto WHERE nome = ?", Produto.class);
    query.setParameter(1, nome);
    return (Produto) query.getSingleResult();
}
```

Com **Spring Data JPA**:
```java
@Query("SELECT p FROM Produto p WHERE p.nome = :nome")
Produto buscarPorNome(@Param("nome") String nome);
```

---

### 5. Given the tables below, write SQL queries to:

#### a) Retornar os nomes dos vendedores sem pedidos com a empresa Samsonic.
```sql
SELECT s.Name
FROM Salesperson s
LEFT JOIN Orders o ON s.ID = o.salesperson_id
WHERE o.customer_id != 4;
```

#### b) Atualizar nomes de vendedores com 2 ou mais pedidos, adicionando `*` no final do nome.
```sql
UPDATE Salesperson
SET Name = CONCAT(Name, '*')
WHERE ID IN (
    SELECT salesperson_id
    FROM Orders
    GROUP BY salesperson_id
    HAVING COUNT(ID) >= 2
);
```

#### c) Deletar vendedores que fizeram pedidos para clientes na cidade de Jackson.
```sql
DELETE FROM Salesperson
WHERE ID IN (
    SELECT DISTINCT salesperson_id
    FROM Orders
    JOIN Customer ON Orders.customer_id = Customer.ID
    WHERE Customer.City = 'Jackson'
);
```

#### d) Retornar o total de vendas por vendedor, mostrando `0` se não houver vendas.
```sql
SELECT s.Name, COALESCE(SUM(o.Amount), 0) AS total
FROM Salesperson s
LEFT JOIN Orders o ON s.ID = o.salesperson_id
GROUP BY s.Name;
```

---

## Considerações Finais

Caso precise de mais detalhes ou exemplos, consulte os repositórios compartilhados acima.

