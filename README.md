# TII---POS
## Componentes
  - Laís Pereira do Nascimento
    - Matrícula: 20141011110107  
    - Github Nickname: laypereirar
  - Sarah Rebecca Soares Penha
    - Matrícula: 20141011110182 
    - Github Nickname: soaressarah  
  - Vanessa Cristiane Santos
    - Matrícula: 20141011110034
    - Github Nickname: santosvanessa
## Linguagem
  - Chakra

## Resumo
1. Propósito da linguagem
    - O Elm é uma linguagem de programação específica de domínio para a criação de interfaces de usuário gráficas baseadas em web browser. Elm é puramente funcional, sendo desenvolvido com ênfase na usabilidade, desempenho e robustez.  Elm compila para JavaScript, HTML e CSS. O principal foco da linguagem é trazer os benefícios (e garantias) da Programação Funcional para o Front-End.
2. Paradigma da Linguagem
    - Funcional.
3. Data de criação
    - O Elm foi criado em 2012, por Evan Czaplicki. Em 2013, Czaplicki, juntou-se ao Prezi em 2013 para trabalhar no Elm, e em 2016 mudou-se para NoRedInk como um engenheiro de código aberto e começou a Elm Software Foundation.
4. Principal mantedor
    - É seu próprio criador, Evan Czaplicki.
## Instalação e Uso
* Instalação
    - O Elm pode ser instalado no Mac, Windows, Linux (através do npm), a plataforma também disponibiliza um compilador online. Se você for baixar no Mac ou Windows basta fazer o download em: http://elm-lang.org/
    - Para instalar no Linux basta utilizar este comando: 
      *$ npm install -g elm*
    - Após a instalação, você terá as seguintes ferramentas de linha de comando: <br>
      <b>elm-repl</b> - brincar com expressões Elm <br>
      <b>elm-reactor</b> - obter um projeto rapidamente <br>
      <b>elm-make</b> - compilar código Elm diretamente <br>
      <b>elm-package</b> - fazer o download de pacotes <br><br>
    
<pre>
    <b>Ex elm-repl</b>
$ elm-repl
----elm-repl 0.18.0-----------------------------------------------------------
 :help for help, :exit to exit, more at https://github.com/elm-lang/elm-repl
--------------------------------------------------------------------------------
> 1 / 2
0.5 : Float
> List.length [1,2,3,4]
4 : Int 
> String.reverse "stressed"
"desserts" : String
> :exit
$
</pre>
<pre>
   <b>Ex elm-reactor</b>
Ajuda a construir projetos Elm sem mexer com a linha de comando demais. Basta executá-lo na raiz do seu projeto, como este:<br>

git clone https://github.com/evancz/elm-architecture-tutorial.git
cd elm-architecture-tutorial
elm-reactor

Isso inicia um servidor em http://localhost:8000. Você pode navegar para qualquer arquivo Elm e ver o que parece.
</pre>
<pre>
   <b>Ex elm-make</b>
Constrói projetos Elm. Ele pode compilar código para HTML ou JavaScript. É a maneira mais geral de compilar a linguagem, portanto, se seu projeto se tornar muito avançado para elm-reactor, você deve começar a usar elm-make diretamente.
Digamos que você queira compilar Main.elm para um arquivo HTML nomeado main.html. Você executaria este comando:

elm-make Main.elm --output=main.html
</pre>
<pre>
   <b>Ex elm-package</b>
Com esse comando você pode baixar e publicar pacotes do no catálogo de pacotes. 
Digamos que você deseja usar elm-lang/http e NoRedInk/elm-decode-pipeline para fazer solicitações HTTP em um servidor e transformar o JSON resultante em valores Elm. Você diria:
elm-package install elm-lang/http
elm-package install NoRedInk/elm-decode-pipeline

Alguns editores de texto são recomendados pelo Elm, tais como: 
Atom
Brackets
Emacs
IntelliJ
Light Table
Sublime Text
Vim
VS Code
</pre>

## Sintaxe Básica
1. Variaveis e constantes
variavel = valor
*Mesma estrutura para todos os tipos*
2. Operadores relacionais e lógicos
   - <b>not</b> : Bool -> Bool <br>
         Nega um valor boleano. 
         <br><br>
            *not True == False* <br>
            *not False == True* <br><br>
   - <b>(&&)</b> : Bool -> Bool -> Bool <br>
         O operador logico AND. True se ambas entradas forem True.
         <br><br>
        *Note: Quando usado na posição do infixo, como (esquerda && direita), o operador curto-circuita. Isso significa que, se deixado é False, não nos incomodamos em avaliar direito e retornar apenas False global.*<br><br>
   - <b>(||)</b> : Bool -> Bool -> Bool <br>
         O operador logico OR. True se uma ou ambas as entradas forem True.
         <br><br>
        *Note: Quando usado na posição do infixo, como (esquerda && direita), o operador curto-circuita. Isso significa que, se deixado é True, não nos incomodamos em avaliar direito e retornar apenas True global.*<br><br>
   - <b>xor</b> Bool -> Bool -> Bool <br>
        O operador exlusivo.True se exatamente uma entrada for True.<br><br>
3. Operadores aritiméticos
   - <b>(+)</b> : number -> number -> number <br><br>
   - <b>(-)</b> : number -> number -> number <br><br>
   - <b>(*)</b> : number -> number -> number <br><br>
   - <b>(/)</b> : Float -> Float -> Float <br>
       Floating point division.<br><br>
   - <b>(^)</b> : number -> number -> number <br>
       Exponentiation  3^2 == 9<br><br>
   - <b>(//)</b> : Int -> Int -> Int <br>
       Divisão Inteira. O restante é descartado.<br><br>
   - <b>rem</b> : Int -> Int -> Int <br>
       Encontra o restante depois de dividir um número por outro.<br>
        *->	rem 11 4 == 3*<br>
        *-> rem 12 4 == 0*<br>
        *-> rem 13 4 == 1*<br>
        *-> rem -1 4 == -1*<br><br>
   - <b>(%)</b> : Int -> Int -> Int <br>
       Executar aritmética modular <br>
        *-> 7 % 2 == 1<br>
        *-> -1 % 4 == 3<br><br>
   - <b>negate</b> : number -> number <br>
       Um número negativo.<br>
        *-> negate 42 == -42*<br>
        *-> negate -42 == 42*<br>
        *-> negate 0 == 0*<br><br>
   - <b>abs</b> : number -> number <br>
       Pegue o valor absoluto de um número. <br><br>
   - <b>sqrt</b> : Float -> Float <br>
      Pegue a raiz quadrada de um número. <br><br>
   - <b>clamp</b> : number -> number -> number -> number <br>
      Prende um número dentro de um determinado intervalo. Com a expresao [clamp 100 200 x] os resultados são os seguites: <br>
        *-> 100     if x < 100* <br>
        *-> x      if 100 <= x < 200* <br>
        *-> 200     if 200 <= x* <br><br>
   - <b>logBase</b> : Float -> Float -> Float <br>
      Calcula o logaritmo de um numero com um dada base. <br>
        *-> logBase 10 100 == 2* <br>
        *-> logBase 2 256 == 8* <br><br>
   - <b>e</b> : Float <br>
      Uma aproximação de e.<br><br>
4. Estruturas de controle condicional <br>
Declarações if sempre devem ter um else e os valores devem ser do mesmo tipo.
<pre>
if powerLevel > 9000 then
  "WHOA!"
else
  "meh"
</pre>
  Declarações if podem ser encadeadas.
<pre>
if n == 0 then
  "n é zero"
else if n > 0 then
  "n é positivo"
else
  "n é negativo"
</pre>
5. Estruturas de repetiçao
<pre>
sum : List number -> number
sum lst =
  case lst of
    [] ->   0
    (x::xs) -> x + sum(xs)
----------------------------
sum [1,4, 6, 8] -- 19
</pre>
6. Vetor, Matriz e String
   - Strings <br>
      *"Esta é uma string porque ela utiliza aspas duplas."*<br>
      Strings podem ser anexadas.<br>
      *"Olá " ++ "mundo!" -- "Olá mundo!"*<br>
   - Matriz
      Não é possível criar uma matriz com uma sintaxe literal como lista. A maneira mais comum de criar uma matriz é criar primeiro uma lista e transformá-la em uma matriz.
<pre>
myArray = Array.fromList [ 1, 2, 3, 4 ]
</pre>
7. Funções
<pre>
multiply a b =
  a * b
</pre>
Aplica (chama) uma função passando seus argumentos (vírgulas não necessárias).
<pre>
multiply 7 6
</pre>
Aplica parcialmente uma função passando somente alguns de seus argumentos.
<br>Dando, em seguida, um novo nome a função.
<pre>
double =
  multiply 2
</pre>
Passa funções como argumentos para outras funções.
<pre>List.map double [1..4] -- [2, 4, 6, 8]</pre>
Ou escreva uma função anônima.
<pre>List.map (\a -> a * 2) [1..4] -- [2, 4, 6, 8]</pre>
Esta função recebe uma tupla em vez de dois argumentos. <br>
Esta é a maneira que você normalmente vai desempacotar/extrair valores de tuplas.
<pre>
area (width, height) =
  width * height
</pre>
Utilize chaves para casar o padrão de nomes de campos de um registro. <br>
Utilize let para definir valores intermediários.
<pre>
volume {width, height, depth} =
  let
    area = width * height
  in
    area * depth
--------------------------------------------
volume { width = 3, height = 2, depth = 7 } 
</pre>
Funções podem ser recursivas.
*fib n = <br>
  if n < 2 then <br>
    1 <br>
  else <br>
    fib (n - 1) + fib (n - 2)* <br>

