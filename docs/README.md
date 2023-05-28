# Documento Principal do Projeto

O desafio do BTG Pactual é fazer uma análise de sentimentos nas suas postagens do Instagrama partir dos comentários, visando entender se a visão do público sobre determinadas campanhas de marketing é positiva, negativa ou neutra.
Assim, com o AdTrack, visamos classificar esses comentários em bons, neutros ou ruins, e extrair as palavras-chave destes, com base em um modelo de processamento de linguagem natural (NLP), de tal modo que seja possível tomar decisões a respeito das campanhas de marketing e acerca dos produtos e serviços do banco de forma mais assertiva.

## (Sprint 1) Entendimento do Negócio

### [**Matriz de Avaliação de Valor (Oceano Azul)**](https://docs.google.com/spreadsheets/d/1efPgxxEptiqPRB1AfTgmY_iF861oDFa0/edit?usp=sharing&ouid=102062215505800350720&rtpof=true&sd=true)

A matriz é utilizada para visualizar, a partir de demais players do mercado, possibilidades a serem exploradas e que podem criar vantagem competitiva. Dessa forma, foram analisados os seguintes aspectos: praticidade, métricas de análise de sentimento, métricas de análise de palavras chave, métricas comparativas com outras contas, custo, métricas comparativas com seus próprios posts, preço e dependência de fornecedor. Tais players foram analisados em comparação com o AdTrack: mLabs, Instagram Analytics e Iconsquare.

![1682733151293](image/README/1682733151293.png)

Matriz de Avaliação de Valor - Imagem 1

Portanto, é possível concluir tais aspectos:

1. Por ser um sistema utilizado internamente pela equipe da empresa, ele é de mais fácil acesso, se tornando mais prático e, por isso, **AUMENTOU** tal atributo. O Instagram Analytics, por ser interno do Instagram, também é prático, diferente de serviços terceiros que requer a criação de conta, pagamento, conexão com conta do Instagram e Facebook, como é o caso do mLabs e Iconosquare.
2. Diferente dos competidores, o AdTrack criou métricas de análise de sentimentos dos comentários feitos nas postagens, mostrando quais sentimentos cada campanha gerou no seguidores. Portanto, ao **CRIAR**, o AdTrack tem vantagem competitiva, gerando mais valor.
3. O AdTrack **CRIOU** tal atributo, visto que os demais serviços não fornecem a análise de palavras chaves extraídas dos comentários feitas nas públicações.
4. O AdTrack não possui métricas comparativas das campanhas de marketing com demais contas, sendo o Iconosquare a única que possui tal serviço, por isso o AdTrack **ELIMINOU** esse atributo, por não ter sido requisitado pelo cliente.
5. O Instagram Analytics é a própria ferramenta de análise do Instagram, portanto não possui custo. Já as plataformas Iconosquare e mLabs são serviços terceiros, que possuem mensalidade de 49 euros e 29,90 reais, respectivamente. O AdTrack, por ser um serviço interno, possui custos de manutenção e utilização, o que representa ser maior que os demais, assim sendo um aspecto que deve ser **REDUZIDO**.
6. A ferramenta nativa do Instagram possui métricas de comparativo de posts. O mLabs fornece as mesmas ferramentas do Instagram Analytics, portanto possuem mesma pontuação. O Iconosquare tem diferentes métricas mais detalhadas, sobre a quantidade de likes a cada 30 minutos, por exemplo. O AdTrack pode seguir algumas métricas da Iconosquare e oferecer, em tempo real, **AUMENTANDO**\-**AS**, mais detalhadas sobre a postagem que o próprio Instagram não oferece.
7. Visto que os serviços terceiros cobram preços mensais para o uso, o AdTrack **ELIMINOU** tal atributo, já que ele será nativo do sistema da empresa, não tendo que pagar um preço para uma outra empresa.
8. Para diminuir os custos e melhorar a eficiência do produto, o AdTrack pode **ELIMINAR** a dependência de fornecedor, ou seja, de base de dados do seu administrador, com a possibilidade de aumentar os dados e permitindo criar novas métricas comparativas.

A seguir é possível ver mais cada serviço que foi utilizado na matriz para comparar com a solução a ser desenvolvida. Foram criadas contas no mLabs e Iconosquare para realizar a pesquisa:

<img src="image/README/1682733615340.png" width="400"> <img src="image/README/1682733688613.png" width="400">

Relatórios do mLabs - Imagens 2 e 3

<img src="image/README/1682733858289.png" width="300"> <img src="image/README/1682733913802.png" width="400">

Relatórios do Iconosquare - Imagens 4 e 5

<img src="image/README/1682734727469.png" width="150"> <img src="image/README/1682734615095.png" width="150"> <img src="image/README/1682734138008.png" width="150">

Relatórios do Instagram Analytics - Imagens 6, 7 e 8

(Sprint 1) Entendimento da Experiência do Usuário

### **Personas**

### **1 Maria**

O Bag of Words é uma técnica de linguagem natural útil para criar um conjunto não ordenado de palavras. Dessa forma, o Bag of Words será importante para a análise de sentimentos porque, com ele, será possível vetorizar e comparar as similaridades ou diferenças com base na frequência de repetição de cada palavra:

O documento contendo a descrição técnica está disponível no seguinte link: https://github.com/2023M6T4-Inteli/Projeto4/blob/Dev/descri%C3%A7%C3%A3oT%C3%A9cnica.md

## (Sprint 2) Documentação do Modelo de Bag of Words

### Fluxograma de processamento (pipeline)

Para a aplicação da técnica Bag Of Words, são necessárias algumas etapas de pré processamento de dados não estruturados, apresentadas na figura abaixo e serão descritas em mais detalhes a seguir.
![1683822640735](image/README/1683822640735.png)

- **Tokenização** : Nesta primeira etapa, o texto é, primeiramente, todo colocado em minúsculo independente da palavra e, logo em seguida, é feito um loop que itera por toda a frase e transforma cada palavra em um elemento da array.
  Assim, é mais fácil para o modelo enxergar cada palavra com um único elemento de uma array, facilitando iterações futuras.

```python
['eu','gosto','de','sorvete','de','pistache']
```

- **Remoção de Stop Words** : Durante essa fase do processo são removidas todas as palavras que não agregam valor semântico ao texto, como por exemplo "o", "a","eu" e etc.
  Fazendo isso, o modelo consegue entender melhor o significado de cada frase para a posterior análise de sentimentos.

```python
['gosto','sorvete','pistache']
```

- **Vetorização bag of words** : A última etapa desse processamento, consiste em tornar o texto uma matrix de vetores e contar quantas vezes determinada palavra aparece no corpus.

```python
['gosto','sorvete','pistache']
[1,1,1]
```

As técnicas implementadas e descritas acima no pipeline estão descritas detalhadamente no seguinte documento: https://github.com/2023M6T4-Inteli/Projeto4/blob/Dev/descri%C3%A7%C3%A3oT%C3%A9cnica.md

## (Sprint 3) Modelo utilizando Word2Vec (IPYNB)

Colocar o link do artefato (deve estar na pasta src do repositório do projeto).

## (Sprint 3) Documentação do Modelo utilizando Word2Vec

O word2vec é um modelo de aprendizado de máquina utilizado para representar palavras como vetores em um espaço vetorial de muitas dimensões. Esse algoritmo foi inventado em 2013 por engenheiros do Google, assim é possível classificar cada palavra em um espaço vetorial finito e realizar operações matemáticas simples com n palavras e buscar graus de similaridades entre as mesmas. 

No presente projeto, o word2vec foi empregado de duas formas primeiro utilizando como base todas as palavras que foram utilizadas nos comentários buscando relações de similaridade entre as mesmas. Também foi utilizanda uma base vetorizada pré treinada fornecida pelo Núcleo Interinstitucional de Linguística Computacional (NILC) da Universidade de São Paulo (USP). 

Para treinar o modelo com o data set fornecido pelo BTG Pactual fui utilizada a biblioteca gensim para transformar as palavras em vetores. O modelo foi treinado utilizando as palavras contidas na base de dados disponível, e posteriormente aplicado às frases processadas. Durante esse processo, o modelo captura os vetores correspondentes a cada palavra presente na frase e os soma. Os primeiros 50 vetores resultantes são então armazenados em colunas específicas, o que proporciona uma representação compacta e numérica das frases, tornando-as adequadas para análises e tarefas de aprendizado de máquina.

Já para utilizar a vetorização pré treinada pelo NILC é necessário baixar o arquivo .txt que esta no site dos mesmos e carregar essa base no modelo. Para mais detalhes dessa etapa consulte o arquivo .ipynb na pasta "scr" e todo o passo a passo estara documentando. Assim, após o download da base do NILC é repetido o mesmo processo citado no parágrafo acima e são obtidas as 50 colunas que representam o vetor de cada frase. 

Essa abordagem baseada no word2vec e na biblioteca gensim possibilitou a obtenção de representações vetoriais para as palavras, as quais foram aplicadas às frases processadas. Ao realizar a soma dos vetores das palavras em cada frase, obtemos uma representação geral da mesma. Essa representação compacta é armazenada nas colunas criadas para esse propósito, permitindo uma análise mais eficiente e possibilitando a utilização dos primeiros 50 vetores resultantes em tarefas subsequentes. Com essa abordagem, é possível explorar as relações semânticas e contextuais entre as palavras, obtendo insights valiosos a partir das frases contidas em nosso banco de dados.

Por fim, ao serem feitas as respectivas análises de acurácia do modelo com o naive bayes, a mudança dos resultados obtidos com as duas vetorizações foram insignificantes. O modelo que utilizou o corpus obteve uma acurácia de 59% e o com a base pré treinada foi de 57%. Assim, futuros ajustes são necessários para obter uma melhor acurácia do modelo e permitir com que as classificações sejam mais acertivas.

## (Sprint 4) Proposta de uma nova modelagem utilizando novas features (IPYNB)

Colocar o link do artefato (deve estar na pasta src do repositório do projeto).

## (Sprint 4) Documentação da proposta de uma nova modelagem

Preencher conforme a descrição do artefato na Adalove.

## (Sprint 5) Apresentação Final

Colocar o link do artefato (deve estar na pasta apresentacoes do repositório do projeto).

## (Sprint 5) Deploy do melhor modelo

Colocar o link dos artefatos (devem estar nas pastas videos e src do repositório do projeto).

## (Sprint 5) Documentação da Solução

Preencher conforme a descrição do artefato na Adalove.
