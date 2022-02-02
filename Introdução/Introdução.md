## Gherkin

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

### Fluidez na escrita

Em casos que existem muitas repetições de uma mesma palavra chave, por exemplo, sequências de *given*, é possível usar outras notações para gerar uma maior fluidez na leitura. Dessa forma podemos utilizar And* para afirmações e *But* para negações. Por exemplo:

   **Given** que está chovendo \
   **And** que está ventando                     
   **But** que estou sem guarda chuvas    

## Introdução

Existem dois tipos de arquivos a serem utilizados:

O arquivo **.feature** é o arquivo responsável por conter as funcionalidades a serem mapeadas e resolvidas de acordo com os critérios de aceitação. Dado como a fonte única de verdade, esse arquivo pode ser utilizado não apenas pelos QAs, mas pelos DEVs e até mesmo pelo Cliente, visto que contém fluxos do sistema.

Um *Scenario* descreve um dos comportamentos desejados do sistema através de um exemplo concreto. Dentro do *Scenario* iremos definir os passos de Give, When e Then. Esses podem estar em 5 estados diferentes. Que são eles:

| Estado    | Descrição                                                                         |  
|-----------|-----------------------------------------------------------------------------------|
| Undefined |Não foi gerado, é necessário implementar                                           |
|  Pending  |Está pendente, foi criado mas entrou em uma excessão pendende *PendingException()* |
|  Failed   |Falhou, lançou uma excessão diferente da excessão de pendente. *RuntimeException()*|
|  Skiped   |Parou a execução em um passo anterior, logo pulou a execução dos passos skiped     |
|  Passed   |Estado que define que o passo obteve sucesso. Ou seja, sem erros na execução       |

O arquivo **.java** vai conter todas as implementações dos *scenarios*. Ou seja, o arquivo de features tende a conter apenas os fluxos, semelhante a um arquivo de header de algumas linguagens como *C*, enquanto que o arquivo java vai ser responsável por dizer o que deve ser feito em cada passo.

Exemplos:

.feature

    Feature: Aprendizado de Cucumber
    Scenario: Executar uma especificacao
	      Given o arquivo foi criado corretamente
	      When  for feito a execucao
	      Then  a especificacao deve obter sucesso

.java
    
    public class AprenderCucumber {
	    @Given("o arquivo foi criado corretamente")
	    public void que_criei_o_arquivo_corretamente() {
	      System.out.println("Passou essa etapa");
	    }

	    @When("for feito a execucao")
	    public void executa_lo() {
        throw new RuntimeException();
	    }

	    @Then("a especificacao deve obter sucesso")
	    public void a_especificacao_deve_finalizar_com_sucesso() {
	      throw new PendingException();
	    }
    }

### Cucumber expressions

Nas versões mais recentes do Cucumber, as *regular expressions* deixaram de ser aceitas, de forma que foram substituídas pelas Cucumber expressions. Dessa forma no link: [Cucumber Expressions](https://github.com/cucumber/cucumber-expressions#readme) é possível verificar a sintaxe a ser utilizada para que os codigos sejam aceitos.


### Tags

Tags são usadas para selecionar pontos específicos a serem executados. Por exemplo, dado uma feature com vários cenários, decidimos executar apenas um em específico. Dessa forma basta adicionar uma tag acima da definição do cenário (p.ex., @this) e informar na classe Runner qual a tag que será utilizada. Pode ser utilizada a nível de cenários ou features. Exemplo abaixo:

.feature

	@this
	Scenario: Deve calcular atraso na entrega
		Given que a entrega é dia 05/04/2018
		When a entrega atrasar em 2 "dias"
		Then a entrega sera efetuada em 07/04/2018	

Runner.java
	
	@RunWith(Cucumber.class)
	@CucumberOptions(
		tags="@this"
	)
	public class Runner {}

Para executar mais de uma tag, basta colocar entre chaves: *tags={"@tipo1, @tipo2"}*

**Observação**: tags podem ser usadas tanto para selecionar qual parte deve ser usada, bem como dizer qual parte não deve ser executada, dessa forma basta usar a tag *@ignore* e negar a mesma no runner, por exemplo:

.feature

	@ignore
	Scenario: Deve calcular atraso na entrega
		Given que a entrega é dia 05/04/2018
		When a entrega atrasar em 2 "dias"
		Then a entrega sera efetuada em 07/04/2018	

Runner.java
	
	@RunWith(Cucumber.class)
	@CucumberOptions(
		tags="not @ignore"
	)
	public class Runner {}
