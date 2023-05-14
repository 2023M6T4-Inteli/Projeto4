# Documento Principal do Projeto

Descrição sucinta do projeto, com descrição do problema, do objetivo e da solução em linhas gerais.

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

Preencher conforme a descrição do artefato na Adalove.

## (Sprint 2) Modelo de Bag of Words (IPYNB)

O Bag of Words é uma técnica de linguagem natural útil para criar um conjunto não ordenado de palavras. Dessa forma, o Bag of Words será importante para a análise de sentimentos porque, com ele, será possível vetorizar e comparar as similaridades ou diferenças com base na frequência de repetição de cada palavra:

O documento contendo a descrição técnica está disponível no seguinte link: https://github.com/2023M6T4-Inteli/Projeto4/blob/Dev/descri%C3%A7%C3%A3oT%C3%A9cnica.md

Colocar o link do artefato (deve estar na pasta src do repositório do projeto).

## (Sprint 2) Documentação do Modelo de Bag of Words

### Fluxograma de processamento (pipeline)

Para o modelo Bag Of Words funcionar são necessárias algumas etapas de pré processamento que são apresentadas na figura acima e serão descrevidas em mais detalhes logo abaixo.

- **Tokenização** : Nesta primeira etapa, o texto é primeiramente todo colocado em minúsculo independe da palavra e logo em seguida é feito um loop que itera por toda a frase e transforma cada palavra em um elemento da array.
 Assim, é mais fácil para o modelo enxergar cada palavra com um único elemento de uma array, facilitando iterações futuras.

```python
['eu','gosto','de','sorvete','de','pistache']
```

- **Remoção de Stop Words** : Durante essa fase do processo são removidas todas as palavras que não agregam valor ao texto, que é o caso de por exemplo "o", "a","eu" e etc.
 Fazendo isso, o modelo consegue entender melhor o significado de cada frase.

```python
['gosto','sorvete','pistache']
```

- **Vetorização bag of words** : A última etapa desse processamento, consiste em tornar o texto uma matrix e contar quantas vezes tal palavra aparece na array que havia sido removida as stop words previamente

```python
['gosto','sorvete','pistache']
[1,1,1]
```

### Limpeza de dados

**Introdução**

Visto que o escopo do projeto se trata da análise de dados dos comentários do Instagram @btgpactual, todos os dados que não tinham relação direta com esse objetivo foram excluídos, sendo eles: comentários (replys) feitos pela empresa, postagens feitas por terceiros que marcavam a empresa foram removidos.
Tal abordagem foi adotada, visto que o grupo entrou em consenso de que tais dados não poderiam agregar valor para a análise e desenvolvimento do modelo.

**Método**

Durante o processo de coleta de dados, foi notado que os comentários feitos pelo BTG Pactual não eram relevantes para o projeto. Além disso, algumas das publicações no feed mencionavam o BTG Pactual sem estar diretamente relacionadas ao objetivo da análise e,opr isso, foi decidido remover esses dados.

Para removê-los, foi utilizado um script que percorre todas as postagens e comentários coletados e remove aqueles que foram feitos pela conta oficial do BTG Pactual (@btgpactual). Da mesma forma, para remover as menções em publicações no feed, um script que identifica as publicações que mencionam o BTG Pactual e as exclui da base de dados.

Essa limpeza de dados foi importante para manter apenas as informações relevantes para a análise e obter resultados mais precisos. Todos os scripts utilizados para a limpeza de dados estão disponíveis na pasta correspondente no repositório do projeto.

Por fim, foi exportada uma nova base de dados (df_final.csv) com os dataframe limpo e pronto para aplicar outras técnicas de pré processamento.

**Resultado**

Com uma base de dados começando com 12355 linhas e 10 colunas, foram aplicados os parâmetros citados acima, assim o total de linhas pós aplicação da limpeza foram 6356 linhas.

**Conclusão**

Após esse processo de limpeza dos dados nota-se que muitos dados são perdidos, visto que o BTG Pactual responde uma grande quantia de pessoas em seus posts e muitas pessoas interagem com a companhia marcando-a mesma em uma vasta quantidade de publicações particulares, restando aproximadamente metade da base com dados relevantes ao objetivo do projeto.

### Pré-processamento

**Introdução**

O projeto lida com dados não-estrutrados (texto), portanto requer outras técnicas de pré-processamento que são amplamente utilizadas em processamento de linguagem natural.

**Método**

Foram utilizadas duas técnicas de pré-processamento em NLP no desenvolvimento do projeto para garantir a qualidade e a integridade dos dados.

A primeira técnica consistiu na transformação de todas as letras para minúsculas, o que ajudou a reduzir a complexidade dos dados e a garantir que as palavras fossem tratadas de forma consistente durante o processo de análise. Essa técnica foi especialmente útil para evitar que as mesmas palavras fossem contadas como diferentes devido a diferenças de capitalização.

A segunda técnica utilizada foi a remoção de stop words, que são palavras que não contribuem muito para o significado de uma frase, como 'de', 'e', 'ou', entre outras. Essa técnica ajudou a reduzir o ruído nos dados e a melhorar a precisão da análise, uma vez que se concentrou nas palavras mais relevantes para a compreensão dos comentários.

Além disso, foi utilizada a técnica de tokenização, que consiste na divisão de textos, no caso os comentários (coluna 'texto'), em palavras ou tokens. Essa técnica ajudou a separar os comentários em unidades menores, o que facilitou o processo de análise e permitiu a identificação de padrões e tendências nos dados.

**Resultado**

Após esse processo realizado em todos os dados do dataframe, foi adicionada uma coluna, 'Frases_sem_stop_words', constituída de listas das palavras tokenizadas e sem stop words e, por fim, exportou-se um novo dataframe com os dados tratados.

**Conclusão**

Ao utilizar essas técnicas de pré-processamento, foi possível garantir que os dados fossem tratados de forma consistente e que a análise fosse baseada em informações relevantes e precisas. Isso ajudou a melhorar a qualidade dos resultados obtidos e a tornar o projeto mais confiável e útil para o leitor.

Para a aplicação do Bag of Words, os dados passaram por tratamentos característicos do processamento de linguagem natural e adicionada uma coluna no dataframe, que será utilizada para a aplicação do BoW.

![1683822640735](image/README/1683822640735.png)

## (Sprint 3) Modelo utilizando Word2Vec (IPYNB)

Colocar o link do artefato (deve estar na pasta src do repositório do projeto).

## (Sprint 3) Documentação do Modelo utilizando Word2Vec

Preencher conforme a descrição do artefato na Adalove.

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
