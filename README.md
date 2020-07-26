### Caso de estudo JUnit 5, parte 1: teste de unidade com o JUnit 5, Mockito e Hamcrest

Configure seu primeiro projeto Maven e comece a escrever testes de unidade robustos com JUnit 5, Hamcrest e Mockito

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

![figura1](imag/figura1.png)

Referencia: https://www.infoworld.com/article/3537563/junit-5-tutorial-part-1-unit-testing-with-junit-5-mockito-and-hamcrest.html
