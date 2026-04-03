# 14 — Controles de Repeticao: for e while

[<- Anterior: Seletores match/case](13-seletores-match-case.md) | [Glossario](00-glossario.md) | [Proximo: Funcoes ->](15-funcoes.md)

---

## Introducao

Ate agora, cada instrucao do seu programa executa apenas uma vez. Mas e se voce precisar repetir uma acao varias vezes? Por exemplo: exibir os numeros de 1 a 100, somar todos os itens de uma lista de compras, ou pedir ao usuario que digite dados ate que ele decida parar.

Fazer isso manualmente (escrevendo 100 linhas de print) seria impraticavel. Para isso existem os **loops** (lacos de repeticao) — estruturas que repetem um bloco de codigo automaticamente.

Pense nos loops como dar voltas em uma pista de corrida. Cada volta e uma **iteracao** (repeticao). Voce continua dando voltas ate completar o numero desejado (loop `for`) ou ate cansar (loop `while`).

Neste modulo, vamos aprender dois tipos de loop:
- **for** — repete um numero definido de vezes ou para cada item de uma colecao
- **while** — repete enquanto uma condicao for verdadeira

> **Dica:** Este modulo depende dos modulos 10 (indentacao), 11 (operadores) e 12 (condicionais). Revise-os se necessario.

---

## Como Executar os Exemplos Deste Modulo

1. Copie o codigo e cole em um novo arquivo no VSCode
2. Salve na pasta `~/meus-projetos/python-curso/modulo-14/`
3. No terminal: `cd ~/meus-projetos/python-curso/modulo-14`
4. Execute: `python3 nome_do_arquivo.py`

---

## Termos Importantes

Antes de comecar, vamos explicar alguns termos que aparecem muito quando falamos de loops:

- **Iteracao** (do ingles "iteration"): cada repeticao do loop. Se o loop executa 5 vezes, ele faz 5 iteracoes. E como cada volta que voce da em uma pista de corrida.

- **Contador** (do ingles "counter"): uma variavel que conta quantas vezes algo aconteceu. Comeca em um valor (geralmente 0) e aumenta a cada iteracao. E como contar nos dedos.

- **Incremento** (do ingles "increment"): a acao de aumentar o valor de uma variavel, geralmente de 1 em 1. E como subir um degrau de cada vez em uma escada.

- **Acumulador** (do ingles "accumulator"): uma variavel que vai somando valores ao longo do loop. E como um cofrinho onde voce coloca moedas a cada volta — no final, tem o total acumulado.

---

## Loop for — Repetir para Cada Item

O loop `for` repete um bloco de codigo **para cada item** de uma sequencia (lista, string, range). E o loop mais usado em Python.

### for com range() — Repetir um numero de vezes

A funcao `range()` gera uma sequencia de numeros. Combinada com `for`, permite repetir algo um numero especifico de vezes:

```python
# Repetindo 5 vezes usando for com range()
# range(5) gera os numeros: 0, 1, 2, 3, 4
# "i" e a variavel que recebe cada numero a cada iteracao (volta)
# "i" vem de "index" (indice) — e uma convencao comum em programacao
for i in range(5):
    # Este bloco executa 5 vezes (uma para cada numero de 0 a 4)
    print(f"Iteracao {i}")
```

**Saida esperada:**
```
Iteracao 0
Iteracao 1
Iteracao 2
Iteracao 3
Iteracao 4
```

> **Nota:** `range(5)` gera numeros de 0 ate 4 (5 numeros no total). O numero 5 nao e incluido. E como a regra do fatiamento de strings: o fim nao e incluido.

### range() com inicio e fim

Voce pode especificar onde comecar e onde terminar:

```python
# range(inicio, fim) — gera numeros de inicio ate fim-1
# Contando de 1 a 10
for number in range(1, 11):
    # "number" = numero — recebe cada valor de 1 a 10
    print(number, end=" ")
```

**Saida esperada:**
```
1 2 3 4 5 6 7 8 9 10 
```

### range() com passo

Voce pode definir o incremento (passo) entre os numeros:

```python
# range(inicio, fim, passo) — pula de "passo" em "passo"
# Contando de 0 a 20 de 2 em 2 (numeros pares)
# "step" = passo
for number in range(0, 21, 2):
    print(number, end=" ")
```

**Saida esperada:**
```
0 2 4 6 8 10 12 14 16 18 20 
```

```python
# Contagem regressiva: passo negativo
for number in range(10, 0, -1):
    # range(10, 0, -1) gera: 10, 9, 8, ..., 1
    print(number, end=" ")
print("Fogo!")
```

**Saida esperada:**
```
10 9 8 7 6 5 4 3 2 1 Fogo!
```

### for com strings — Percorrendo cada caractere

```python
# Percorrendo cada caractere de uma string
# "word" = palavra
word = "Python"

# "char" = caractere (abreviacao de character)
# A cada iteracao, char recebe o proximo caractere da string
for char in word:
    print(char)
```

**Saida esperada:**
```
P
y
t
h
o
n
```

### for com listas — Percorrendo cada item

```python
# Percorrendo cada item de uma lista
# "fruits" = frutas
fruits = ["maca", "banana", "laranja", "uva"]

# "fruit" = fruta — recebe cada item da lista a cada iteracao
for fruit in fruits:
    print(f"Eu gosto de {fruit}")
```

**Saida esperada:**
```
Eu gosto de maca
Eu gosto de banana
Eu gosto de laranja
Eu gosto de uva
```

> **Nota:** Listas serao aprofundadas no modulo 19. Por enquanto, saiba que uma lista e uma colecao de itens entre colchetes `[]`, separados por virgula.

---

## Loop while — Repetir Enquanto uma Condicao For Verdadeira

O loop `while` repete um bloco **enquanto** uma condicao for verdadeira. Quando a condicao se torna falsa, o loop para.

Pense assim: "enquanto a panela nao estiver fervendo, continue mexendo". Voce nao sabe quantas vezes vai mexer — depende de quando a agua ferver.

```python
# Contando de 1 a 5 com while
# "counter" = contador — comeca em 1
counter = 1

# while verifica a condicao antes de cada iteracao
# Enquanto counter for <= 5, o bloco executa
while counter <= 5:
    print(f"Contagem: {counter}")
    # Incrementamos o contador em 1 a cada iteracao
    # Sem isso, o loop nunca pararia (loop infinito!)
    counter = counter + 1

print("Fim da contagem!")
```

**Saida esperada:**
```
Contagem: 1
Contagem: 2
Contagem: 3
Contagem: 4
Contagem: 5
Fim da contagem!
```

> **Atencao:** Sempre garanta que a condicao do while vai se tornar falsa em algum momento. Se a condicao nunca mudar, o loop roda para sempre (loop infinito) e o programa trava. Se isso acontecer, pressione `Ctrl + C` no terminal para interromper.

### while com input — Repetir ate o usuario decidir parar

```python
# Programa que repete ate o usuario digitar "sair"
# "user_input" = entrada do usuario
user_input = ""

# Enquanto o usuario nao digitar "sair", continua pedindo
while user_input != "sair":
    user_input = input("Digite algo (ou 'sair' para encerrar): ")
    print(f"Voce digitou: {user_input}")

print("Programa encerrado.")
```

---

## break — Interrompendo o Loop

O comando `break` ("quebrar/interromper") para o loop imediatamente, independente da condicao:

```python
# Procurando um numero especifico
# "target" = alvo (o numero que estamos procurando)
target = 7

for number in range(1, 20):
    print(f"Verificando {number}...")
    if number == target:
        # Encontramos! Paramos o loop com break
        print(f"Encontrei o {target}!")
        break

print("Busca encerrada.")
```

**Saida esperada:**
```
Verificando 1...
Verificando 2...
...
Verificando 7...
Encontrei o 7!
Busca encerrada.
```

---

## continue — Pulando para a Proxima Iteracao

O comando `continue` ("continuar") pula o restante do bloco atual e vai direto para a proxima iteracao:

```python
# Exibindo apenas numeros impares de 1 a 10
for number in range(1, 11):
    # Se o numero for par, pula para o proximo
    if number % 2 == 0:
        continue  # Pula o print abaixo e vai para a proxima iteracao
    print(number, end=" ")
```

**Saida esperada:**
```
1 3 5 7 9 
```

---

## Padroes Comuns com Loops

### Padrao 1: Contador

```python
# Contando quantos numeros pares existem de 1 a 20
# "even_count" = contagem de pares (even = par, count = contagem)
even_count = 0

for number in range(1, 21):
    if number % 2 == 0:
        # Incrementamos o contador quando encontramos um par
        even_count = even_count + 1
        # Forma abreviada: even_count += 1 (faz a mesma coisa)

print(f"Quantidade de numeros pares de 1 a 20: {even_count}")
```

**Saida esperada:**
```
Quantidade de numeros pares de 1 a 20: 10
```

### Padrao 2: Acumulador (Soma)

```python
# Somando todos os numeros de 1 a 100
# "total" = total (acumulador — comeca em 0 e vai somando)
total = 0

for number in range(1, 101):
    # A cada iteracao, somamos o numero atual ao total
    total = total + number
    # Forma abreviada: total += number

print(f"Soma de 1 a 100: {total}")
```

**Saida esperada:**
```
Soma de 1 a 100: 5050
```

### Padrao 3: Busca

```python
# Procurando se um nome esta na lista
# "names" = nomes
names = ["Ana", "Carlos", "Maria", "Pedro", "Julia"]

# "search_name" = nome a buscar (search = busca)
search_name = input("Qual nome voce procura? ")

# "found" = encontrado — comeca como False
found = False

for name in names:
    if name.lower() == search_name.lower():
        found = True
        break  # Encontrou, nao precisa continuar procurando

if found:
    print(f"{search_name} esta na lista!")
else:
    print(f"{search_name} nao foi encontrado.")
```

---

## Loops Aninhados — Loop Dentro de Loop

Voce pode colocar um loop dentro de outro. O loop interno executa completamente para cada iteracao do loop externo:

```python
# Tabuada de multiplicacao (1 a 5)
for i in range(1, 6):
    # Para cada valor de i, o loop interno executa completamente
    for j in range(1, 6):
        # "result" = resultado da multiplicacao
        result = i * j
        print(f"{i} x {j} = {result}", end="\t")
    # Pula linha apos cada linha da tabuada
    print()
```

**Saida esperada:**
```
1 x 1 = 1	1 x 2 = 2	1 x 3 = 3	1 x 4 = 4	1 x 5 = 5	
2 x 1 = 2	2 x 2 = 4	2 x 3 = 6	2 x 4 = 8	2 x 5 = 10	
...
```

---

## for vs while — Quando Usar Cada Um?

| Situacao | Melhor opcao | Motivo |
|----------|-------------|--------|
| Sabe quantas vezes repetir | `for` | `range()` define o numero exato |
| Percorrer uma colecao | `for` | Itera naturalmente sobre cada item |
| Nao sabe quantas vezes | `while` | Repete ate a condicao mudar |
| Esperar entrada do usuario | `while` | Repete ate o usuario decidir parar |

---

## Resumo

| Conceito | Descricao |
|----------|-----------|
| `for i in range(n):` | Repete n vezes (0 a n-1) |
| `for item in colecao:` | Repete para cada item |
| `while condicao:` | Repete enquanto condicao for True |
| `break` | Interrompe o loop imediatamente |
| `continue` | Pula para a proxima iteracao |
| Contador | Variavel que conta ocorrencias |
| Acumulador | Variavel que soma valores |

---

## Para Saber Mais

- [W3Schools — Python For Loops](https://www.w3schools.com/python/python_for_loops.asp) — _Loops for_
- [W3Schools — Python While Loops](https://www.w3schools.com/python/python_while_loops.asp) — _Loops while_
- [W3Schools — Python Range](https://www.w3schools.com/python/ref_func_range.asp) — _Funcao range()_
- [Documentacao Python — Controle de Fluxo](https://docs.python.org/pt-br/3/tutorial/controlflow.html) — _Referencia oficial_

---

## Perguntas Frequentes (FAQ)

**P: O que e um "loop infinito"?**
R: E quando o loop nunca para porque a condicao nunca se torna falsa. Exemplo: `while True: print("ola")` roda para sempre. Se isso acontecer, pressione `Ctrl + C` no terminal para interromper o programa.

**P: Qual a diferenca entre for e while?**
R: O `for` e ideal quando voce sabe quantas vezes quer repetir ou quando quer percorrer uma colecao. O `while` e ideal quando voce nao sabe quantas vezes vai repetir — depende de uma condicao que pode mudar a qualquer momento.

**P: Por que range(5) gera 0, 1, 2, 3, 4 e nao 1, 2, 3, 4, 5?**
R: Porque em Python (e na maioria das linguagens), a contagem comeca do zero. `range(5)` gera 5 numeros comecando do 0. Se quiser comecar do 1, use `range(1, 6)`.

**P: O que e "iteracao"?**
R: E cada repeticao (volta) do loop. Se o loop executa 10 vezes, ele faz 10 iteracoes. E como cada volta que voce da em uma pista de corrida.

**P: O que e um "contador"?**
R: E uma variavel que conta quantas vezes algo aconteceu. Comeca em 0 (ou outro valor) e aumenta de 1 em 1 a cada vez. E como contar nos dedos.

**P: O que e um "acumulador"?**
R: E uma variavel que vai somando valores ao longo do loop. Comeca em 0 e a cada iteracao soma mais um valor. No final, tem o total acumulado. E como um cofrinho.

**P: O que e "incremento"?**
R: E aumentar o valor de uma variavel, geralmente de 1 em 1. `counter = counter + 1` ou `counter += 1` incrementa o contador. E como subir um degrau.

**P: O que `+=` significa?**
R: E uma forma abreviada de somar e atribuir. `x += 5` e o mesmo que `x = x + 5`. Tambem existem `-=`, `*=`, `/=` para outras operacoes.

**P: Posso usar break no for e no while?**
R: Sim! O `break` funciona em ambos os tipos de loop. Ele interrompe o loop imediatamente, independente da condicao ou do range.

**P: Posso usar continue no for e no while?**
R: Sim! O `continue` funciona em ambos. Ele pula o restante do bloco atual e vai para a proxima iteracao.

**P: O que acontece se eu esquecer de incrementar o contador no while?**
R: O loop nunca para — vira um loop infinito. A condicao nunca muda, entao o while continua executando para sempre. Sempre garanta que algo dentro do while muda a condicao.

**P: Posso ter um loop dentro de outro?**
R: Sim, isso se chama "loops aninhados". O loop interno executa completamente para cada iteracao do loop externo. Use com cuidado — muitos niveis de aninhamento tornam o codigo confuso.

**P: O que e `range(inicio, fim, passo)`?**
R: `range()` pode receber ate 3 argumentos: inicio (onde comecar), fim (onde parar, nao incluido) e passo (de quanto em quanto pular). Exemplo: `range(0, 10, 2)` gera 0, 2, 4, 6, 8.

**P: Posso contar de tras para frente com range?**
R: Sim! Use passo negativo: `range(10, 0, -1)` gera 10, 9, 8, ..., 1. O inicio deve ser maior que o fim quando o passo e negativo.

**P: O que e `enumerate()`?**
R: E uma funcao que adiciona um contador automatico ao loop for: `for i, item in enumerate(lista):` da acesso ao indice (i) e ao item ao mesmo tempo. Muito util, mas e um conceito intermediario.

**P: Posso usar else com for ou while?**
R: Sim! Python permite `for...else` e `while...else`. O bloco do `else` executa quando o loop termina normalmente (sem `break`). E um recurso avancado que nao e muito comum.

**P: Como faco um loop que pede dados ate o usuario acertar?**
R: Use `while` com uma condicao que verifica se a resposta esta correta. Exemplo: `while resposta != "correta": resposta = input("Tente novamente: ")`.

**P: Posso modificar a variavel do for dentro do loop?**
R: Voce pode, mas nao e recomendado. O `for` vai sobrescrever o valor na proxima iteracao de qualquer forma. Se precisa controlar a variavel manualmente, use `while`.

**P: O que e "iterar"?**
R: E o ato de percorrer uma colecao item por item. Quando voce usa `for item in lista:`, voce esta "iterando" sobre a lista — visitando cada item, um por um.

**P: E normal achar loops confusos no inicio?**
R: Muito normal! Loops sao um dos conceitos mais desafiadores para iniciantes. A chave e praticar bastante. Faca os exercicios, experimente variacoes e use `print()` dentro do loop para ver o que esta acontecendo a cada iteracao. Com o tempo, loops se tornam naturais.

---

## Exercicios de Fixacao

Os exercicios deste modulo estao em um arquivo separado. Este e um modulo complexo — os exercicios sao mais numerosos e progressivos.

**[Acessar Exercicios do Modulo 14](14-controles-repeticao-exercicios.md)**

---

[<- Anterior: Seletores match/case](13-seletores-match-case.md) | [Glossario](00-glossario.md) | [Proximo: Funcoes ->](15-funcoes.md)
