# 15 — Funcoes: Conceitos de Entrada e Saida

[<- Anterior: Controles de Repeticao](14-controles-repeticao.md) | [Glossario](00-glossario.md) | [Proximo: Exercicios de Logica ->](16-exercicios-logica.md)

---

## Introducao

Ate agora, todo o codigo que voce escreveu fica em um unico bloco, executado de cima para baixo. Conforme seus programas crescem, voce vai perceber que repete trechos de codigo em varios lugares. Copiar e colar o mesmo codigo varias vezes e trabalhoso, propenso a erros e dificil de manter.

Funcoes resolvem esse problema. Uma **funcao** e um bloco de codigo reutilizavel que voce escreve uma vez e pode usar quantas vezes quiser. E como uma **receita de cozinha**: voce escreve a receita uma vez e pode segui-la sempre que quiser preparar aquele prato, sem precisar reinventar os passos toda vez.

Esse principio tem um nome em programacao: **DRY** — "Don't Repeat Yourself" (Nao Se Repita). Em vez de repetir codigo, crie uma funcao.

> **Dica:** Consulte o [Glossario](00-glossario.md) sempre que encontrar um termo desconhecido.

---

## Como Executar os Exemplos Deste Modulo

1. Copie o codigo e cole em um novo arquivo no VSCode
2. Salve na pasta `~/meus-projetos/python-curso/modulo-15/`
3. No terminal: `cd ~/meus-projetos/python-curso/modulo-15`
4. Execute: `python3 nome_do_arquivo.py`

---

## Criando uma Funcao com def

Em Python, voce cria uma funcao usando a palavra-chave `def` (abreviacao de "define" — definir em ingles), seguida do nome da funcao e parenteses:

```python
# Definindo uma funcao simples
# def = define (criar/definir uma funcao)
# "greet" = saudar/cumprimentar
def greet():
    # Este bloco e o corpo da funcao — executa quando a funcao e chamada
    print("Ola! Bem-vindo ao sistema.")
    print("Tenha um otimo dia!")

# A funcao foi definida, mas ainda nao executou
# Para executar, precisamos CHAMAR a funcao pelo nome seguido de ()
greet()

# Podemos chamar quantas vezes quisermos
greet()
```

**Saida esperada:**
```
Ola! Bem-vindo ao sistema.
Tenha um otimo dia!
Ola! Bem-vindo ao sistema.
Tenha um otimo dia!
```

> **Nota:** Definir uma funcao (com `def`) nao executa o codigo dentro dela. O codigo so executa quando voce **chama** a funcao pelo nome seguido de parenteses: `greet()`.

### Anatomia de uma funcao

```
def nome_da_funcao(parametros):    <-- definicao: nome + parametros
    instrucao_1                    <-- corpo: codigo indentado
    instrucao_2                    <-- executa quando a funcao e chamada
    return resultado               <-- (opcional) retorna um valor

nome_da_funcao(argumentos)         <-- chamada: executa a funcao
```

---

## Parametros e Argumentos

Parametros sao variaveis que a funcao recebe quando e chamada. Eles permitem que a funcao trabalhe com dados diferentes a cada chamada.

Pense assim: a funcao e uma maquina de suco. Os **parametros** sao os espacos onde voce coloca as frutas. Os **argumentos** sao as frutas que voce realmente coloca.

```python
# Funcao com parametro
# "name" e o parametro — uma variavel que recebe um valor quando a funcao e chamada
# "greet_person" = saudar pessoa
def greet_person(name):
    # "name" = nome — recebe o valor passado na chamada
    print(f"Ola, {name}! Seja bem-vindo(a)!")

# Chamando a funcao com diferentes argumentos
# "Maria" e o argumento — o valor real passado para o parametro "name"
greet_person("Maria")
greet_person("Carlos")
greet_person("Ana")
```

**Saida esperada:**
```
Ola, Maria! Seja bem-vindo(a)!
Ola, Carlos! Seja bem-vindo(a)!
Ola, Ana! Seja bem-vindo(a)!
```

### Multiplos parametros

```python
# Funcao com dois parametros
# "product_name" = nome do produto, "price" = preco
# "display_product" = exibir produto
def display_product(product_name, price):
    print(f"Produto: {product_name} — Preco: R$ {price}")

# Chamando com dois argumentos (na mesma ordem dos parametros)
display_product("Arroz", 5.99)
display_product("Feijao", 8.50)
```

**Saida esperada:**
```
Produto: Arroz — Preco: R$ 5.99
Produto: Feijao — Preco: R$ 8.50
```

> **Nota:** A ordem dos argumentos importa! O primeiro argumento vai para o primeiro parametro, o segundo para o segundo, e assim por diante.

---

## return — Retornando Valores

Ate agora, nossas funcoes apenas exibiam coisas com `print()`. Mas funcoes tambem podem **calcular e devolver um resultado** usando `return`.

Pense na funcao como uma maquina: voce coloca ingredientes (argumentos), a maquina processa, e devolve o produto final (return).

```python
# Funcao que calcula e RETORNA um resultado
# "calculate_double" = calcular o dobro
# "number" = numero (parametro)
def calculate_double(number):
    # Calculamos o dobro
    # "result" = resultado
    result = number * 2
    # return devolve o resultado para quem chamou a funcao
    return result

# Chamamos a funcao e guardamos o resultado em uma variavel
# "my_double" = meu dobro
my_double = calculate_double(7)
print(f"O dobro de 7 e {my_double}")

# Podemos usar o resultado diretamente no print
print(f"O dobro de 15 e {calculate_double(15)}")
```

**Saida esperada:**
```
O dobro de 7 e 14
O dobro de 15 e 30
```

### Funcoes com return vs funcoes sem return

| Tipo | Descricao | Exemplo |
|------|-----------|---------|
| Com return | Calcula e devolve um valor | `def soma(a, b): return a + b` |
| Sem return | Apenas executa acoes (print, etc.) | `def saudar(): print("Ola")` |

Funcoes sem `return` retornam `None` automaticamente.

```python
# Funcao que calcula a soma de dois numeros
# "add" = somar/adicionar
def add(number_a, number_b):
    # "total" = total (soma)
    total = number_a + number_b
    # return devolve o total para quem chamou
    return total

# Usando o resultado da funcao
# "result" = resultado
result = add(10, 5)
print(f"10 + 5 = {result}")

# Podemos usar em expressoes
# "final_price" = preco final
final_price = add(100, 50) * 0.9  # soma e aplica 10% de desconto
print(f"Preco com desconto: R$ {final_price}")
```

**Saida esperada:**
```
10 + 5 = 15
Preco com desconto: R$ 135.0
```

---

## Valores Padrao de Parametros

Voce pode definir valores padrao para parametros. Se o argumento nao for passado na chamada, o valor padrao e usado:

```python
# Funcao com valor padrao no parametro
# "discount_percent" tem valor padrao 10 — se nao for passado, usa 10
# "calculate_discount" = calcular desconto
def calculate_discount(price, discount_percent=10):
    # "price" = preco, "discount_percent" = porcentagem de desconto
    # "discount_value" = valor do desconto
    discount_value = price * (discount_percent / 100)
    # "final_price" = preco final
    final_price = price - discount_value
    return final_price

# Chamando sem o segundo argumento — usa o padrao (10%)
print(f"Com 10% (padrao): R$ {calculate_discount(100)}")

# Chamando com o segundo argumento — usa o valor passado (20%)
print(f"Com 20%: R$ {calculate_discount(100, 20)}")
```

**Saida esperada:**
```
Com 10% (padrao): R$ 90.0
Com 20%: R$ 80.0
```

> **Nota:** Parametros com valor padrao devem vir **depois** dos parametros sem valor padrao. `def funcao(a, b=10):` esta correto. `def funcao(a=10, b):` gera erro.

---

## Escopo de Variaveis — Local vs Global

O [escopo](00-glossario-e-i.md#escopo-de-variavel) define onde uma variavel existe e pode ser acessada. Em Python, existem dois escopos principais:

- **Escopo local**: variaveis criadas dentro de uma funcao. So existem dentro daquela funcao.
- **Escopo global**: variaveis criadas fora de funcoes. Podem ser acessadas em qualquer lugar.

Pense assim: objetos dentro de um quarto (escopo local) so existem dentro daquele quarto. Objetos na sala (escopo global) podem ser vistos de qualquer comodo da casa.

```python
# Variavel global — criada fora de qualquer funcao
# "global_message" = mensagem global
global_message = "Eu sou global!"

def my_function():
    # Variavel local — criada dentro da funcao
    # "local_message" = mensagem local
    local_message = "Eu sou local!"

    # Dentro da funcao, podemos acessar AMBAS
    print(f"Dentro da funcao: {global_message}")
    print(f"Dentro da funcao: {local_message}")

# Chamamos a funcao
my_function()

# Fora da funcao, so podemos acessar a global
print(f"Fora da funcao: {global_message}")

# Tentar acessar a variavel local fora da funcao gera erro:
# print(local_message)  # NameError: name 'local_message' is not defined
```

**Saida esperada:**
```
Dentro da funcao: Eu sou global!
Dentro da funcao: Eu sou local!
Fora da funcao: Eu sou global!
```

> **Dica:** Evite depender de variaveis globais dentro de funcoes. Prefira passar valores como parametros — isso torna a funcao mais independente e reutilizavel.

---

## Exemplos Praticos

### Exemplo 1: Funcao de validacao

```python
# Funcao que valida se uma idade e valida
# "validate_age" = validar idade
# Retorna True se valida, False se invalida
def validate_age(age):
    # "age" = idade
    # Idade valida: entre 0 e 150
    if age >= 0 and age <= 150:
        return True
    else:
        return False

# Usando a funcao
# "user_age" = idade do usuario
user_age = int(input("Digite sua idade: "))

if validate_age(user_age):
    print(f"Idade {user_age} registrada com sucesso!")
else:
    print("Idade invalida! Digite um valor entre 0 e 150.")
```

### Exemplo 2: Funcao de calculo de preco

```python
# Funcao que calcula o preco total com quantidade e desconto
# "calculate_total" = calcular total
def calculate_total(unit_price, quantity, discount_percent=0):
    # "unit_price" = preco unitario
    # "quantity" = quantidade
    # "discount_percent" = porcentagem de desconto (padrao: 0)

    # "subtotal" = subtotal (preco x quantidade)
    subtotal = unit_price * quantity

    # "discount" = valor do desconto
    discount = subtotal * (discount_percent / 100)

    # "total" = total final
    total = subtotal - discount

    return total

# Usando a funcao em diferentes cenarios
print(f"Sem desconto: R$ {calculate_total(10, 5)}")
print(f"Com 15% desconto: R$ {calculate_total(10, 5, 15)}")
print(f"Com 50% desconto: R$ {calculate_total(10, 5, 50)}")
```

**Saida esperada:**
```
Sem desconto: R$ 50.0
Com 15% desconto: R$ 42.5
Com 50% desconto: R$ 25.0
```

---

## Resumo

| Conceito | Descricao | Exemplo |
|----------|-----------|---------|
| `def nome():` | Define uma funcao | `def greet():` |
| Parametro | Variavel na definicao | `def greet(name):` |
| Argumento | Valor na chamada | `greet("Maria")` |
| `return` | Devolve um resultado | `return total` |
| Valor padrao | Parametro com valor pre-definido | `def f(x=10):` |
| Escopo local | Variavel dentro da funcao | So existe na funcao |
| Escopo global | Variavel fora de funcoes | Acessivel em todo lugar |

---

## Para Saber Mais

- [W3Schools — Python Functions](https://www.w3schools.com/python/python_functions.asp) — _Funcoes em Python_
- [W3Schools — Python Scope](https://www.w3schools.com/python/python_scope.asp) — _Escopo de variaveis_
- [Documentacao Python — Funcoes](https://docs.python.org/pt-br/3/tutorial/controlflow.html#defining-functions) — _Referencia oficial_

---

## Perguntas Frequentes (FAQ)

**P: O que e uma funcao?**
R: E um bloco de codigo reutilizavel que realiza uma tarefa especifica. Voce define uma vez com `def` e pode chamar quantas vezes quiser. E como uma receita que voce escreve uma vez e usa varias vezes.

**P: Qual a diferenca entre parametro e argumento?**
R: Parametro e a variavel na definicao da funcao: `def somar(a, b)` — `a` e `b` sao parametros. Argumento e o valor passado na chamada: `somar(5, 3)` — `5` e `3` sao argumentos. Na pratica, muitas pessoas usam os termos como sinonimos.

**P: Preciso sempre usar return?**
R: Nao. Use `return` quando a funcao precisa devolver um resultado para ser usado depois. Se a funcao apenas executa acoes (como exibir mensagens), nao precisa de `return`.

**P: O que acontece se eu nao usar return?**
R: A funcao retorna `None` automaticamente. `None` e o valor que significa "nada" em Python.

**P: Posso ter mais de um return na mesma funcao?**
R: Sim! Mas apenas o primeiro `return` executado encerra a funcao. E comum ter returns dentro de `if/else` para retornar valores diferentes dependendo da condicao.

**P: O que e "chamar" uma funcao?**
R: E executar a funcao escrevendo seu nome seguido de parenteses: `minha_funcao()`. Sem os parenteses, voce esta apenas referenciando a funcao, nao executando.

**P: Posso chamar uma funcao dentro de outra funcao?**
R: Sim! Isso e muito comum. Uma funcao pode chamar outras funcoes para dividir o trabalho em partes menores.

**P: O que e DRY?**
R: "Don't Repeat Yourself" (Nao Se Repita). E um principio que diz: se voce esta copiando e colando codigo, provavelmente deveria criar uma funcao. Codigo repetido e dificil de manter — se precisar mudar algo, tem que mudar em todos os lugares.

**P: O que e escopo?**
R: E a regiao do codigo onde uma variavel existe. Variaveis criadas dentro de uma funcao (escopo local) so existem ali. Variaveis criadas fora (escopo global) existem em todo o programa. E como objetos dentro de um quarto vs objetos na sala.

**P: Posso acessar uma variavel global dentro de uma funcao?**
R: Sim, voce pode ler variaveis globais dentro de funcoes. Mas se tentar modificar uma variavel global dentro de uma funcao, o Python cria uma variavel local com o mesmo nome. Para modificar a global, use a palavra-chave `global` — mas evite isso, prefira parametros.

**P: O que e `global`?**
R: E uma palavra-chave que permite modificar uma variavel global dentro de uma funcao. Exemplo: `global contador`. Mas usar `global` e considerado ma pratica na maioria dos casos — prefira passar valores como parametros e usar return.

**P: Posso ter uma funcao sem parametros?**
R: Sim! `def saudar(): print("Ola")` e uma funcao sem parametros. Os parenteses vazios `()` sao obrigatorios tanto na definicao quanto na chamada.

**P: O que sao valores padrao de parametros?**
R: Sao valores pre-definidos que o parametro assume quando nenhum argumento e passado. `def funcao(x=10):` — se voce chamar `funcao()`, x sera 10. Se chamar `funcao(5)`, x sera 5.

**P: Posso retornar mais de um valor?**
R: Sim! Use virgula: `return a, b`. O Python retorna uma tupla (que vamos aprender no modulo 19). Para receber: `x, y = minha_funcao()`.

**P: O que e "recursao"?**
R: E quando uma funcao chama a si mesma. E um conceito avancado que nao vamos aprofundar neste curso. Exemplo classico: calcular fatorial com recursao. Por enquanto, use loops.

**P: Posso definir uma funcao dentro de outra?**
R: Sim, Python permite. Mas e um recurso avancado. Para iniciantes, defina todas as funcoes no nivel principal do programa.

**P: A ordem das funcoes importa?**
R: Sim! Voce precisa definir a funcao ANTES de chama-la. Se chamar uma funcao que ainda nao foi definida, o Python mostra `NameError`. Coloque as definicoes de funcoes no inicio do arquivo.

**P: Posso usar o mesmo nome para uma funcao e uma variavel?**
R: Tecnicamente sim, mas e uma pessima ideia. O segundo uso sobrescreve o primeiro. Se voce criar uma variavel `print = 5`, a funcao `print()` para de funcionar. Use nomes diferentes e descritivos.

**P: O que e `pass` dentro de uma funcao?**
R: `pass` e um placeholder que nao faz nada. Util quando voce quer definir uma funcao mas ainda nao escreveu o corpo: `def minha_funcao(): pass`. Evita o `IndentationError`.

**P: E normal achar funcoes confusas no inicio?**
R: Sim, funcoes sao um salto conceitual importante. A ideia de "definir agora, executar depois" e de "passar valores e receber resultados" leva um tempo para se tornar natural. Pratique bastante com os exercicios — cada funcao que voce escreve fortalece esse entendimento.

---

## Exercicios de Fixacao

Os exercicios deste modulo estao em um arquivo separado. Este e um modulo complexo — os exercicios sao mais numerosos e progressivos.

**[Acessar Exercicios do Modulo 15](15-funcoes-exercicios.md)**

---

[<- Anterior: Controles de Repeticao](14-controles-repeticao.md) | [Glossario](00-glossario.md) | [Proximo: Exercicios de Logica ->](16-exercicios-logica.md)
