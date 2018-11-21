---
layout: default
title: "Primeiro Post"
date: "2018-11-20 22:55:32 -0200"
---


# Primeiro post teste

Em nosso dia-a-dia como desenvolvedores nos deparamos com alguns processos onde precisamos manipular listas
e fazer algumas condições em cima dessa lista , para filtrar e  retornar uma nova lista e por ai vai … Imagine o seguinte objeto :

```java
public class Pessoa {

        private String nome;
        private Integer idade;
        private String sexo;

        //getter and setter
    }
```

Imagine agora que dado uma lista do tipo pessoa, precisamos filtrar apenas as pessoas acima de 25 anos, então implementamos o seguinte método :    

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
Olhando pra o código acima, notamos que foi necessário instanciar uma nova lista do tipo Pessoa, realizar um laço de repetição sobre os elementos da lista da forma que estamos acostumados até o Java 7, e logo em seguida criar um if para aplicar a condição e então adicionar somente as pessoas com idade acima de 25 anos na nova lista.
    Vamos resolver esse mesmo problema, mas dessa vez aplicando stream do java 8 :

```java
public List<Pessoa> filtraPessoasAcimaDe25AnosTeste(List<Pessoa> pessoas){
    return pessoas.stream()
                  .filter(pessoa -> pessoa.getIdade() > 25)
                  .collect(Collectors.toList());
}
```   

Perceba que no código acima utilizamos Stream API, nela se concentram algumas operação uteis conhecidas como Filter, Map, Reduce e por ai vai … Nesse post vamos focar no Filter, que em nosso exemplo já resolve nosso problema, esse método da Interface Stream recebe como parametro um Predicate também do java 8 (Podemos falar sobre ele em outro post), mas nesse caso aplicamos a expressão lambda dentro do filter, já passando a condição que queremos aplicar, e então aplicamos o método collect, também da Interface Stream, que irá retornar um List<Pessoa> já com o filtro aplicado.
Dessa forma, fica muito mais fácil de lermos o método filtraPessoaAcimaDe25Anos( ) e entender o que realmente ele faz, sem muito esforço.
