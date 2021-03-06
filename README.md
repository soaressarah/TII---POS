# TII---POS
## COMPONENTES
### Laís Pereira do Nascimento
    Matrícula: 20141011110107  
    Github Nickname: laypereirar
### Sarah Rebecca Soares Penha
    Matrícula: 20141011110182 
    Github Nickname: soaressarah  
### Vanessa Cristiane Santos
    Matrícula: 20141011110034
    Github Nickname: santosvanessa

## LINGUAGEM
  - Elm
 
## RESUMO
### Propósito da linguagem
- O Elm é uma linguagem funcional, fortemente tipada e que compila para JavaScript, HTML e CSS. O principal foco da linguagem é trazer os benefícios (e garantias) da Programação Funcional para o Front-End.
- Por ser uma linguagem compilada, tem chances nulas de erros em tempo de execução.
- Os efeitos colaterais são bem controlados, diferentemente do JavaScript. No JavaScript o erro pode estar em qualquer lugar do código.
    
### Paradigma da Linguagem
- O paradigma da linguagem é funcional, ou seja, baseia-se no conceito matemático de função. Onde para cada entrada (domínio) há somente uma saída (contra-domínio).

### Data de criação
- O Elm foi criado em 2012, por Evan Czaplicki. Em 2013, Czaplicki, juntou-se ao Prezi para trabalhar no Elm, e em 2016 mudou-se para o NoRedInk como um engenheiro de código aberto e começou a Elm Software Foundation.
### Principal mantedor
- Seu próprio criador, Evan Czaplicki.
## INSTALAÇÃO E USO
### Instalação
- O Elm pode ser instalado no Mac, Windows, Linux (através do npm), a plataforma também disponibiliza um [compilador online](http://elm-lang.org/try). 
- Se você for baixar no Mac ou Windows basta fazer o download no [site deles](http://elm-lang.org/)
- Para instalar no Linux basta utilizar este comando: `$ npm install -g elm`
### Uso
Após a instalação, você terá algumas ferramentas de linha de comando: 
**elm-repl**: "Brinca" com expressões
```
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
```
**elm-reactor**: Ajuda a construir projetos Elm sem mexer com a linha de comando demais. Basta executá-lo na raiz do seu projeto como no exemplo a seguir: 
```
git clone https://github.com/evancz/elm-architecture-tutorial.git
cd elm-architecture-tutorial
elm-reactor

Isso inicia um servidor em http://localhost:8000. Você pode navegar para qualquer arquivo Elm e ver o que parece.
```
**elm-make**: Constrói projetos Elm. Ele pode compilar código para HTML ou JavaScript. É a maneira mais geral de compilar a linguagem, portanto, se seu projeto se tornar muito avançado para elm-reactor, você deve começar a usar elm-make diretamente.
```
Digamos que você queira compilar Main.elm para um arquivo HTML nomeado main.html. Você executaria este comando:

elm-make Main.elm --output=main.html
```
**elm-package**: Com esse comando você pode baixar e publicar pacotes do no catálogo de pacotes.
```
elm-package install elm-lang/http
elm-package install NoRedInk/elm-decode-pipeline
```


## SINTAXE BÁSICA
### Varáveis e constantes
Mesma estrutura para todos os tipos: ``` variavel = valor ```
### Operadores relacionais e lógicos
**not**: Nega um valor boleano
``` 
Bool -> Bool 
not True == False 
not False == True 
```

**(&&)**: Operador lógico AND. 
```
Bool -> Bool -> Bool
True se ambas forem true
```
*Observação: Quando usado na posição do infixo, como (esquerda && direita), o operador curto-circuita. Isso significa que, se deixado é False, não nos incomodamos em avaliar direito e retorna apenas False global.* 

**(||)**: Operador logico OR.
```
Bool -> Bool -> Bool
True se uma ou ambas as entradas forem True.
```
*Observação: Quando usado na posição do infixo, como (esquerda && direita), o operador curto-circuita. Isso significa que, se deixado é True, não nos incomodamos em avaliar direito e retorna apenas True global.*

**xor**: Operador exclusivo.
```
Bool -> Bool -> Bool
True se exatamente uma entrada for True.
```
### Operadores aritméticos
**(+)**: Soma
```number -> number -> number```
**(-)**: Subtração 
```number -> number -> number```
**( * )**: Multiplicação
```number -> number -> number ```
**(/)**: Divisão.
```Float -> Float -> Float .```
**(^)**: Exponenciação. 
```
number -> number -> number.
Exemplo: 3^2 == 9
```
**(//)**: Divisão Inteira. O resto da divisão é descartado.
```Int -> Int -> Int.```
**rem** : Encontra o restante depois de dividir um número por outro.
```
Int -> Int -> Int 
Exemplos:
->	rem 11 4 == 3
-> rem 12 4 == 0
-> rem 13 4 == 1
-> rem -1 4 == -1
```
**(%)**: Executa aritmética modular
```
Int -> Int -> Int 
Exemplos:
-> 7 % 2 == 1
-> -1 % 4 == 3
```
**negate**: Negativo do número.
```
number -> number 
Exemplos:
-> negate 42 == -42
-> negate -42 == 42
-> negate 0 == 0
```
**abs**: Pega o valor absoluto do número
```number -> number ```

**sqrt**: Pega a raiz quadrada de um número.
```Float -> Float```

**clamp**: Prende um número dentro de um determinado intervalo.
```
number -> number -> number -> number 
Exemplo:
Com a expresao [clamp 100 200 x] os resultados são os seguites: 
-> 100 if x < 100 
-> x if 100 <= x < 200 
-> 200 if 200 <= x 
```

**logBase**: Calcula o logaritmo de um número com uma dada base.
```
Float -> Float -> Float 
Exemplos:
-> logBase 10 100 == 2 
-> logBase 2 256 == 8 
```
**e**: Uma aproximação de e.
``` Float ```
##### Estruturas de controle condicional
Declarações if sempre devem ter um else e os valores devem ser do mesmo tipo.
``` 
if powerLevel > 9000 then
  "WHOA!"
else
  "meh"
```

Declarações if podem ser encadeadas.
```
if n == 0 then
  "n é zero"
else if n > 0 then
  "n é positivo"
else
  "n é negativo"
```
### Estruturas de repetição

```
sum : List number -> number
sum lst =
  case lst of
    [] ->   0
    (x::xs) -> x + sum(xs)
----------------------------
sum [1,4, 6, 8] -- 19
```
### Vetores, matrizes e strings
**Strings**
``` "Esta é uma string porque ela utiliza aspas duplas." ```
Strings podem ser anexadas: ```"Olá " ++ "mundo!" -- "Olá mundo!"```
**Vetor** 
Não é possível criar um vetor com uma sintaxe literal como lista. A maneira mais comum de criar um vetor é criar primeiro uma lista e transforma-la em um vetor
``` myArray = Array.fromList [ 1, 2, 3, 4 ] ```
**Matriz**
``` array2d =
    Array2D.fromList
      [ ["Row 1-Col 1", "Row 1-Col 2"]
      , ["Row 2-Col 1", "Row 2-Col 2"]
      ] ```
**Funções**
```
multiply a b =
  a * b
```
Aplica (chama) uma função passando seus argumentos (vírgulas não necessárias).
```
multiply 7 6
```
Aplica parcialmente uma função passando somente alguns de seus argumentos. 
Dando, em seguida, um novo nome a função.
```
double =
  multiply 2
```
Passa funções como argumentos para outras funções.
```
List.map double [1..4] -- [2, 4, 6, 8]
```
Ou escreva uma função anônima.
```
List.map (\a -> a * 2) [1..4] -- [2, 4, 6, 8]
```
Esta função recebe uma tupla em vez de dois argumentos. 
Esta é a maneira que você normalmente vai desempacotar/extrair valores de tuplas.
```
area (width, height) =
  width * height
```
Utilize chaves para casar o padrão de nomes de campos de um registro. 
Utilize let para definir valores intermediários.
```
volume {width, height, depth} =
  let
    area = width * height
  in
    area * depth
--------------------------------------------
volume { width = 3, height = 2, depth = 7 } 
```
## SINTAXE OO
- O ELM não possui sintaxe OO. Ou seja, não há o conceito de objeto, método, classe e etc.

## SINTAXE FUNCIONAL
Elm é uma linguagem inteiramente funcional, onde sua sintaxe é basicamente composta por funções puras (dado um parâmetro, o retorno será sempre o mesmo. Além de não gerar efeito colateral)
### Função básica
``` 
--add -> nome da função
--a b -> argumentos
--a + b -> corpo da função
    add a b = a + b
--Não é necessário um return
--Para chamar: nomeDaFunção paramêtros
    add 1 2
```
### Anotações de tipo
Informa o tipo de entrada e saída de uma função. Muito recomendado pelo Elm, pois permite escrever melhor as funções e as restringir ainda mais.
```
NomeDaFunção : argumento -> argumento -> retorno
add: Int -> Int -> Int

--a função update recebe uma mensagem e o model como argumento e retorna um novo model
update: Msg -> Model -> Model
```

### Função Recursiva
Quando uma função pode invocar a si mesma. Serve como uma estrutura de repetição.
```
fib n = 
if n < 2 then 
1 
else 
fib (n - 1) + fib (n - 2) 
```
