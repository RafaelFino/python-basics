# Exercicios — Modulo 14: Controles de Repeticao

[<- Voltar ao Modulo 14](14-controles-repeticao.md) | [Glossario](00-glossario.md)

> **Como usar estes exercicios:**
> 1. Leia o enunciado com atencao
> 2. Leia as dicas antes de comecar
> 3. Tente resolver sozinho
> 4. Use a Proposta de Teste para verificar se sua solucao funciona
> 5. So depois consulte a Resposta Comentada
>
> **Como testar:** Salve na pasta `~/meus-projetos/python-curso/modulo-14/` e execute com `python3 nome_do_arquivo.py`.
>
> Este e um modulo complexo. Os exercicios estao em ordem crescente de dificuldade.

---

## Exercicio 1 — Contagem Simples — Nivel: Basico

### Enunciado
Exiba os numeros de 1 a 10 usando um loop for.

### Dicas
- Use `range(1, 11)` para gerar numeros de 1 a 10

### Proposta de Teste
- **Caso unico:** Saida: `1 2 3 4 5 6 7 8 9 10`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Usamos for com range(1, 11) para gerar numeros de 1 a 10
# range(1, 11) gera: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
# O 11 nao e incluido — o range para um antes do fim
for number in range(1, 11):
    # "number" = numero — recebe cada valor a cada iteracao
    # end=" " mantem os numeros na mesma linha separados por espaco
    print(number, end=" ")
```

---

## Exercicio 2 — Contagem Regressiva — Nivel: Basico

### Enunciado
Exiba uma contagem regressiva de 10 a 1 e depois exiba "Lancamento!".

### Dicas
- Use `range(10, 0, -1)` para contar de tras para frente

### Proposta de Teste
- **Caso unico:** Saida: `10 9 8 7 6 5 4 3 2 1 Lancamento!`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# range(10, 0, -1) gera numeros de 10 ate 1 (0 nao e incluido)
# O terceiro argumento (-1) e o passo: conta de -1 em -1
for number in range(10, 0, -1):
    # "number" = numero
    print(number, end=" ")

# Apos o loop, exibimos a mensagem final
print("Lancamento!")
```

---

## Exercicio 3 — Soma de Numeros — Nivel: Basico

### Enunciado
Peca ao usuario um numero N e calcule a soma de todos os numeros de 1 ate N.

### Dicas
- Use um acumulador (variavel que comeca em 0 e vai somando)
- Use `range(1, n + 1)` para incluir o numero N

### Proposta de Teste
- **Caso basico:** N: `5` — Soma: 15 (1+2+3+4+5)
- **Caso de borda:** N: `1` — Soma: 1

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos o numero limite
# "n" = o numero ate onde queremos somar
n = int(input("Digite um numero: "))

# Criamos o acumulador — comeca em 0
# "total" = total (acumulador que vai somando)
total = 0

# Percorremos de 1 ate n (incluindo n)
for number in range(1, n + 1):
    # A cada iteracao, somamos o numero atual ao total
    # total = total + number (forma completa)
    total += number  # forma abreviada — faz a mesma coisa

# Exibimos o resultado
print(f"Soma de 1 a {n}: {total}")
```

---

## Exercicio 4 — Tabuada — Nivel: Basico

### Enunciado
Peca um numero ao usuario e exiba a tabuada de multiplicacao desse numero (de 1 a 10).

### Dicas
- Use `for` com `range(1, 11)`
- Multiplique o numero do usuario pelo contador

### Proposta de Teste
- **Caso basico:** Numero: `7` — Saida: `7 x 1 = 7`, `7 x 2 = 14`, ..., `7 x 10 = 70`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos o numero para a tabuada
# "number" = numero
number = int(input("Tabuada de qual numero? "))

# Exibimos a tabuada de 1 a 10
print(f"\nTabuada do {number}:")
for i in range(1, 11):
    # "i" = multiplicador (de 1 a 10)
    # "result" = resultado da multiplicacao
    result = number * i
    # Exibimos no formato "N x i = resultado"
    print(f"{number} x {i} = {result}")
```

---

## Exercicio 5 — Numeros Pares — Nivel: Basico

### Enunciado
Exiba todos os numeros pares de 1 a 30.

### Dicas
- Use `range(2, 31, 2)` para pular de 2 em 2
- Ou use `range(1, 31)` com `if` para verificar se e par

### Proposta de Teste
- **Caso unico:** Saida: `2 4 6 8 10 12 14 16 18 20 22 24 26 28 30`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Metodo 1: usando range com passo 2
# range(2, 31, 2) gera: 2, 4, 6, 8, ..., 30
print("Numeros pares de 1 a 30:")
for number in range(2, 31, 2):
    # "number" = numero — ja e par porque o range pula de 2 em 2
    print(number, end=" ")
```

---

## Exercicio 6 — Contador de Vogais — Nivel: Intermediario

### Enunciado
Peca uma frase ao usuario e conte quantas vogais (a, e, i, o, u) ela contem.

### Dicas
- Percorra cada caractere da frase com `for`
- Verifique se o caractere e uma vogal com `if`
- Use `.lower()` para ignorar maiusculas

### Proposta de Teste
- **Caso basico:** Frase: `Python e legal` — Vogais: 5
- **Caso de borda:** Frase: `xyz` — Vogais: 0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos uma frase ao usuario
# "sentence" = frase
sentence = input("Digite uma frase: ")

# Criamos o contador de vogais — comeca em 0
# "vowel_count" = contagem de vogais (vowel = vogal, count = contagem)
vowel_count = 0

# Definimos quais sao as vogais
# "vowels" = vogais
vowels = "aeiou"

# Percorremos cada caractere da frase
for char in sentence.lower():
    # "char" = caractere (cada letra da frase)
    # .lower() converte para minuscula para tratar A e a como iguais
    # Verificamos se o caractere esta na string de vogais
    if char in vowels:
        # Se for vogal, incrementamos o contador
        vowel_count += 1

# Exibimos o resultado
print(f"A frase tem {vowel_count} vogal(is).")
```

---

## Exercicio 7 — Maior Numero — Nivel: Intermediario

### Enunciado
Peca 5 numeros ao usuario (um por vez) e exiba qual foi o maior.

### Dicas
- Use um loop `for` com `range(5)` para pedir 5 numeros
- Guarde o maior valor encontrado em uma variavel

### Proposta de Teste
- **Caso basico:** Numeros: `3, 7, 2, 9, 1` — Maior: 9
- **Caso de borda:** Numeros: `5, 5, 5, 5, 5` — Maior: 5

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Variavel para guardar o maior numero encontrado
# Comecamos com None (nenhum valor ainda)
# "largest" = maior
largest = None

# Pedimos 5 numeros ao usuario
for i in range(5):
    # "number" = numero
    number = float(input(f"Digite o numero {i + 1} de 5: "))

    # Se e o primeiro numero OU se e maior que o atual maior
    if largest is None or number > largest:
        # Atualizamos o maior
        largest = number

# Exibimos o resultado
print(f"O maior numero digitado foi: {largest}")
```

---

## Exercicio 8 — Menu com While — Nivel: Intermediario

### Enunciado
Crie um menu que se repete ate o usuario escolher "Sair". Opcoes: 1-Bom dia, 2-Boa tarde, 3-Boa noite, 0-Sair.

### Dicas
- Use `while` com uma condicao que verifica se o usuario nao escolheu sair
- Dentro do while, exiba o menu e peca a opcao

### Proposta de Teste
- **Caso basico:** Escolher 1, depois 3, depois 0 — Exibe saudacoes e depois encerra
- **Caso de borda:** Escolher 0 direto — Encerra imediatamente

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Variavel para controlar o loop
# "option" = opcao — comecamos com -1 (valor que nao e nenhuma opcao valida)
option = -1

# O loop continua enquanto a opcao nao for 0 (sair)
while option != 0:
    # Exibimos o menu a cada iteracao
    print("\n=== Menu ===")
    print("1 - Bom dia")
    print("2 - Boa tarde")
    print("3 - Boa noite")
    print("0 - Sair")

    # Pedimos a opcao
    option = int(input("Escolha: "))

    # Verificamos a opcao escolhida
    if option == 1:
        print("Bom dia! Tenha um otimo dia!")
    elif option == 2:
        print("Boa tarde! Continue firme!")
    elif option == 3:
        print("Boa noite! Descanse bem!")
    elif option == 0:
        print("Ate logo!")
    else:
        print("Opcao invalida!")
```

---

## Exercicio 9 — Fatorial — Nivel: Intermediario

### Enunciado
Peca um numero inteiro positivo e calcule o fatorial dele. (Fatorial de um numero e a multiplicacao de todos os numeros de 1 ate ele. Exemplo: fatorial de 5 = 5 x 4 x 3 x 2 x 1 = 120. Fatorial de 1 = 1. Fatorial de 0 = 1.)

### Dicas
- Use um acumulador que comeca em 1 (nao em 0, porque estamos multiplicando)
- Multiplique o acumulador por cada numero de 1 ate N

### Proposta de Teste
- **Caso basico:** Numero: `5` — Fatorial: 120
- **Caso de borda:** Numero: `0` — Fatorial: 1
- **Caso de borda:** Numero: `1` — Fatorial: 1

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos o numero
# "n" = o numero cujo fatorial queremos calcular
n = int(input("Digite um numero inteiro positivo: "))

# Criamos o acumulador para o fatorial
# Comeca em 1 porque estamos multiplicando (se comecasse em 0, tudo seria 0)
# "factorial" = fatorial
factorial = 1

# Multiplicamos por cada numero de 1 ate n
for i in range(1, n + 1):
    # "i" = cada numero de 1 ate n
    # Multiplicamos o acumulador pelo numero atual
    factorial *= i  # forma abreviada de: factorial = factorial * i

# Exibimos o resultado
print(f"Fatorial de {n} = {factorial}")
```

---

## Exercicio 10 — Adivinhe o Numero — Nivel: Intermediario

### Enunciado
Defina um numero secreto no codigo (ex: 42). Peca ao usuario que adivinhe, dando dicas de "maior" ou "menor" a cada tentativa. Conte quantas tentativas foram necessarias.

### Dicas
- Use `while` para repetir ate o usuario acertar
- Compare o palpite com o numero secreto
- Use um contador de tentativas

### Proposta de Teste
- **Caso basico:** Secreto: 42, Palpites: 20 ("maior"), 50 ("menor"), 42 ("acertou em 3 tentativas")

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Definimos o numero secreto
# "secret_number" = numero secreto
secret_number = 42

# Contador de tentativas
# "attempts" = tentativas
attempts = 0

# Variavel para o palpite do usuario
# "guess" = palpite
guess = -1  # valor inicial diferente do secreto

# Enquanto o palpite for diferente do numero secreto, continua
while guess != secret_number:
    # Pedimos um palpite
    guess = int(input("Adivinhe o numero: "))
    # Incrementamos o contador de tentativas
    attempts += 1

    # Damos dicas
    if guess < secret_number:
        # O palpite e menor que o secreto — o numero e maior
        print("O numero e MAIOR. Tente novamente.")
    elif guess > secret_number:
        # O palpite e maior que o secreto — o numero e menor
        print("O numero e MENOR. Tente novamente.")
    else:
        # Acertou!
        print(f"Parabens! Voce acertou em {attempts} tentativa(s)!")
```

---

## Exercicio 11 — Soma ate Digitar Zero — Nivel: Intermediario

### Enunciado
Peca numeros ao usuario repetidamente. Quando ele digitar 0, pare e exiba a soma de todos os numeros digitados (exceto o zero).

### Dicas
- Use `while` com condicao baseada no valor digitado
- Use um acumulador para a soma

### Proposta de Teste
- **Caso basico:** Numeros: `5, 3, 7, 0` — Soma: 15
- **Caso de borda:** Primeiro numero: `0` — Soma: 0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Acumulador para a soma
# "total" = total
total = 0

# Pedimos o primeiro numero
# "number" = numero
number = float(input("Digite um numero (0 para parar): "))

# Enquanto o numero nao for zero, continuamos somando
while number != 0:
    # Somamos o numero ao total
    total += number
    # Pedimos o proximo numero
    number = float(input("Digite um numero (0 para parar): "))

# Exibimos a soma total
print(f"Soma total: {total}")
```

---

## Exercicio 12 — Padrao de Asteriscos — Nivel: Avancado

### Enunciado
Peca um numero N ao usuario e exiba um triangulo de asteriscos com N linhas. Exemplo para N=5:
```
*
**
***
****
*****
```

### Dicas
- Use um loop for de 1 a N
- Em cada iteracao, exiba i asteriscos (use `"*" * i`)

### Proposta de Teste
- **Caso basico:** N: `5` — Triangulo com 5 linhas
- **Caso de borda:** N: `1` — Apenas uma linha com `*`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos o numero de linhas
# "n" = numero de linhas do triangulo
n = int(input("Numero de linhas: "))

# Para cada linha de 1 a n
for i in range(1, n + 1):
    # "i" = numero da linha atual
    # "*" * i repete o asterisco i vezes
    # Na linha 1: "*", na linha 2: "**", na linha 3: "***", etc.
    print("*" * i)
```

---

## Exercicio 13 — Media de Notas com While — Nivel: Avancado

### Enunciado
Peca notas ao usuario ate que ele digite -1 para parar. Calcule e exiba a media das notas digitadas (sem contar o -1). Exiba tambem quantas notas foram digitadas.

### Dicas
- Use `while` com condicao baseada no valor digitado
- Use um acumulador para a soma e um contador para a quantidade
- Media = soma / quantidade

### Proposta de Teste
- **Caso basico:** Notas: `7, 8, 9, -1` — Media: 8.0, Quantidade: 3
- **Caso de borda:** Primeiro valor: `-1` — Nenhuma nota digitada

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Acumulador para a soma das notas
# "total" = total (soma)
total = 0

# Contador de notas
# "count" = contagem (quantas notas foram digitadas)
count = 0

# Pedimos a primeira nota
# "grade" = nota
grade = float(input("Digite uma nota (-1 para parar): "))

# Enquanto a nota nao for -1, continuamos
while grade != -1:
    # Somamos a nota ao total
    total += grade
    # Incrementamos o contador
    count += 1
    # Pedimos a proxima nota
    grade = float(input("Digite uma nota (-1 para parar): "))

# Exibimos o resultado
if count > 0:
    # "average" = media
    # Media = soma de todas as notas dividida pela quantidade de notas
    average = total / count
    print(f"Notas digitadas: {count}")
    print(f"Media: {average}")
else:
    print("Nenhuma nota foi digitada.")
```

---

## Exercicio 14 — Fibonacci — Nivel: Avancado

### Enunciado
Exiba os primeiros N numeros da sequencia de Fibonacci. (Fibonacci e uma sequencia onde cada numero e a soma dos dois anteriores. Comeca com 0 e 1: 0, 1, 1, 2, 3, 5, 8, 13, 21, ... Exemplo: 0+1=1, 1+1=2, 1+2=3, 2+3=5.)

### Dicas
- Comece com duas variaveis: a=0 e b=1
- A cada iteracao, o proximo numero e a+b
- Atualize: a recebe b, b recebe o proximo

### Proposta de Teste
- **Caso basico:** N: `10` — Saida: `0 1 1 2 3 5 8 13 21 34`
- **Caso de borda:** N: `1` — Saida: `0`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos quantos numeros exibir
# "n" = quantidade de numeros da sequencia
n = int(input("Quantos numeros de Fibonacci? "))

# Definimos os dois primeiros numeros da sequencia
# "a" e "b" sao os dois numeros anteriores
# A sequencia comeca com 0 e 1
a = 0
b = 1

# Exibimos os N primeiros numeros
print(f"Primeiros {n} numeros de Fibonacci:")
for i in range(n):
    # Exibimos o numero atual (a)
    print(a, end=" ")
    # Calculamos o proximo numero: soma dos dois anteriores
    # "next_number" = proximo numero
    next_number = a + b
    # Atualizamos: a recebe b, b recebe o proximo
    a = b
    b = next_number
```

---

## Exercicio 15 — Lista de Compras Interativa — Nivel: Avancado

### Enunciado
Crie um programa que peca itens e precos ao usuario repetidamente. Quando o usuario digitar "fim" como nome do item, pare e exiba a lista completa com o total.

### Dicas
- Use `while` para repetir ate o usuario digitar "fim"
- Use listas para guardar os itens e precos (ou exiba conforme digita)
- Use um acumulador para o total

### Proposta de Teste
- **Caso basico:** Itens: Arroz R$5, Feijao R$8, fim — Total: R$13.0
- **Caso de borda:** Primeiro item: "fim" — Lista vazia, Total: R$0.0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Acumulador para o total
# "total" = total da compra
total = 0

# Contador de itens
# "item_count" = contagem de itens
item_count = 0

# Cabecalho da lista
print("=== Lista de Compras ===")
print("(Digite 'fim' como nome do item para encerrar)\n")

# Pedimos o primeiro item
# "item_name" = nome do item
item_name = input("Nome do item: ")

# Enquanto o usuario nao digitar "fim", continuamos
while item_name.lower() != "fim":
    # Pedimos o preco do item
    # "item_price" = preco do item
    item_price = float(input(f"Preco de {item_name}: R$ "))

    # Somamos ao total e incrementamos o contador
    total += item_price
    item_count += 1

    # Exibimos o item adicionado
    print(f"  + {item_name}: R$ {item_price}")

    # Pedimos o proximo item
    item_name = input("\nNome do item: ")

# Exibimos o resumo
print("\n=== Resumo ===")
print(f"Itens: {item_count}")
print(f"Total: R$ {total}")
```

---

[<- Voltar ao Modulo 14](14-controles-repeticao.md) | [Glossario](00-glossario.md)
