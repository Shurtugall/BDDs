## Configurando o ambiente

Inicialmente é necessário ter instalado o [Java jdk](https://www.oracle.com/java/technologies/downloads/) (de preferência a última versão disponibilizada).

Em seguida é necessário ter uma IDE para poder executar os códigos, atualmente utilizo [Eclipse](https://www.eclipse.org/downloads/) (a IDE para java developers já é suficiente), mas outras opções são válidas, como IntelliJ e NetBeans.

Após instalar o eclipse, vá em: aba **Help -> Eclipse Marketplace**. Procure por "Cucumber" na caixa de busca e faça a instalação do **Eclipse Cucumber Plugin**

Assim que o plugin for instalado, basta criar um Maven Project. Verifique qual o jdk do projeto, se não for aquele que você baixou, clique com o botão direito no projeto e vá em: Properties -> Java Build Path -> Libraries, remova o JRE System Library, clique no botão add Library e adicione o jdk baixado.

O próximo passo é baixar as dependencias do Cucumber. Para tal acesse o site do [Maven Repository](https://mvnrepository.com/search?q=cucumber) procure por cucumber e abra o [Cucumber JVM: Java](https://mvnrepository.com/artifact/io.cucumber/cucumber-java). Basta copiar a dependencia do Maven da última versão disponibilizada

No projeto, procure pelo arquivo **pom.xml**, acrescente uma div de "<dependences>" e copie essa dependencia dentro da div. Feito isso o projeto está configurado.


### Junit

O Junit é um framework com suporte a testes automatizados.

Para fazer a instalação do mesmo, basta ir novamente no site do [Maven Repository](https://mvnrepository.com/search?q=cucumber) procurando por cucumber e procurar pela última versão disponível do [Cucumber JVM: Junit](https://mvnrepository.com/artifact/io.cucumber/cucumber-junit)

Assim, basta copiar a dependencia para o arquivo **pom.xml** conforme foi feito nos passos anteriores.

Dessa forma, sempre que for executado um teste, podemos utilizar um runner do Junit, basta criar um arquivo no mesmo nível do arquivo java. É posível nomeá-lo como Runner.java. Dentro do arquivo basta conter a condição de *RunWith* e como forma opcional os *CucumberOptions*:

      @RunWith(Cucumber.class)
      @CucumberOptions(plugin = "pretty", monochrome = true, snippets = SnippetType.CAMELCASE)
      public class Runner {
      }
