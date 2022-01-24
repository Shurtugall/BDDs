### Gherkin

Linguagem usada para definir as features e estruturar todos os cenários. Extremamente legível para ser facilmente compreendida por todos os integrantes da equipe.

Cada Feature deve ter um ou mais cenários. Cenários são divididos em 3 passos principais:

| Palavra chave   | Definição                                           |
|-----------------|-----------------------------------------------------|
|**Given** (Dado) | Indica o cenário inicial do teste                   |
|**When** (Quando)| Indica a ação a ser executada                       |
|**Then** (Então) | Indica o que deve ter acontecido ao final do cenário|

**Dica**: busque deixar as sentenças o mais simples possíveis. Dessa forma é possível reaproveitar as mesmas. Por exemplo:

   **Given** ~que está chovendo e estou sem guarda-chuvas~

   **Given** que está chovendo \                          
   **Given** que estou sem guarda chuvas                  

Dessa forma é possível usar ambos os casos no mesmo cenário, além de usá-los separadamente para outros cenários.

### Introdução

Arquivo **.feature** é o arquivo responsável por conter as "histórias" a serem mapeadas e resolvidas de acordo com os critérios de aceitação
