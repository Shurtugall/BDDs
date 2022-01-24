## Configurando o ambiente

Inicialmente é necessário ter instalado o [Java jdk](https://www.oracle.com/java/technologies/downloads/) (de preferência a última versão disponibilizada).

Em seguida é necessário ter uma IDE para poder executar os códigos, atualmente utilizo [Eclipse](https://www.eclipse.org/downloads/) (a IDE para java developers já é suficiente), mas outras opções são válidas, como IntelliJ e NetBeans.

Após instalar o eclipse, vá em: aba **Help -> Eclipse Marketplace**. Procure por "Cucumber" na caixa de busca e faça a instalação do **Eclipse Cucumber Plugin**

Assim que o plugin for instalado, basta criar um Maven Project. Verifique qual o jdk do projeto, se não for aquele que você baixou, clique com o botão direito no projeto e vá em: Properties -> Java Build Path -> Libraries, remova o JRE System Library, clique no botão add Library e adicione o jdk baixado.

O próximo passo é baixar as dependencias do Cucumber. Para tal acesse o site do [Maven Repository](https://mvnrepository.com/search?q=cucumber) procure por cucumber e abra o [Cucumber JVM: Java](https://mvnrepository.com/artifact/io.cucumber/cucumber-java). Basta copiar a dependencia do Maven da última versão disponibilizada

No projeto, procure pelo arquivo **pom.xml**, acrescente uma div de "<dependences>" e copie essa dependencia dentro da div. Feito isso o projeto está configurado.
