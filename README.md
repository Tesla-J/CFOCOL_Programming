# CFOCOL_Programming
O CFOCOL é uma esolang denominada Chemical Formula of Coffe-oriented Language ou Linguagem orientada a fórmula química de café. Possui apenas 6 instruções em formato de fórmulas químicas do café e pode ser usada para "testar limites de aplicação" como na maioria das linguagens "Turing Tarpit". O CFOCOL, além de programação imperativa, cria outros conceitos de "Linguagem orientada a argumentos", onde as possíveis funcionalidades de 1 instrução pode ser descrita como argumentos numéricos. Neste repositório está armazenada Pasta de exemplos de algoritmos Cfocol, o interpretador da linguagem, arquivos de configurações e o código fonte do interpretador. Abaixo são descritos algumas funcionalidades e instruções da linguagem:

 <a name="menu"></a>
  * <a href="#inst"> Instruções da linguagem </a>
  * <a href="#proc"> Procedimentos & Sinais </a>
  * <a href="#func"> Funcionalidades do CFOCOL </a>
      *  <a href="#op"> Operações aritméticas </a>
      *  <a href="#sel"> Seleção/Deslocamento de memória </a>
      *  <a href="#impr"> Impressão de dados </a>
      *  <a href="#salt"> Saltos Condicionais/Incondicionais </a>
      *  <a href="#call"> Chamadas Condicionais/Incondicionais </a>
      *  <a href="#inp"> Entrada de dados & Bottles Secundários  </a>
      *  <a href="#com"> Comentários em CFOCOL  </a>
      *  <a href="#prog"> Programas em CFOCOL  </a>
  * <a href="#mode"> Modos de Interpretação </a>
      *  <a href="#command1"> Via linha de comando  </a>
      *  <a href="#command2"> Via linha de comando global (Variáveis de Ambiente) </a>
      *  <a href="#click"> Clique Duplo </a>
      *  <a href="#linux">Executando em distros Linux</a>
  * <a href="#colors"> Cores sintáticas no Editor </a>
  
<a name="inst"></a> 
## Instruções da linguagem
  
  Existem 6 fórmulas químicas, cada uma pra um comando/instrução. Dessas 6 fórmulas: 2 são alcalóides, 2 são ácidos orgânicos, 1 é um diterpeno e 1 é um sacarose (açúcar), todos eles são umas das composições do café, veja abaixo:
  
 **Alcalóides ->**
 
    1. C8H10N4O2 -> Saída de dados (Impressão) - cafeína
    2. C7H8N4O2  -> Operações aritméticas      - teobromina
    
**Ácidos orgânicos ->**

    1. C9H8O4 -> Seleção de memória (Deslocamento) - ácido cafeico
    2. C7H6O3 -> Retorno de chamada                - ácido hidroxibenzoico 
    
 **Diterpeno e Sacarose ->**
 
    1. C20H28O3  -> salto/chamada condicional ou incondicional - cafestol
    2. C12H22O11 -> Entrada de dados                           - sacarose (açúcar)
 
 <a href="#menu">Voltar ao menu</a>
 <a name="proc"></a> 
## Procedimentos e sinais

Os Bottles (Garrafas) são os procedimentos/rotinas do CFOCOL, o Bottle (função) principal é obrigatoriamente o "cup", seguido por 2 pontos ':', assim como o Main de uma linguagem de programação de alto-nível. Todo Bottle deve abrir com ':' e finalizar com ';', dentro de cada Bottle terá instruções referenciadas pelos seus **identificadores** que são números hexadecimais para identificar uma determinada instrução. Também existem os **Bottles Secundários** que tem um sinal de referência '@' no começo, os nomes de Bottles poderão ser utilizados para ser chamados por instruções de saltos por outro Bottle, especificando também o identificador específico que se quer executar, veja abaixo as definições de sinais da linguagem e Bottles:

**Bottles(Procedimentos/rotinas):**
   1. Bottle principal - cup -> main.
   2. Bottles secundários - outros com @ (Ex.: @Bottle1).
 
**Identificadores:**
   1. 0000 a FFFF cada Bottle (Seguido por :)

**Sinais(sem aspas):**
   1.  ';'  -> finalização de Bottles
   2.  '!'  -> Finalização de instruções
   3.  '%'  -> quebra de linha em exibição
   4.  ','  -> concatenação de posições de memória
   5.  '@'  -> identificador de bottles secundários
   6.  '_'  -> acesso de identificadores por Bottles
   7.  ':'  -> atribuição de instruções em identificadores e Bottles
   8.  '$'  -> valor da posição atual de memória
   9.  '#'  -> valor da última posição deslocada
   10. '<>' -> exibição de inteiros das posições
  
  <a href="#menu">Voltar ao menu</a>
   <a name="func"></a> 
   ## Funcionalidades do CFOCOL
   <a name="op"></a> 
 ### Operações Aritméticas
 
   Em CFOCOL, além das instruções, é preciso conhecer os **argumentos**, já que a maior parte das funcionalidades de cada instrução são programadas pelos argumentos. Na linguagem CFOCOL, argumentos são números separados por vírgula que cada instrução pode utilizar, são esses números que define a funcionalidade daquela instrução, um exemplo é a teobromina _C7H8N4O2_, que é uma instrução de operações aritméticas, ela contém o 1ª argumento reservado para o tipo de operação, veja os tipos possíveis:
   
   Nª 0 - Adição <br>
   Nª 1 - Subtração <br>
   Nª 2 - Multiplicação <br>
   Nª 3 - Divisão <br>
   
   **Exemplos:**
   
      C7H8N4O2 0,2,1!  -> isto soma 2 + 1 e armazena o resultado em memória
      C7H8N4O2 1,2,1!  -> isto subtrai 2 - 1 e armazena o resultado em memória
      C7H8N4O2 2,2,1!  -> isto multiplica 2 * 1 e armazena o resultado em memória
      C7H8N4O2 3,2,1!  -> isto divide 2 / 1 e armazena o resultado em memória
      
 O mínimo de quantidade de argumentos em algumas instruções são 3, no entanto, em algumas instruções, como o de **deslocamento de memória**, o mínimo é apenas 2. Porém, pode ser utilizado mais de 3 argumentos para as operações aritméticas, Exemplos:
      
      C7H8N4O2 0,2,1,3,4! -> O resultado da soma em memória será 10
      C7H8N4O2 2,2,2,4,2! -> O resultado da multiplicação em memória será 32
      
 Então, já deu pra perceber que do 2ª argumento para frente é relacionado aos números que serão operados, o tipo de operação é determinada pelo 1ª argumento, assim como as fórmulas químicas tradicionais que conhecemos que tem suas representações numéricas separadas por vírgulas.
 No lugar de números, os argumentos também podem ser **Endereços**, que são chamadas de **Posições**. Existem 2 possíveis posições que podem ser acessadas simultaneamente: '$' e '#' (sem aspas). 
 
 O símbolo de dólar '$' representa a **posição atual** selecionada pela instrução _C9H8O4_, que é um ácido cafeico para seleção e deslocamento de memória, enquanto que o símbolo de tralha '#' representa a **última posição** selecionada antes da posição atual e este símbolo se dar o nome de **último deslocamento**.
 No entanto, quando o programa começa, a 1ª posição selecionada por padrão é 0, logo, todo o programa pode-se basear apenas nesta posição, descartando o símbolo de último deslocamento. Quando uma operação aritmética é feita, mesmo que nenhuma posição é selecionada, o resultado desta operação é armazenada na posição 0 de memória, porém se uma nova posição for deslocada, a próxima operação armazenará o resultado nesta nova posição, e aí, o valor armazenado da posição anterior é recuperada pelo símbolo '#' e o valor da posição atual é recuperado pelo símbolo '$', veja 2 exemplos:
 
 **Exemplo 1:**
    
        C7H8N4O2 0,$,1! -> Considerando que o valor da posição de memória 0 é 0, logo, 0 + 1 = 1
        C7H8N4O2 0,$,3! -> Considerando que o valor da posição de memória 0 é 1, logo, 1 + 3 = 4
        C7H8N4O2 2,$,2! -> Considerando que o valor da posição de memória 0 é 4, logo, 4 * 2 = 16
        
        O valor final da posição 0 é 16.
  
  **Exemplo 2(seguindo o exemplo anterior):**
        
        C9H8O4 0,1!     -> 0 é operação de soma para deslocamento, logo, desloca +1 posição na memória
        C7H8N4O2 0,$,2! -> Considerando que o valor da posição de memória 1 é 0, logo, 0 + 2 = 2 
        C9H8O4 1,1!     -> 1 é operação de subtração para deslocamento, logo, desloca -1 posição na memória
        C7H8N4O2 1,$,1! -> Considerando que o valor da posição de memória 0 é 16, logo, 16 - 1 = 15
        C7H8N4O2 0,$,#! -> Considerando que $ é 15 e # (último deslocamento) é 2, logo, 15 + 2 = 17
        
        O valor final da posição atual (0) é 17 -> recuperado por $
        O valor final da posição anterior (1) é 2 -> recuperado por #  
  
  <a href="#menu">Voltar ao menu</a>
  <a name="sel"></a>     
  ### Seleção/Deslocamento de memória
  
  O Ácido orgânico _C9H8O4_ é uma instrução para deslocamento de memória. Antes dela ser utilizada, a posição atual da memória é 0, porém, após ser utilizada, a posição pode assumir qualquer valor, exemplo: O 1ª argumento desta instrução pode ser 0 ou 1, 0 para soma de deslocamento e 1 para subtração de deslocamento; O 2ª argumento está relacionado ao número de operação para deslocamento, se for 1, deslocará 1 posição na memória, se for 2, 2 posições na memória, se for 5, vai deslocar 5 posições na memória, etc... o deslocamento irá pra frente se o 1ª argumento for 0 e o deslocamento irá pra trás se o 1ª argumento for 1. No entanto, só é possível utilizar o máximo de 2 argumentos nesta instrução, diferente de outras instruções que utiliza de 3 argumentos pra mais. No momento que a instrução de deslocamento é utilizada, a devida posição é selecionada, permitindo que operações aritméticas agem em cima destas posições, incluindo saltos condicionais/incondicionais. 
  
  Já que em CFOCOL não existem variáveis, a intenção é testar até onde será o limite das aplicações utilizando apenas 2 endereços simultaneamente por vez, então vamos dar um exemplo de várias seleções de memória:
  
       C9H8O4 0,5!  -> $ referencía o valor da posição 5
       C9H8O4 1,4!  -> $ referencía o valor da posição 1 (5-4=1) e # referencía o valor da posição 5
       C9H8O4 0,3!  -> $ referencía o valor da posição 4 (1+3=4) e # referencía o valor da posição 1
       C9H8O4 1,4!  -> $ referencía o valor da posição 0 (4-4=0) e # referencía o valor da posição 4
        
  
   Considerando este exemplo, '$' sempre vai referenciar a posição cujo resultado da posição é igual a posição anterior calculada com o número de posição atual (exceto na 1ª vez que o deslocamento é acionado), enquanto que '#' vai referenciar a mesma posição que '$' assumía anteriormente. Mas vamos considerar que queremos fazer uma operação e utilizar o resultado como um deslocamento, isso é possível, veja nos seguintes exemplos:
   
        C9H8O4 0,5!     -> $ referencía o valor da posição 5
        C7H8N4O2 0,$,2! -> soma o valor da posição 5 (0) + 2 e $ referencía o valor 2
        C9H8O4 0,$!     -> $ referencía o valor da posição 7, pois 5 + 2 = 7
        C9H8O4 1,#!     -> $ referencía o valor da posição 5, pois 7 - 2 = 5 (# = 2)
        C7H8N4O2 0,$,3! -> soma o valor da posição 5 (2) + 3 e $ referencía o valor 5
        C9H8O4 1,$!     -> $ referencía o valor da posição 0, pois 5 - 5 = 0
        
        Resultado final: $ = 0 (valor e posição)
                         # = 5 (valor e posição)
   
   <a href="#menu">Voltar ao menu</a>
   <a name="impr"></a>                     
   ### Impressão de dados                      
       
  Após compreendermos sobre as operações aritméticas e seleções de memória, vamos entender como funciona a cafeína, que é a instrução para **Impressão de caracteres**. Existem 3 maneiras para imprimir caracteres:
  
        1ª - Utilizar strings estáticas
        2ª - Utilizar posições de memória
        3ª - Utilizar strings estáticas + posições de memória
    
A 1ª opção é feito de um modo muito simples utilizando o alcalóide de cafeína _C8H10N4O2_ para imprimir caracteres:

        C8H10N4O2 Hello World!  -> Isto exibe um Hello World na tela
        
As strings não necessitam ser colocadas em aspas duplas como na maioria das linguagens de alto-nível, também pode-se adicionar uma ou mais quebras de linhas através do símbolo '%':

        C8H10N4O2 Hello World%%!  -> Isto exibe um Hello World na tela com 2 quebras de linhas após a exibição
        
Se quiser exibir caracteres na mesma linha só que com um espaço entre eles, só adicionar um espaço:

        C8H10N4O2 1 !  -> Exibe o 1 com espaço
        C8H10N4O2 2 !  -> Exibe o 2 com espaço
        C8H10N4O2 3 !  -> Exibe o 3 com espaço
        
      Resultado: 1 2 3 
      
  Agora, a 2ª opção é um pouco mais complicado, porém ainda é simples. Pra exibir valores de posições de memória, é preciso conhecer os símbolos $, #, ',,' e <>, como os 2 primeiros símbolos já conhecemos, então vamos para os 2 últimos. Considerando que aconteceu uma operação aritmética onde foi armazenado o valor 65 na posição atual e quero exibir o decimal 65 na tela, eu preciso usar o símbolo de posição atual $ entre os símbolos <>, porém entre vírgulas, veja o exemplo:
  
         C7H8N4O2 0,$,65!  -> soma 0 + 65 = 65 e armazena o resultado na posição 0
         C8H10N4O2 ,<$>,!  -> Exibe o decimal 65
         
 Considerando que eu quero exibir uma letra, um caractere... Então eu descarto os símbolos <> e utilizo apenas o $ e as vírgulas:
 
         C7H8N4O2 0,$,65!  -> soma 0 + 65 = 65 e armazena o resultado na posição 0
         C8H10N4O2 ,$,!    -> Exibe o caractere 'A' (em maiúsculo), A = 65 em decimal
         
  Pra exibir o caractere 'a' minúsculo é preciso utilizar o decimal 97:
  
         C7H8N4O2 0,$,97!  -> soma 0 + 97 = 97 e armazena o resultado na posição 0
         C8H10N4O2 ,$,!    -> Exibe o caractere 'a' (em minúsculo), a = 97 em decimal
      
  Já deu pra perceber que pra exibir caracteres da memória é preciso conhecer a tabela ASCII, especialmente, valores decimais. Os símbolos $ entre <> se trata de impressões de inteiros da memória enquanto que o símbolo $ sem <> se trata de impressões de símbolos de caracteres da tabela ASCII em decimal, mas e as vírgulas? Então, as vírgulas servem para **delimitar** endereços com strings, ou seja, ora utilizando strings na exibição será concatenações, ora NÃO utilizando strings será apenas uma delimitação, pois isso evita de ocorrer erros caso houver um espaço antes do $ ou depois do $, isto porque "espaços" são strings.
  
  Agora vai um exemplo de concatenação de strings com as posições atuais:
  
          C7H8N4O2 0,$,97!                     -> soma 0 + 97 = 97 e armazena o resultado na posição 0
          C8H10N4O2 Exibindo a letra ',$,'!    -> Exibe o caractere a com aspas simples
          C8H10N4O2 Exibindo a letra ,$,!      -> Exibe o caractere a sem aspas simples
          
          Resultado:
              Exibindo a letra 'a'
              Exibindo a letra a
             
   É possível **duplicar** a exibição, repetindo o símbolo de posição atual (seguindo o exemplo anterior):
   
           C8H10N4O2 Exibindo a letra ,$$$,!  -> Exibe a string "Exibindo a letra aaa"
   
   O único problema que, entre as vírgulas, não é possível adicionar espaços, logo só é possível se houver outra concatenação, exemplo:
   
           C8H10N4O2 Exibindo a letra: ,$, ,$, ,$,!  -> Exibe a string "Exibindo a letra: a a a"
           
   Não é só com a posição atual que é possível exibir números/letras, o símbolo # de _último deslocamento_ pode ser utilizado pra ser exibido, contanto que tenha havido algum deslocamento antes desta exibição, exemplo:
   
           C7H8N4O2 0,$,97! -> Atribui ao primeiro endereço o valor 97 ('a' em decimal)
           C9H8O4 0,1!      -> 1ª deslocamento para a direita (somando +1)
           C7H8N4O2 0,$,98! -> Atribui ao segundo endereço o valor 98 ('b' em decimal)
           C9H8O4 1,1!      -> 2ª deslocamento para a esquerda (subtraindo -1)
           C8H10N4O2 1ª Valor: ,$, % 2ª Valor: ,#, %!      -> Exibe strings com os caracteres de $ e #
           C8H10N4O2 1ª Valor: ,<$>, % 2ª Valor: ,<#>, %!  -> Exibe strings com os decimais de $ e #
           
         Resultado:
              1ª Valor: a
              2ª Valor: b
              1ª Valor: 97
              2ª Valor: 98
   
   <a href="#menu">Voltar ao menu</a>
   <a name="salt"></a>           
  ### Saltos Condicionais/Incondicionais
  
  Veremos agora sobre um dos tipos de diterpenos chamado **_Cafestol_** e o **_ácido hidroxibenzóico_** que faz parte dos **_ácidos orgânicos_** (da mesma família que o ácido cafeico), ambos são utilizados no café e vai nos dar muita energia cerebral ao programar esses elementos... Pois bem, o cafestol _C20H28O3_ é uma instrução para saltos condicionais/incondicionais e chamadas condicionais/incondicionais. A instrução de salto condicional faz a condição e se for verdadeira, ela salta para um endereço chamado **identificador** (termos do CFOCOL), a mesma coisa é a chamada condicional, na qual é a mesma instrução cafestol, a diferença é que na chamada ela salta se for verdadeiro, executa a instrução e quando identifica o ácido hidroxibenzóico _C7H6O3_, o interpretador retorna para a chamada de origem, ou seja, 1 linha a mais da instrução que chamou a outra instrução. No entanto, os saltos e as chamadas podem ser **incondicionais**, ou seja, não necessitando de uma condição. A partir de agora, iremos utilizar os identificadores nos exemplos e os códigos equivalentes em C, primeiramente vamos ver quais argumentos que especifica um salto ou uma chamada:
  
   #### 1ª Argumento (Saltos):
              
              Operações lógicas da posição atual $:
            
               0 -> Salto incondicional
               1 -> Salta se for igual
               2 -> Salta se for diferente
               3 -> Salta se for maior
               4 -> Salta se for menor
               5 -> Salta se for maior ou igual
               6 -> Salta se for menor ou igual
               7 -> Salta se AND deu verdadeiro
               8 -> Salta se OR deu verdadeiro
               9 -> Salta se for diferente de 0
               10 -> Salta se for igual a 0
               
             Operações lógicas da posição anterior #:
            
               11 -> Salta se for igual
               12 -> Salta se for diferente
               13 -> Salta se for maior
               14 -> Salta se for menor
               15 -> Salta se for maior ou igual
               16 -> Salta se for menor ou igual
               17 -> Salta se AND deu verdadeiro
               18 -> Salta se OR deu verdadeiro
               19 -> Salta se for diferente de 0
               20 -> Salta se for igual a 0
                
   #### 1ª Argumento (Chamadas):
              
              Operações lógicas da posição atual $:
            
               30 -> Chamada incondicional
               31 -> Chama se for igual
               32 -> Chama se for diferente
               33 -> Chama se for maior
               34 -> Chama se for menor
               35 -> Chama se for maior ou igual
               36 -> Chama se for menor ou igual
               37 -> Chama se AND deu verdadeiro
               38 -> Chama se OR deu verdadeiro
               39 -> Chama se for diferente de 0
               40 -> Chama se for igual a 0
               
             Operações lógicas da posição anterior #:
            
               41 -> Chama se for igual
               42 -> Chama se for diferente
               43 -> Chama se for maior
               44 -> Chama se for menor
               45 -> Chama se for maior ou igual
               46 -> Chama se for menor ou igual
               47 -> Chama se AND deu verdadeiro
               48 -> Chama se OR deu verdadeiro
               49 -> Chama se for diferente de 0
               50 -> Chama se for igual a 0
               
   Como vimos, todos esses números se trata das funcionalidades dos saltos e chamadas apenas do 1ª argumento da instrução _C20H28O3_, os saltos são de 0 à 20 e as chamadas são de 30 a 50, a condição irá fazer uma operação lógica do valor da posição de memória (seja ela atual ou anterior dependendo do valor do 1ª argumento) com o 3ª argumento que poderá ser um número estático ou uma própria posição de memória, se a condição for satisfeita, a instrução vai utilizar o 2ª argumento para saltar para o valor desse argumento, que será nosso identificador, então vamos ver na prática um salto incondicional para o 1ª identificador (loop infinito), desta vez no Bottle principal "cup" (copo):
   
     
  **Código em CFOCOL:**
  
             cup:
                 0000: C8H10N4O2 Tomando café eternamente%!  -> Exibe uma string com quebra de linha no identificador 0000
                 0001: C20H28O3 0,0000,0!                    -> Salta incondicionalmente para o identificador 0000
             ;
             
  **Código em C:**
             
             while(true){
                 printf("Tomando café eternamente\n");
             }

  **Código em Assembly:**
  
             cup:
                 mov si, String
                 call PrintString
                 jmp cup
              String db "Tomando café eternamente",13,10,0
              
   No código em CFOCOL, o identificador 0001 tem a instrução _C20H28O3_ com o 1ª argumento 0 (salto incondicional), na qual ele salta para o identificador 0000 que está com a instrução de exibição de caracteres _C8H10N4O2_, porém se é incondicional significa que o 3ª argumento é inútil, pois não é utilizado na condição, logo, o 3ª argumento deve ser 0, pois o mínimo de argumentos nessas instruções são 3 (mesmo sendo inútil), é claro que em outras versões vamos alterar essa funcionalidade, removendo o 3ª argumento em situações incondicionais.
   
 Por enquanto, o interpretador funciona apenas para o 1ª Bottle cup, ou seja, não é possível chamar instruções de outros Bottles utilizando o sinal '_', como: _@Bottle1_0000_, isto vamos implementar na 2ª versão do interpretador. Então agora veremos outra situação que é um salto condicional, comparando o valor da posição de memória atual com 10, enquanto não for, ele saltará para a instrução:
 
 **Código em CFOCOL:**
 
            cup:
                 0000: C8H10N4O2 Tomando café eternamente%!  -> Exibe uma string com quebra de linha no identificador 0000
                 0001: C7H8N4O2 0,$,1!                       -> soma +1 na posição atual de memória (inicialmente é 0)
                 0002: C20H28O3 2,0000,10!                   -> Salta para o identificador 0000 se posição atual é diferente de 10
            ;
   
  **Código em C:**
             
             for(int i = 0; i != 10; i++){
                 printf("Tomando café eternamente\n");
             }
             
 **Código em Assembly:**
  
             cup:
                 mov cl, 0
                 loop:
                    mov si, String
                    call PrintString
                    inc cl
                    cmp cl, 10
                    jne loop
              String db "Tomando café eternamente",13,10,0
              
  
 Nestes códigos exemplos, as 3 linguagens executa a mesma operação: Exibir a string "Tomando café eternamente" 10 vezes. Então, enquanto uma condição não for satisfeita (valor for diferente de 10), uma mesma instrução será executada, por um salto condicional. O 1ª argumento 2 da instrução em CFOCOL simboliza a operação lógica **diferente** e desta vez o 3ª argumento 10 se torna útil, pois é com esse argumento que vamos comparar o valor da posição atual 0 (que é padrão em casos que não utiliza o deslocamento). Desta vez vamos pro último exemplo de um mesmo salto condicional mas comparando com a posição anterior e não com a posição atual, porém precisamos utilizar os deslocamentos:
 
  **Código em CFOCOL:**
 
            cup:
                 0000: C8H10N4O2 ,<$>, !       -> Exibe o número 0 da posição atual com espaço
                 0001: C9H8O4 0,1!             -> desloca +1 posição na memória
                 0002: C7H8N4O2 0,$,1!         -> soma +1 na posição atual de memória (inicialmente é 0)
                 0003: C9H8O4 1,1!             -> desloca -1 posição na memória
                 0004: C20H28O3 12,0000,10!    -> Salta para o identificador 0000 se posição anterior é diferente de 10
            ; 
            
   **Código em C:**
             
             for(int i = 0; i != 10; i++){
                 int j = 0;
                 printf("%d ", j);
             }
             
    
   **Código em Assembly:**
  
             cup:
                 mov cl, 0
                 mov ah, 0Eh
                 loop:
                    mov al, '0'
                    int 10h
                    mov al, ' '
                    int 10h
                    inc cl
                    cmp cl, 10
                    jne loop
                    
   
  Nestes códigos exemplos, nós incrementamos um valor mas exibimos outro, ou seja, uma variável em C é incrementada e utilizada na condição e a outra variável é exibida mas nunca incrementada, no total de 10 vezes. No Assembly a mesma coisa é feita, cl é incrementado e comparado mas o que é exibido é o que está em al que é o char '0'. Tudo isso se trata de exibir um valor diferente daquele que é o incremento, pois o valor de incremento só é utilizado como _contador_ de um programa, em CFOCOL não é diferente, podemos ter inúmeros valores pra exibir em posições de memória totalmente distintas e utilizando um contador individual de incremento. Por enquanto, tudo parece simples, pois temos um programa menor, mas como a própria frase de Alan perling diz sobre as linguagens Turing Tarpit: "Cuidado com o Turing Tarpit, onde tudo é possível mas nada de interessante é fácil". Isso quer dizer que, quanto maior for a necessidade do nosso programa, maior é a quantidade de variáveis diferentes a ser utilizadas e mais complexo será o programa em CFOCOL pois não existem variáveis em CFOCOL, e aí, uma tremenda gambiarra de operações aritméticas + deslocamento de memória deve ser feita para alcançar tal propósito, muito café deve estar armazenado no organismo para atingir tal privilégio porque não é impossível, mas é difícil. Então tudo isso, pode alimentar a teoria de que os limites das possibilidades de um método funcional pode ser testado, a fim de chegar numa conclusão de como um programa "quase-primordial" pode simular na vida real. CFOCOL não é uma linguagem Turing Completa, mesmo adotando algumas características, mas chega perto dessa categoria mesclados com conceitos imperativos de programação. 
  
  <a href="#menu">Voltar ao menu</a>
  <a name="call"></a>  
 ### Chamadas Condicionais/Incondicionais
 
Então, nosso próximo passo é substituir a **operação de salto** por **operação de chamada**, mas não vamos substituir a instrução em si que é o cafestol, manteremos esta instrução e a única coisa que vamos substituir é um único argumento - O primeiro. Como além de orientação a cafeína, é uma linguagem orientada a argumentos, vamos começar a chamar as instruções condicionalmente com retornos manipulados ou não pelo interpretador, tal retorno será o ácido hidroxibenzóico _C7H6O3_ e também veremos sobre os códigos equivalentes em C e Assembly, primeiro vamos ver como funciona as chamadas incondicionais em CFOCOL:


**Código em CFOCOL:**
 
           cup:
                0000: C20H28O3 0,0003,0!            -> Salto incondicional para a instrução 0003
                0001: C8H10N4O2 A!                  -> Exibe a letra A 
                0002: C7H6O3 0,0!                   -> Retorna a chamada de origem
                0003: C20H28O3 30,0001,0!           -> Chama a instrução 0001 (Chamada de origem)
                0004: C8H10N4O2 %Fim do programa%!  -> Exibe "Fim do programa" com quebra de linha no Início e Final
           ;
 
 **Código em C:**
 
           void Exibir(){
               printf("A");
           }
           int main(void){
             Exibir();
             printf("\nFim do programa\n");
             return 0;
           }

**Código em Assembly:**

           jmp Main
           Exibir:
              mov ah, 0Eh
              mov al, 'A'
              int 10h
           ret
           Main:
              call Exibir
              mov si, String
              call PrintString  ;rotina pra exibir caracteres do que está em si
              jmp END
           String db 13,10,"Fim do programa",13,10,0
           
  Assim como no código Assembly, a instrução _jmp_ efetua um salto incondicional para a rotina _Main_, no código CFOCOL a instrução _C20H28O3_ salta para a instrução cujo identificador é _0003_, não satisfazendo nenhuma condição pois o 1ª argumento é 0. Em Assembly utilizamos a instrução _call_ para chamar uma rotina que terá retorno, executando cada linha até achar um _ret_, quando ret é encontrado, o programa salta novamente para a chamada de origem, onde se encontra o _call_, porém o salto de retorno não é feito para a mesma linha que tem a chamada, e sim, na linha abaixo a ela, isso porque alguns registradores em Assembly trabalham para armazenar no topo da pilha o endereço da instrução abaixo da instrução do _call_, utilizando um **salto incondicional** (jmp) para o endereço da rotina chamada, executando as instruções e no retorno, o endereço armazenado pelo call é recuperado, saltando novamente para esse endereço. Em C, o mesmo processo acontece, porém a programação ocorre da forma mais abstrata, o programador apenas chama a função _Exibir()_ que executa e automaticamente retorna pra sua chamada de origem, que após vai executar a próxima função que é o _printf("\nFim do programa\n")_, claro que como o tipo da função Exibir() é _void_, nenhum valor é retornado porém a leitura do programa é retornada para o endereço da instrução. Em CFOCOL, a instrução do _0003_ é executada, efetuando outro salto incondicional para o identificador _0001_ (abaixo do 1ª salto pois se não seria um loop infinito), no identificador _0001_ exibe uma letra, vai para o próximo passo, que terá a instrução de retorno _C7H6O3_, essa instrução de retorno vai saltar novamente para a instrução "abaixo" da instrução que efetuou a chamada, na qual é a instrução de exibição de caracteres que imprimirá na tela "Fim do programa".
  
  Isso significa que, o que possibilita a instrução de salto _C20H28O3_ em cfocol **armazenar** em pilha o endereço da instrução (como a explicação do Assembly) é o 1ª argumento, cujo argumento é 30, de 31 pra frente tudo será uma **chamada condicional** e a instrução _C7H6O3_ trabalha em conjunto para **recuperar** esse endereço da pilha e saltar novamente. Agora veremos um último exemplo de como será uma chamada condicional em CFOCOL com seus respectivos equivalentes em C e Assembly:
  
  **Código em CFOCOL:**
 
           cup:
                0000: C20H28O3 0,0004,0!                -> Salto incondicional para a instrução 0004
                0001: C7H8N4O2 0,$,1!                   -> incrementa +1 no valor
                0002: C8H10N4O2 A !                     -> Exibe a letra A 
                0003: C7H6O3 1,1!                       -> Retorna para o "endereço de chamada" -1
                0004: C8H10N4O2 %Exibindo letras%%!     -> Exibe uma string
                0005: C20H28O3 34,0001,10!              -> Chama a instrução 0001 se valor for menor que 10
                0006: C8H10N4O2 %%Fim do programa%!     -> Exibe "Fim do programa" com quebra de linha no Início e Final
           ;
 
 **Código em C:**
 
           void Exibir(){
               printf("A ");
           }
           int main(void){
             printf("\nExibindo letras\n\n");
             for(int i = 0; i < 10; i++)
                Exibir();
                
             printf("\nFim do programa\n");
             return 0;
           }

**Código em Assembly:**

           jmp Main
           Exibir:
              mov ah, 0Eh
              mov al, 'A'
              int 10h
              mov al, ' '
              int 10h
           ret
           Main:
              mov si, StringIni
              call PrintString
              mov cl, 0
              loop:
                  inc cl
                  call Exibir
                  cmp cl, 10
                  jb loop
                  mov si, StringEnd
                  call PrintString
              jmp END
           StringIni db 13,10,"Exibindo letras",13,10,13,10,0
           StringEnd db 13,10,13,10,"Fim do programa",13,10,0
  
   
  
 Para enfatizarmos melhor o exemplo, vamos utilizar 3 novos métodos: 
         
         1. O primeiro argumento da instrução 0005 é alterado de 30 para 34 (chama se for menor);
         2. Usamos uma operação aritmética para incrementar valor no endereço;
         3. O retorno _C7H6O3_ recebe 2 novos tipos de argumentos;
         
   O 1ª argumento da instrução _C20H28O3_ sendo 30, seria uma chamada incondicional, mas sendo acima desse valor, Ex.: 31,32,etc.. seria uma chamada condicional, cada valor se refere a um tipo de condição (Como vimos anteriormente), então após a instrução no Id. 0000 chamar a instrução 0004 (que vai exibir "Exibir letras"), o próximo passo será saltar para a instrução no Id. 0001 se o valor da posição atual de memória for menor que 10, satisfazendo a condição, a instrução no Id. 0001 vai somar 0 + 1 na posição de memória, já que o início do valor é 0 por padrão, Na posição 0 agora tendo o valor 1, o próximo passo é executado exibindo a letra A com espaço e após, a instrução de retorno _C7H6O3_ vai retornar para a Instrução 0005 (chamada) + 1, que é 0006, isso se os argumentos da instrução de retorno fosse 0, porém algo mudou, vemos que é "C7H6O3 1,1!". Isso significa que o 1ª argumento da instrução de retorno vai simbolizar a operação: se for 0 é soma, se for 1 é subtração; E o 2ª argumento vai ser o número de deslocamento de retorno, Exemplo: Se naturalmente os argumentos sendo 0, a instrução retornava para o Id. 0006 (0005 + 1), os argumentos sendo "1,1", vai subtrair o deslocamento -1, ou seja, se era 0006, será 0005, exatamente na mesma instrução que efetua a chamada, re-executando a instrução novamente. Se os argumentos fossem 1,3 por exemplo, iria subtrair o deslocamento -3 (0006 - 3 = 0003). Se o primeiro argumento fosse 0, logo iria somar 0006 + 3 = 0009 (esse identificador não existe no código), portanto iria dar erro, retornando para um identificador que não existe.
   
   Todo esse programa constrói um Loop de repetição onde é o retorno da chamada que vai definir esse loop, isso vai depender dos seus argumentos. E aí, a junção de hidroxibenzóico + cafestol, usando argumentos certos, poderá construir inúmeros tipos de loops For, do, While e chamada de funções equivalentes em C, e saltos condicionais je, jne, jb,ja,etc.. + instruções CALLs equivalentes em Assembly. Perceba também que a String "Exibindo letras" só é imprimida uma vez no programa (primeira vez), pois durante a iteração do loop, a instrução de retorno é chamado antes da instrução de impressão.

<a href="#menu">Voltar ao menu</a>
<a name="prog"></a>
### Programas em CFOCOL

Veremos alguns programas em CFOCOL para problemas mais simples, estes programas estão na pasta **Examples** dentro deste repositório:

#### Exibindo resto de uma divisão

![](/Imagens/resto.png)

O clássico programa em programação que consiste em identificar o resto de uma divisão, Em outras linguagens consiste em utilizar o operador _%_ para verificar se um número é divisível por outro, porém em CFOCOL acontece de uma forma onde tudo deve ser feito passo a passo: Divide o dividendo pelo divisor, pega o resultado e multiplica pelo divisor e o resultado é subtraído pelo dividendo, o resto do dividendo pelo divisor é o resultado da subtração, já que não utilizamos variáveis é necessário utilizar as instruções de deslocamento. Como não utilizamos _saltos_, os identificadores podem ser zero, pois eles só servem pra identificar uma determinada instrução durante os saltos.

#### Fatorial de um número

![](/Imagens/fator.png)

Outro clássico é identificar o Fatorial de um número. Este programa em outras linguagens é utilizado um loop recursivo _Fatorial(n) = n * Fatorial(n-1)_ . A mesma lógica em CFOCOL pode ser utilizado usando chamadas condicionais & retornos manipulados, porém neste exemplo usamos apenas os saltos condicionais e os deslocamento de memória onde usamos 2 posições diferentes de memória: Uma para decrementar o valor e outra para armazenar os resultados das multiplicações.

#### Símbolos da Tabela ASCII

![](/Imagens/ascii.png)

Que tal exibir todos os símbolos da tabela ascii em cfocol? Isto pode ser necessário para relembrar os caracteres desta tabela e também o programa pode ser adaptado para exibir as diversas representações desses símbolos como: Hexadecimal, Binário, Octal e Decimal, porém é necessário muita cafeína no organismo para concretizar tal operação. No entanto, exibir os 256 caracteres da Tabela ASCII é bem simples: basta incrementar um valor de uma posição de memória e ir exibindo até que a condição de um salto seja verdadeira, ou seja, até que o determinado valor chegue a 256.

#### Hello World de Operações aritméticas

![](/Imagens/helloworld.png)

Eis aqui um "simples" Exemplo Hello World. Como em toda linguagem de programação, existe uma forma de entrar nela conhecendo os primeiros programas Hello World, em CFOCOL não é diferente. Por mais que é possível exibir uma frase normal através da instrução de impressões, podemos brincar um pouco exibindo caracteres de forma calculada. Isso é até importante no caso de armazenar Strings em memória, pois só é possível uma String ser armazenada caractere por caractere em formato decimal calculadamente de forma estática ou dinâmica e isso também possibilita construir sistemas complexos de criptografia.

#### Programa soma de 5

![](/Imagens/teste.png)

Este programa apesar de ser simples, é bem interessante por um detalhe: teste de outros tipos de operações lógicas. Este programa exibe X números somados com 5, porém tudo pode mudar na mudança do 1ª argumento. O sistema salta para o Id. 1 enquanto é diferente de 50 mas aí é que entra, Enquanto a quantidade de números for diferente de 50 ou enquanto o próprio número final for diferente de 50? Pois então, o argumento com o número 2 indica a 2ª opção, porém se somar esse argumento +10, ou seja, 12, será a 1ª opção pois ele não vai comparar os valores da posição atual mas sim da posição anterior, e isso acarreta uma mudança no programa, exibindo 50 números somados com 5 e não, X números até 50. Outra mudança é alterar os argumentos para 6 ou 16, que pode exibir um número a mais no final da interação, os argumentos 4 e 14 também podem ser usados.

[Saiba mais sobre outros códigos na pasta Examples](https://github.com/FrancisBFTC/CFOCOL_Programming/tree/master/Examples)

<a href="#menu">Voltar ao menu</a>
<a name="com"></a>
### Comentários em CFOCOL

Outra questão que ainda não foi tratada nesta documentação são os _comentários_. Perceba que durante as explicações das funcionalidades das instruções, após a finalização de todas as instruções CFOCOL, identificados pelo símbolo '!', colocamos uma descrição daquela instrução sempre com um símbolo '->', porém isso é só uma referência a descrição e não uma regra de comentários, Pois nos comentários não existem regras de símbolos, apenas uma convenção que pode ser alterada por qualquer programador, isso explica o motivo das imagens mostradas anteriormente ter os comentários entre aspas, não é uma regra. Qualquer texto, colocado após o símbolo '!' de exclamação, será ignorado. A execução de instruções finaliza no símbolo !, após isso, tudo é comentário porém por uma convenção, pode ser colocado símbolos identificadores de comentários, para facilitar na manutenção do código.

<a href="#menu">Voltar ao menu</a>
<a name="inp"></a>
### Entrada de dados & Bottles Secundários

Por enquanto, as funcionalidades de Inputs (Entrada de dados do teclado) não foi criada, algumas metodologias seguindo o paradigma do CFOCOL ainda estão sendo pensadas a respeito sobre entrada de dados. Os Bottles Secundários também ainda não foram criados, pois ainda todo o interpretador se baseia apenas em 1 matriz de dados que é relacionado ao Bottle "Cup" (Main), para desenvolver outros Bottles, durante a pré-interpretação, é preciso armazenar os Bottles Secundários em uma outra matriz separada por índices de uma estrutura de dados, onde ocorrerá um **mapeamento** de índices passando como referência o nome do Bottle, e isso será feito em outra versão do CFOCOL, que será a definitiva, incluindo a **entrada de dados** através da Instrução sacarose _C12H22O11_ e possíveis outros sinais da linguagem. Então, A linguagem está na versão Alfa e em breve promete chegar na versão Beta. Abaixo será disponibilizado o Link da outra versão da documentação:

(Link não disponível)

<a href="#menu">Voltar ao menu</a>
<a name="mode"></a>
### Modos de interpretação

<a name="command1"></a>
#### Via linha de comando

Para executar via linha de comando, apenas abra o CMD e navegue até o diretório que contém o executável do cfocol. O interpretador só requere 1 argumento na linha de comando - o nome do arquivo/diretório do arquivo. No entanto, é preciso conhecer a extensão utilizada em arquivos CFOCOL e são elas: .cf, .cfl e .cop. O interpretador vai reconhecer apenas essas 3 extensões de arquivos, veja o exemplo do arquivo resto.cf sendo interpretado de 3 extensões diferentes:

![](/Imagens/ext1.png)
![](/Imagens/ext2.png)
![](/Imagens/ext3.png)

Tente interpretar um arquivo com uma extensão diferente e veja o que acontece:

![](/Imagens/ext4.png)

Por enquanto, não existem outros parâmetros de linha de comando na versão Alfa do interpretador, como por exemplo: --verbose, --debug. Isto porque a linguagem ainda não está completa.

<a href="#menu">Voltar ao menu</a>
<a name="command2"></a>
#### Via linha de comando global (Variáveis de Ambiente)

Para executar o interpretador em qualquer região do computador, é preciso adicionar na variável PATH das Variáveis de Ambiente do sistema. Se tiver utilizando Windows 7, vá em "computador" ou "Meu computador", clique em _propriedades_, no painel de controle abra as _Configurações avançadas do sistema_, na janela que abriu clique no botão _Variáveis de Ambiente_ e na região de Variáveis do sistema, procure e selecione a variável _path_, clique no botão _Editar_ e vai até o final do valor onde está o ;, após o ; adicione o diretório onde está o executável **cfocol.exe**, Exemplo: C:\CFOCOL\;, após isso é só dar os OKs e pronto. Se optar, execute como administrador o arquivo [ConfigSystem.bat](https://github.com/FrancisBFTC/CFOCOL_Programming/tree/master/Config) deste repositório, que ele irá efetuar todos esses procedimentos automaticamente, só é preciso fornecer um caminho de entrada do interpretador durante a execução.

![](/Imagens/varsamb.png)
![](/Imagens/global.png)

<a href="#menu">Voltar ao menu</a>
<a name="click"></a>
#### Clique Duplo

Outra opção de interpretação é dar **Cliques duplos** nos arquivos CFOCOL. No momento que cria um arquivo no computador, cuja extensão é desconhecida pelo sistema operacional, pela primeira vez, o sistema operacional cria registros no banco de dados do sistema com uma pasta nomeada com a extensão criada, Exemplo: .cf, .cop,etc.. nas chaves do sistema e de usuário desse registro, a extensão ainda está vazia, ou seja, não contém nenhuma informação relevante para o sistema operacional interpretar o tipo daquele arquivo, portanto o padrão de todo tipo de arquivo desconhecido pré-criado será - **Abre com:** _DLL comum do Shell..._; **Tipo de arquivo:** Arquivo EXTENSÃO (onde a palavra EXTENSÃO é substituída pela extensão criada pela primeira vez), no nosso Exemplo seria: Arquivo CF, Arquivo CFL, etc... a forma mais simples de fazer o S.O adicionar mais informações para aquele tipo de arquivo é **Abrir o arquivo com algum programa** pela primeira vez, e marcar pra sempre abrir com aquele programa quando ser clicado, o nosso programa é o interpretador cfocol.exe, então veja o antes e o depois nas imagens do arquivo sem um programa associado e com uma associação:

**Sem associação de nenhum programa**:

![](/Imagens/assoc1.png)
![](/Imagens/assoc2.png)

**Com associação do interpretador**:

![](/Imagens/assoc3.png)
![](/Imagens/assoc4.png)

Perceba que após o arquivo ser associado ao executável, podemos clicar 2 vezes e executar o arquivo, porém como a janela do CMD vai abrir muito rápido, é preciso adicionar algum comando de esperar tecla, na qual poderemos fazer daqui em diante, o mesmo procedimento pode ser feito executando o arquivo direto na linha de comando, em vez de digitar **cfocol resto.cf**, apenas digite: **resto.cf** e o arquivo será executado. Fazer isso é simples: basta clicar 2 vezes no arquivo, na janela que abre (como na 2ª imagem da parte de **sem associação de nenhum programa**), selecione a opção _Selecionar um programa em uma lista de programas instalados_ e dê um ok, na próxima janela que abrir vai ter uma lista de programas que você pode usar para abrir este tipo de arquivo, porém como queremos abrir com o interpretador, basta clicar em **Procurar** (caso o interpretador não esteja na lista) e procure o diretório onde você colocou a pasta e o executável do interpretador e selecione o executável **cfocol.exe**, é recomendável que depois desta associação não excluir o executável do diretório, porém o executável pode ser substituído por outro em casos de atualização do código-fonte do interpretador. Veja a imagem abaixo:

![](/Imagens/assoc5.png)

No entanto, como vimos na imagem, apenas o programa em que o arquivo é aberto, é atribuído e associado, pois apenas esta informação é armazenada no Editor de registros do S.O, porém ainda se mantém o nome padrão **Arquivo CF** ou **Arquivo COP**, você poderá editar manualmente o Editor de registros para adicionar mais informações como: Ao clicar em **Editar** sobre o arquivo, ele abre com um Editor padrão; Ter uma lista de programas possíveis para o arquivo ser aberto; Alterar a descrição do tipo de arquivo - em vez de **Arquivo CF**, algo como, **Arquivo de programação CFOCOL**, ou, **CFOCOL File**; Executar diversos parâmetros do interpretador através do mouse; e Por aí vai... são muitas coisas que se pode fazer sobre um arquivo com extensão nova de linguagem pelo Editor de Registros, só é recomendável sempre estudar melhor sobre o assunto para não mecher com chaves erradas no Registro, pois isso pode danificar o sistema operacional. Existe 2 formas para fazer todas essas operações com segurança nos arquivos CFOCOL: Manual e Programado. Para saber mais sobre o assunto, acesse o vídeo do Youtube que ensino: [**Como criar tipos & Extensões de arquivos no Editor de Registros**](https://www.youtube.com/watch?v=vNV6SAtMvgY), clicando neste link você será redirecionado para o meu canal no Youtube onde ensino as 2 formas que falei pra fazer alteração nos registros. Veja abaixo algumas imagens de exemplos após a edição do Editor de Registros:

![](/Imagens/icon0.png)

Primeiro, resolvi testar um ícone comum do Shell do sistema operacional Windows. Este ícone se encontra no diretório e arquivo _%SystemRoot%\system32\SHELL32.dll_ (mais na frente mostrarei onde que identifica isso). Percebam que no **Tipo de arquivo** o nome foi alterado de **Arquivo CF** para **CFOCOL Programming File** e tanto as 3 extensões (.cf, .cfl e .cop) acompanham essa mudança, tudo isso é feito no Editor de registros.

![](/Imagens/icon1.png)

Já este ícone é enganador mas não é o que está pensando, ele é o ícone de pasta padrão do sistema operacional, e se encontra no mesmo arquivo _SHELL32.dll_, porém não na posição 0 mas em outra posição. Quando é inserido numa determinada chave do registro um diretório com arquivo DLL, pode-se especificar a posição separado por vírgulas, este ícone teria a posição 3, ficando assim no registro: _%SystemRoot%\system32\SHELL32.dll,3_, Então estes ícones não vem do executável CFOCOL, porque em relação ao CFOCOL nada foi alterado sobre Ícones do software e também estes arquivos CFOCOL não são "Atalhos", onde se pode alterar o ícone de forma comum, mesmo tendo ícone de pastas eles ainda são arquivos CFOCOL executáveis com duplo cliques.

![](/Imagens/icon2.png)

E até mesmo nesta imagem utilizo uma DLL do VisualStudio, onde a DLL é chamada de: Microsoft.VisualStudio.ORDesigner.DslPackage.dll. Onde o ícone da imagem faz parte de uma função interna do VisualStudio e pode ser alterado na mesma chave de registro do Windows.

![](/Imagens/icon3.png)

Então, decidi definitivamente usar este ícone do próprio sistema operacional, Pois ele tem mais cara de um arquivo de Fórmulas químicas. em outras ocasiões podemos ver/criar ícones melhores. Este ícone assume o seguinte valor do sistema: _%SystemRoot%\system32\SHELL32.dll,84_; Ele está na 84ª posição da DLL e é inserida na chave cuja estrutura de pastas mostrarei na próxima imagem:

![](/Imagens/RegEditConf.png)

Na esquerda são as estruturas de pastas que chamamos de _Chaves de registros_, cada Chave (Pasta) pode assumir **nomes** e **valores**. Então, Na direita é que são definido esses Valores, que podem ser binários, nulos ou como **Cadeia de caracteres**. Exemplo: a Chave **cfocol.file** tem o valor padrão "CFOCOL Programming File", na qual irá aparecer nos tipos de arquivos associados a esta chave, dentro da chave cfocol.file, existem as sub-chaves e uma delas é a **DefaultIcon** - O valor padrão dessa sub-chave deve ter o diretório de um executável ou uma DLL, cujo executável contém o mesmo ícone, porém se for uma DLL, deve especificar uma posição numérica no final do valor da sub-chave. no caso do _%SystemRoot%\system32\SHELL32.dll,84_ é inserido exatamente como valor padrão do DefaultIcon, para manter o ícone definitivo mostrado na imagem anterior.

Vamos identificar agora onde é obtido este diretório. Primeiramente, é preciso criar um atalho de qualquer arquivo, após criar, clicar em _propriedades_ do arquivo e depois clicar em _Alterar Ícone_ na próxima janela que se abrirá, vai aparecer inúmeros ícones do sistema operacional que se pode escolher, cada ícone terá uma posição numérica contada de cima pra baixo e todos esses ícones terá um campo especificando o diretório dll onde se encontra, basta contar os ícones de cima pra baixo, identificar a posição e acrescentar esta posição após o diretório, veja na imagem abaixo:

![](/Imagens/icon4.png)

Existem outras estruturas de pastas em outras chaves mas isto seria muita coisa pra ser explicado nessa documentação, então resolvi disponibilizar no mesmo repositório na pasta **Config** o arquivo [cfocol_registry](https://github.com/FrancisBFTC/CFOCOL_Programming/tree/master/Config) que terá o Script de registros pra executar todas as configurações das 3 extensões do CFOCOL mas isso pode ser alterado de sua escolha, algumas configurações como as "configurações adicionais" sobre Editor a ser utilizado pode ser mudado no Script, porém é preciso conhecer sobre a Edição de registros (Como dito anteriormente, esta é a forma programada), então se não tem conhecimento sobre o assunto, recomendo que assista o vídeo [**Como criar tipos & Extensões de arquivos no Editor de Registros**](https://www.youtube.com/watch?v=vNV6SAtMvgY).

<a href="#menu">Voltar ao menu</a>
<a name="linux"/>
### Executando em distros Linux

Caso esteja usando uma distribuição Linux, apenas será possível executar o interpretador usando o Wine.
Para instalá-lo é muito simples, se estiver em uma distribuição baseada em Debian (Ubuntu, Linux Mint, etc) abra do terminal e execute:
```
sudo apt update
sudo apt install wine
```

E caso esteja a usar uma distribuição baseada em Red Hat (ex: Fedora, CentOS, etc), execute:
```
sudo dnf install wine
```

Para executar o interpretador basta ir para a pasta do mesmo e executar:
```
wine cfocol.exe
```

Exemplo:
```
wine cfocol.exe Examples/HelloWorld.cf
```


<a href="#menu">Voltar ao menu</a>
<a name="colors"></a>
### Cores sintáticas no Editor

Pra finalizarmos essa documentação, vamos falar sobre as configurações do Editor. Todos os editores modernos contém uma identificação de linguagem de programação e quando se salva um arquivo com uma determinada extensão, o editor já identifica a linguagem e automaticamente colore os códigos durante o desenvolvimento, isso também facilita muito na hora de visualizar e desenvolver os algoritmos. Cada linguagem tem sua própria configuração no Editor, com fontes, cores e tamanhos diferenciados pra cada operador, instrução, variáveis ou até comentários. Estas configurações são identificadas pelo Editor através de arquivos XML e podem ser alteradas tanto em arquivos XML quanto no menu de **Linguagem** do Editor. Veja no exemplo abaixo um código em C do arquivo cfocol.cpp no Notepad++ e a configuração de linguagem desse editor:

![](/Imagens/lang0.png)

A grande questão é que podemos criar nossas próprias cores de novas linguagens, exportando e importando arquivos XML que colore automaticamente nossos códigos. No Notepad++ isso é feito no menu **Linguagem** e **Defina o seu idioma**, logo uma janela irá se abrir pra fazer inúmeras edições de cores sintáticas:

![](/Imagens/lang1.png)

A partir do momento que você fazer estas configurações e salvar, todos os arquivos que você criar com uma determinada extensão e tipo configurado, vai ser identificado pelo editor e durante o desenvolvimento, os códigos irá se colorir. Neste repositório na pasta Config, já existe um arquivo chamado [EditorConfig.xml](https://github.com/FrancisBFTC/CFOCOL_Programming/tree/master/Config), agora mostrarei os passos de como importar este arquivo no Editor Notepad++:

Vá no menu _Linguagem_ e clique em _Defina o seu idioma_:

![](/Imagens/lang2.png)

Na janela que abriu, clique no Botão _Importar_ e escolha o arquivo _EditorConfig.xml_:

![](/Imagens/lang3.png)

Após isso, é só marcar em **idioma do...** a opção **cfocol** e todas as configurações de cores de palavras-chaves estarão lá, disponíveis pra ser alteradas ou utilizadas. Pode-se exportar outros tipos de configurações pra outras linguagens também.

![](/Imagens/lang4.png)

Todas as configurações salvas de novas linguagens, irá armazenar no menu **linguagem**, quando criar um arquivo cfocol pela primeira vez, marque o nome **cfocol** no menu **linguagem**, abaixo do **Defina o seu idioma** e partir daí, toda vez que salvar um arquivo na extensão .cf, .cfl ou .cop, o Editor automaticamente irá colorir os códigos do CFOCOL.

Para conhecer mais sobre esse assunto de Edição de cores em códigos no Notepad++, clique no link [Criando visual de códigos de uma linguagem própria no Notepad++](https://www.youtube.com/watch?v=tjg0f8krCwk)

<a href="#menu">Voltar ao menu</a>


Então, isso é tudo que devemos saber sobre o cfocol por enquanto, vimos muita coisa nesta documentação, porém possivelmente nas próximas versões após a linguagem ficar completa, o desenvolvimento vai ficar mais amplo, ou seja, seria uma boa idéia criar uma IDE própria para o CFOCOL que consegue reconhecer instruções específicas e aliás, ter as mesmas configurações de linguagem do Notepad++ mas por enquanto vamos apenas focar no funcionamento da linguagem.

Enfim, quero agradecer por ter chegado até aqui e meus parabéns! você realmente ultrapassou os limites da cafeína no organismo e tem de sobra pra poder programar em qualquer linguagem de programação (não importa a sua complexidade). É uma honra pra mim está compartilhando este repositório para pessoas que querem aprender a desenvolver uma linguagem de programação ou até aqueles que pretendem colaborar com o projeto e tornar a linguagem mais eficiente e segura, como também abrir novas oportunidades de funções, novas linguagens e novos paradigmas. Então, aproveite o desenvolvimento em CFOCOL!

Canal no Youtube: [BFTCorporations](https://www.youtube.com/channel/UCAC2WHKy7UmEQXaZbMfcszg)<br>
Perfil no Facebook: [Wender Francis (francis.bftc)](https://www.facebook.com/francis.bftc)<br>
Perfil no Instagram: [Francis.System (@francisbftc.sys)](https://www.instagram.com/francisbftc.sys/)<br>
Perfil no Linkedin: [Wender Francis](https://www.linkedin.com/in/bftcorporations/)<br>
<br>
Curso D.S.O.S : [Desenvolva um sistema operacional do zero em Assembly que também terá sua própria linguagem de programação](https://www.youtube.com/playlist?list=PLsoiO2Be-2z8BfsSkspJfDiuKeC9-LSca)
<br><br>
Agradecimentos BFTCorporations!
<br><br>
<a href="#menu">Voltar ao menu</a><br>
<a href="https://github.com/FrancisBFTC/CFOCOL_Programming">Voltar ao repositório</a>
