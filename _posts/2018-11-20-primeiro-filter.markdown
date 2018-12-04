---
layout: default
title: "Filter"
nav_order: 1
parent : Stream
---


# Filter


{: .fw-400 }
O método `filter()` como o nome sugere, é utilizado para filtrar dados de um `Stream`. Aqui vamos aprender como utilizar esse método, com
um exemplo simples, e fazendo uma comparação de como era feito antes do Java 8.
{: .lh-default}    
Imagine o seguinte objeto :

```java
public class Pessoa {
        private String nome;
        private Integer idade;
        private String sexo;
        //getter and setter
    }
```


{: .fw-400 }
Imagine agora que dado um `List<Pessoa>`, precisamos filtrar apenas as pessoas acima de **25 anos**, então implementamos o seguinte método :    

```java
public List<Pessoa> filtraPessoasAcimaDe25Anos(List<Pessoa> pessoas){
    List<Pessoa> pessoaList = new ArrayList<>();
    for(Pessoa pessoa : pessoas){
        if(pessoa.getIdade() > 25){
            pessoaList.add(pessoa);
        }
    }
    return pessoaList;
}
```


{: .fw-400 }
Olhando pra o código acima, notamos que foi necessário instanciar uma nova `List<Pessoa>`, realizar um laço de repetição sobre os elementos da lista da forma que estamos acostumados até o Java 7, e logo em seguida criar um `IF` para aplicar a condição e então adicionar somente as pessoas com idade acima de 25 anos na nova lista.
{: .lh-default}    
  Vamos resolver esse mesmo problema, mas dessa vez aplicando `STREAM` do java 8 :



```java
public List<Pessoa> filtraPessoasAcimaDe25Anos(List<Pessoa> pessoas){
    return pessoas.stream()
                  .filter(pessoa -> pessoa.getIdade() > 25)
                  .collect(Collectors.toList());
}
```   


{: .fw-400 }
Perceba que no código acima utilizamos `Stream API`, nela se concentram algumas operação uteis conhecidas como `Filter`, `Map`, `Reduce` e por ai vai …

{: .lh-default}    
Aqui utilizamos o `Filter`, esse método recebe como parametro um `Predicate` também do java 8 mas nesse caso aplicamos uma expressão `Lambda` dentro do filter, já aplicando a condição, e na sequencia chamamos o método `Collect`, também da Interface Stream, que irá retornar um `List<Pessoa>` já com o filtro aplicado, ou seja apenas as pessoas acima de 25 anos.
Dessa forma, fica muito mais fácil de lermos o método `filtraPessoaAcimaDe25Anos()` sem muito esforço.
