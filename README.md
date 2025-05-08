# Linguagem APS - Documentação e Guia de Uso
## Feito por Pedro Drumond e Douglas Bracale
## Introdução à Linguagem APS

A Linguagem APS é uma linguagem de programação criada com o objetivo de facilitar o aprendizado de conceitos básicos de programação e compiladores. Inspirada em sintaxes claras e utilizando palavras-chave em português, a linguagem permite que os usuários escrevam programas de forma intuitiva e próxima da linguagem natural.

### Características Principais
- Sintaxe em Português: Utiliza palavras-chave em português, tornando o código mais acessível para falantes da língua.
- Estruturas de Controle: Suporte a condicionais, loops e funções, permitindo a criação de programas complexos.
- Tipos de Dados Simples: Suporte a tipos básicos como INT, STR e BOOL.
- Operadores Aritméticos e Relacionais: Permite realizar operações matemáticas e lógicas.

### Palavras-chave Utilizadas
- Declaração de Variáveis: `INT`, `STR`, `BOOL`
- Atribuição: `RECEBE`
- Condicional: `SE`, `ENTAO`, `SENAO`, `FIMSE`
- Loop Enquanto: `ENQUANTO`, `FACA`, `FIMENQUANTO`
- Loop Para: `PARA`, `DE`, `ATE`, `PASSO`, `FACA`, `FIMPARA`
- Funções: `FUNCAO`, `RETORNA`
- Entrada/Saída: `LEIA`, `IMPRIME`
- Operadores Relacionais: `IGUAL`, `DIFERENTE`, `MAIOR`, `MENOR`, `MAIORIGUAL`, `MENORIGUAL`
- Operadores Aritméticos: `+`, `-`, `*`, `/`

## Gramática da Linguagem APS em EBNF

A seguir, apresentamos a gramática formal da Linguagem APS, definida em Extended Backus-Naur Form (EBNF). Correções foram feitas para garantir a consistência e completude da gramática.

    <Programa>          ::= { <Comando> }

    <Comando>           ::= <DeclaracaoVariavel> | <DeclaracaoFuncao> | <Atribuicao> | <Condicional> | <LoopEnquanto> | <LoopPara> | <Impressao> | <Leitura> | <Retorno> | <Comentario>

    <DeclaracaoVariavel> ::= <DeclaracaoUnica> { "," <DeclaracaoUnica> } ";"

    <DeclaracaoUnica>    ::= <Tipo> <Identificador> [ "RECEBE" <Expressao> ]

    <DeclaracaoFuncao> ::= "FUNCAO" <Tipo> <Identificador> "(" [ <ListaParametros> ] ")" <Bloco>

    <ListaParametros>   ::= <Parametro> { "," <Parametro> }

    <Parametro>         ::= <Tipo> <Identificador>

    <Tipo>              ::= "INT" | "STR" | "BOOL"

    <Atribuicao>        ::= <Identificador> "RECEBE" <Expressao> ";"

    <Condicional>       ::= "SE" <Condicao> "ENTAO" <Bloco> [ "SENAO" <Bloco> ] "FIMSE"

    <LoopEnquanto>      ::= "ENQUANTO" <Condicao> "FACA" <Bloco> "FIMENQUANTO"

    <LoopPara>          ::= "PARA" <Identificador> "DE" <Expressao> "ATE" <Expressao> [ "PASSO" <Expressao> ] "FACA" <Bloco> "FIMPARA"

    <Impressao>         ::= "IMPRIME" <Expressao> ";"

    <Leitura>           ::= "LEIA" <Identificador> ";"

    <Retorno>           ::= "RETORNA" <Expressao> ";"

    <Bloco>             ::= "{" { <Comando> } "}"

    <Expressao>         ::= <Termo> { ("+" | "-") <Termo> }

    <Termo>             ::= <Fator> { ("*" | "/") <Fator> }

    <Fator>             ::= <Número> | <String> | <Identificador> | "(" <Expressao> ")" | <ChamadaFuncao> | <OperadorUnario> <Fator>

    <ChamadaFuncao>     ::= <Identificador> "(" [ <ListaArgumentos> ] ")"

    <ListaArgumentos>   ::= <Expressao> { "," <Expressao> }

    <Condicao>          ::= <Expressao> <OperadorRelacional> <Expressao>

    <OperadorRelacional>::= "IGUAL" | "DIFERENTE" | "MAIOR" | "MENOR" | "MAIORIGUAL" | "MENORIGUAL"

    <OperadorUnario>    ::= "+" | "-" | "!"

    <Identificador>     ::= <Letra> { <Letra> | <Digito> | "_" }

    <Número>            ::= <Digito> { <Digito> }

    <String>            ::= '"' { <Caractere> } '"'

    <Comentario>        ::= "#" { <QualquerCaractereExcetoNovaLinha> }

    <Letra>             ::= "A" | ... | "Z" | "a" | ... | "z"

    <Digito>            ::= "0" | ... | "9"

    <QualquerCaractereExcetoNovaLinha> ::= qualquer caractere exceto "\n"

    <Caractere>         ::= qualquer caractere exceto '"'

## Explicação da Gramática com Exemplos

### Declaração de Variáveis
Para declarar variáveis, utilizamos os tipos `INT`, `STR` ou `BOOL`, seguidos do nome da variável. Podemos opcionalmente inicializá-las usando `RECEBE`. Exemplo:
```c
INT a;
STR nome RECEBE "João";
BOOL ativo RECEBE 1;
INT x RECEBE 10, INT y RECEBE 20, INT resultado;
```

### Atribuição
Utilizamos `RECEBE` para atribuir um valor a uma variável já declarada. Exemplo:
```c
x RECEBE y + 5;
```

### Expressões Matemáticas
Usamos operadores aritméticos tradicionais para realizar operações matemáticas: `+`, `-`, `*`, `/`. Exemplo:
```c
resultado RECEBE x * y;
```

### Estruturas de Controle

#### Condicionais

Utilizamos `SE`, `ENTAO`, `SENAO` e `FIMSE` para criar estruturas condicionais. O bloco de código é definido entre `{` e `}`. Exemplo:
```c
SE x MAIOR y ENTAO
{
    IMPRIME "x é maior que y";
}
SENAO
{
    IMPRIME "x é menor ou igual a y";
}
FIMSE
```

#### Loop Enquanto
Utilizamos `ENQUANTO`, `FACA` e `FIMENQUANTO` para criar loops que repetem enquanto a condição for verdadeira. Exemplo:
```c
INT contador RECEBE 0;
ENQUANTO contador MENOR 10 FACA
{
    IMPRIME contador;
    contador RECEBE contador + 1;
}
FIMENQUANTO
```

#### Loop Para
Utilizamos `PARA`, `DE`, `ATE`, `PASSO`, `FACA` e `FIMPARA` para criar loops com iteração controlada. Exemplo:

```c
PARA i DE 1 ATE 5 FACA
{
    IMPRIME i;
}
FIMPARA
```

### Funções
Definimos funções usando `FUNCAO`, especificando o tipo de retorno, o nome da função e os parâmetros. Utilizamos `RETORNA` para retornar um valor. Exemplo:

```c
FUNCAO INT somar(INT a, INT b)
{
    RETORNA a + b;
}
```

### Entrada e Saída
#### Impressão
Utilizamos `IMPRIME` para exibir valores ou mensagens na tela. Exemplo:
```c
IMPRIME "O resultado é: " + resultado;
```

#### Leitura
Utilizamos `LEIA` para ler um valor da entrada padrão e atribuí-lo a uma variável. Exemplo:
```c
LEIA nome;
```

### Comentários
Podemos adicionar comentários ao código iniciando a linha com `#`. O compilador ignorará tudo que estiver após o `#` até o fim da linha.
```py
# Este é um comentário
```

## Como Executar o Compilador
1. **Escolha um Programa APS:** Utilize um dos exemplos fornecidos na pasta programas ou crie seu próprio programa com a extensão .aps

2. **Execute o Compilador:** Abra o terminal ou prompt de comando, navegue até o diretório do compilador e execute:

`python main.py .\programas\nome_do_programa.aps`

Exemplo:

`python main.py .\programas\programa.aps`

## Exemplo de Código

```py
INT a RECEBE 10, INT b RECEBE 20, INT resultado;

FUNCAO INT somar(INT x, INT y) {
    RETORNA x + y;
}

resultado RECEBE somar(a, b);

IMPRIME "O resultado da soma é: " + resultado;

# Loop enquanto
INT contador RECEBE 1;
ENQUANTO contador MENORIGUAL 5 FACA {
    IMPRIME "Contador: " + contador;
    contador RECEBE contador + 1;
}
FIMENQUANTO

# Loop para
PARA INT i DE 1 ATE 5 FACA {
    IMPRIME "i = " + i;
}
FIMPARA

# Condicional
SE resultado MAIOR 100 ENTAO {
    IMPRIME "Resultado é maior que 100";
} SENAO {
    IMPRIME "Resultado é menor ou igual a 100";
}
FIMSE
```
