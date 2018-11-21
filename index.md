<!-- ---
layout: default
title: Home
nav_order: 1
permalink: /
---


# Focus on writing good documentation
{: .fs-9 }

Just the Docs gives your documentation a jumpstart with a responsive Jekyll theme that is easily customizable and hosted on GitHub pages.
{: .fs-6 .fw-300 }

[Get started now](#getting-started){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [View it on GitHub](https://github.com/pmarsceill/just-the-docs){: .btn .fs-5 }

---

## Getting started
### Dependencies
Just the Docs is built for [Jekyll](https://jekyllrb.com), a static site generator. View the [quick start guide](https://jekyllrb.com/docs/quickstart/) for more information. Just the Docs requires no special Jekyll plugins and can run on GitHub Pages standard Jekyll compiler.

### Quick start: Use as a GitHub Pages remote theme
1. Add Just the Docs to your Jekyll site's `_config.yml` as a [remote theme](https://blog.github.com/2017-11-29-use-any-theme-with-github-pages/)
```yaml
remote_theme: pmarsceill/just-the-docs
```
<small>You must have GitHub pages enabled on your repo, one or more markdown files, and a `_config.yml` file. [See an example repository](https://github.com/pmarsceill/jtd-remote)</small>

### Local installation: Use the gem-based theme
1. Install the Ruby Gem
```bash
$ gem install just-the-docs
```
```yaml
# .. or add it to your your Jekyll site’s Gemfile
gem "just-the-docs"
```
2. Add Just the Docs to your Jekyll site’s `_config.yml`
```yaml
theme: "just-the-docs"
```
3. _Optional:_ Initialize search data (creates `search-data.json`)
```bash
$ bundle exec just-the-docs rake search:init
```
3. Run you local Jekyll server
```bash
$ jekyll serve
```
```bash
# .. or if you're using a Gemfile (bundler)
$ bundle exec jekyll serve
```
4. Point your web browser to [http://localhost:4000](http://localhost:4000)

### Configure Just the Docs
- [See configuration options]({{ site.baseurl }}{% link docs/configuration.md %})


---

## About the project

Just the Docs is &copy; 2017 by [Patrick Marsceill](http://patrickmarsceill.com).

### License

Just the Docs is distributed by an [MIT license](https://github.com/pmarsceill/just-the-docs/tree/master/LICENSE.txt).

### Contributing

When contributing to this repository, please first discuss the change you wish to make via issue,
email, or any other method with the owners of this repository before making a change. Read more about becoming a contributor in [our GitHub repo](https://github.com/pmarsceill/just-the-docs#contributing).


### Code of Conduct

Just the Docs is committed to fostering a welcoming community.

[View our Code of Conduct](https://github.com/pmarsceill/just-the-docs/tree/master/CODE_OF_CONDUCT.md) on our GitHub repository. -->


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
