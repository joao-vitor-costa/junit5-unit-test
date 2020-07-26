## Caso de estudo para JUnit 5: teste de unidade com o JUnit 5, Mockito e Hamcrest

O JUnit 5 é o novo padrão de fato para o desenvolvimento de testes de unidade em Java. Esta versão mais recente deixou para trás as restrições do Java 5 e integrou muitos recursos do Java 8, principalmente o suporte a expressões lambda .

Nesta primeira metade de uma introdução em duas partes do JUnit 5, você começará a testar o JUnit 5. Mostrarei como configurar um projeto Maven para usar o JUnit 5, como escrever testes usando as anotações @Teste @ParameterizedTest, e como trabalhar com as novas anotações do ciclo de vida no JUnit 5. Você também verá um breve exemplo do uso de tags de filtro e mostrarei como integrar o JUnit 5 a uma biblioteca de asserções de terceiros - nesse caso, Hamcrest . Por fim, você obterá uma introdução rápida e tutorial à integração do JUnit 5 com o Mockito, para que você possa escrever testes de unidade mais robustos para sistemas complexos do mundo real.

Desenvolvimento orientado a teste
Se você desenvolve código Java há algum tempo, provavelmente está familiarizado com o desenvolvimento orientado a testes, por isso vou manter esta seção breve. É importante entender por que escrevemos testes de unidade, no entanto, bem como as estratégias que os desenvolvedores empregam ao projetar testes de unidade.

O Test-driven development (TDD) é um processo de desenvolvimento de software que entrelaça a codificação, teste e design. É uma abordagem test-first que visa melhorar a qualidade de seus aplicativos. O desenvolvimento orientado a teste é definido pelo seguinte ciclo de vida:

1. Adicione um teste.
2. Execute todos os seus testes e observe a falha do novo teste.
3. Implemente o código.
4. Execute todos os seus testes e observe o novo teste com êxito.
5. Refatorar o código.

![figura1](https://github.com/joao-vitor-costa/junit5-unit-test/blob/master/img/figura1.png)

Há um duplo objetivo de escrever testes antes de escrever seu código. Primeiro, obriga a pensar no problema de negócios que você está tentando resolver. Por exemplo, como os cenários de sucesso devem se comportar? Quais condições devem falhar? Como eles deveriam falhar? Segundo, o teste primeiro oferece mais confiança nos testes. Sempre que escrevo testes depois de escrever código, sempre tenho que quebrá-los para garantir que eles estejam realmente capturando erros. Os testes de escrita primeiro evitam essa etapa extra.

Escrever testes para o caminho feliz geralmente é fácil: dada a boa entrada, a classe deve retornar uma resposta determinística. Mas escrever casos de teste negativos (ou com falha), especialmente para componentes complexos, pode ser mais complicado.

Como exemplo, considere escrever testes para um repositório de banco de dados. No caminho feliz, inserimos um registro no banco de dados e recebemos de volta o objeto criado, incluindo todas as chaves geradas. Na realidade, também devemos considerar a possibilidade de um conflito, como inserir um registro com um valor de coluna exclusivo que já é mantido por outro registro. Além disso, o que acontece quando o repositório não pode se conectar ao banco de dados, talvez porque o nome de usuário ou a senha foram alterados? O que acontece se houver um erro de rede em trânsito? O que acontece se a solicitação não for concluída no limite de tempo limite definido?

Para criar um componente robusto, você precisa considerar todos os cenários prováveis e improváveis, desenvolver testes para eles e escrever seu código para satisfazer esses testes. Mais adiante neste artigo, veremos estratégias para criar diferentes cenários de falha, juntamente com alguns dos novos recursos do JUnit 5 que podem ajudá-lo a testar esses cenários.

![figura2](https://github.com/joao-vitor-costa/junit5-unit-test/blob/master/img/figura2.png)

### JUnit 5
A classe Assertions e seus métodos
A  org.junit.jupiter.api.Testanotação indica um método de teste. Observe que a @Testanotação agora vem do pacote da API JUnit 5 Jupiter em vez do pacote da JUnit 4 org.junit. O testConvertToDecimalSuccessmétodo primeiro executa o MathTools::convertToDecimalmétodo com um numerador de 3 e um denominador de 4 e, em seguida, afirma que o resultado é igual a 0,75. A org.junit.jupiter.api.Assertionsclasse fornece um conjunto de staticmétodos para comparar resultados reais e esperados. A Assertionsclasse possui os seguintes métodos, que abrangem a maioria dos tipos de dados primitivos:

- assertArrayEquals compara o conteúdo de uma matriz real com uma matriz esperada.
- assertEquals compara um valor real a um valor esperado.
- assertNotEquals compara dois valores para validar que eles não são iguais.
- assertTrue valida que o valor fornecido é verdadeiro.
- assertFalse valida que o valor fornecido é falso.
- assertLinesMatchcompara duas listas de Strings.
- assertNull valida que o valor fornecido é nulo.
- assertNotNull valida que o valor fornecido não é nulo.
- assertSame valida que dois valores referenciam o mesmo objeto.
- assertNotSame valida que dois valores não fazem referência ao mesmo objeto.
- assertThrowsvalida que a execução de um método lança uma exceção esperada (você pode ver isso no testConvertToDecimalInvalidDenominatorexemplo acima).
- assertTimeout valida que uma função fornecida seja concluída dentro de um tempo limite especificado.
- assertTimeoutPreemptively valida que uma função fornecida é concluída dentro de um tempo limite especificado, mas uma vez atingido o tempo limite, ele mata a execução da função.
-
Se algum desses métodos de asserção falhar, o teste de unidade será marcado como reprovado. Esse aviso de falha será gravado na tela quando você executar o teste e, em seguida, salvo em um arquivo de relatório.


Referencia: https://www.infoworld.com/article/3537563/junit-5-tutorial-part-1-unit-testing-with-junit-5-mockito-and-hamcrest.html
