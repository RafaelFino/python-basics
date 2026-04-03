# Exercicios de Logica — Parte 3: Contadores e Acumuladores

[<- Parte 2](16-exercicios-logica-parte2.md) | [Voltar ao Modulo 16](16-exercicios-logica.md) | [Parte 4 ->](16-exercicios-logica-parte4.md)

---

## Exercicio 11 — Contar Pares e Impares — Nivel: Basico
**Conceitos praticados:** loops, contadores, modulo, condicionais

### Enunciado
Peca 10 numeros ao usuario e conte quantos sao pares e quantos sao impares.

### Dicas
- Use dois contadores: um para pares e outro para impares
- Use `numero % 2 == 0` para verificar se e par

### Proposta de Teste
- Numeros: `1,2,3,4,5,6,7,8,9,10` — Pares: 5, Impares: 5
- Numeros: `2,4,6,8,10,12,14,16,18,20` — Pares: 10, Impares: 0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Contadores — comecam em 0
# "even_count" = contagem de pares (even = par)
even_count = 0
# "odd_count" = contagem de impares (odd = impar)
odd_count = 0

# Pedimos 10 numeros ao usuario
for i in range(10):
    # "number" = numero
    number = int(input(f"Digite o numero {i + 1} de 10: "))

    # Verificamos se e par ou impar usando modulo
    # Se o resto da divisao por 2 for 0, e par
    if number % 2 == 0:
        even_count += 1  # Incrementa contador de pares
    else:
        odd_count += 1   # Incrementa contador de impares

# Exibimos os resultados
print(f"\nNumeros pares: {even_count}")
print(f"Numeros impares: {odd_count}")
```

---

## Exercicio 12 — Soma de Positivos e Negativos — Nivel: Basico
**Conceitos praticados:** loops, acumuladores, condicionais

### Enunciado
Peca numeros ao usuario ate que ele digite 0. Calcule separadamente a soma dos positivos e a soma dos negativos.

### Dicas
- Use while para repetir ate digitar 0
- Use dois acumuladores: um para positivos e outro para negativos

### Proposta de Teste
- Numeros: `5, -3, 8, -2, 0` — Soma positivos: 13, Soma negativos: -5
- Numeros: `0` — Soma positivos: 0, Soma negativos: 0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Acumuladores separados para positivos e negativos
# "positive_sum" = soma dos positivos
positive_sum = 0
# "negative_sum" = soma dos negativos
negative_sum = 0

# Pedimos o primeiro numero
# "number" = numero
number = float(input("Digite um numero (0 para parar): "))

# Enquanto nao for zero, continuamos
while number != 0:
    if number > 0:
        # Numero positivo — soma no acumulador de positivos
        positive_sum += number
    else:
        # Numero negativo — soma no acumulador de negativos
        negative_sum += number

    # Pedimos o proximo numero
    number = float(input("Digite um numero (0 para parar): "))

# Exibimos os resultados
print(f"\nSoma dos positivos: {positive_sum}")
print(f"Soma dos negativos: {negative_sum}")
```

---

## Exercicio 13 — Maior Sequencia de Positivos — Nivel: Intermediario
**Conceitos praticados:** loops, contadores, logica de sequencia

### Enunciado
Peca 10 numeros ao usuario. Encontre a maior sequencia consecutiva de numeros positivos. (Exemplo: nos numeros 3, 5, -1, 2, 4, 6, -2, 1, a maior sequencia de positivos consecutivos e 3: os numeros 2, 4, 6.)

### Dicas
- Use um contador para a sequencia atual e outro para a maior encontrada
- Quando encontrar um positivo, incremente o contador atual
- Quando encontrar um negativo ou zero, compare com o maior e reinicie

### Proposta de Teste
- Numeros: `3, 5, -1, 2, 4, 6, -2, 1, 3, 5` — Maior sequencia: 3
- Numeros: `1, 2, 3, 4, 5, 6, 7, 8, 9, 10` — Maior sequencia: 10

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# "current_streak" = sequencia atual de positivos consecutivos
current_streak = 0
# "max_streak" = maior sequencia encontrada
max_streak = 0

# Pedimos 10 numeros
for i in range(10):
    # "number" = numero
    number = float(input(f"Numero {i + 1} de 10: "))

    if number > 0:
        # Numero positivo — incrementa a sequencia atual
        current_streak += 1
        # Se a sequencia atual for maior que a maior registrada, atualiza
        if current_streak > max_streak:
            max_streak = current_streak
    else:
        # Numero nao positivo — reinicia a sequencia atual
        current_streak = 0

# Exibimos o resultado
print(f"\nMaior sequencia de positivos consecutivos: {max_streak}")
```

---

## Exercicio 14 — Calculadora de Estatisticas — Nivel: Intermediario
**Conceitos praticados:** loops, acumuladores, contadores, funcoes, logica composta

### Enunciado
Peca numeros ao usuario ate digitar -999. Calcule e exiba: quantidade de numeros, soma, media, maior e menor valor.

### Dicas
- Use acumuladores e contadores
- Atualize o maior e menor a cada numero
- Cuidado com o primeiro numero (inicialize maior e menor com ele)

### Proposta de Teste
- Numeros: `5, 3, 8, 1, 9, -999` — Quantidade: 5, Soma: 26, Media: 5.2, Maior: 9, Menor: 1

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Funcao que coleta numeros e calcula estatisticas
# "calculate_statistics" = calcular estatisticas
def calculate_statistics():
    # Inicializamos as variaveis
    # "count" = contagem, "total" = soma total
    count = 0
    total = 0
    # "largest" = maior, "smallest" = menor
    largest = None  # None porque ainda nao temos nenhum numero
    smallest = None

    # Pedimos o primeiro numero
    # "number" = numero
    number = float(input("Digite um numero (-999 para parar): "))

    # Enquanto nao for -999, processamos
    while number != -999:
        # Incrementamos o contador e somamos ao total
        count += 1
        total += number

        # Atualizamos maior e menor
        # Na primeira iteracao, largest e smallest sao None
        if largest is None or number > largest:
            largest = number
        if smallest is None or number < smallest:
            smallest = number

        # Pedimos o proximo numero
        number = float(input("Digite um numero (-999 para parar): "))

    # Exibimos os resultados
    if count > 0:
        # "average" = media
        average = total / count
        print(f"\n=== Estatisticas ===")
        print(f"Quantidade: {count}")
        print(f"Soma: {total}")
        print(f"Media: {average}")
        print(f"Maior: {largest}")
        print(f"Menor: {smallest}")
    else:
        print("Nenhum numero foi digitado.")

# Chamamos a funcao
calculate_statistics()
```

---

## Exercicio 15 — Histograma Simples — Nivel: Avancado
**Conceitos praticados:** loops, contadores, strings, formatacao

### Enunciado
Peca 5 numeros inteiros positivos ao usuario. Para cada numero, exiba uma barra de asteriscos proporcional ao valor. Exemplo: se o numero for 7, exiba `*******`.

### Dicas
- Use `"*" * numero` para criar a barra
- Formate a saida para alinhar os numeros e as barras

### Proposta de Teste
- Numeros: `3, 7, 5, 2, 9` — Barras de 3, 7, 5, 2 e 9 asteriscos respectivamente

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Lista para guardar os numeros (usaremos de forma simples)
# "values" = valores
values = []

# Pedimos 5 numeros
print("Digite 5 numeros inteiros positivos:\n")
for i in range(5):
    # "value" = valor
    value = int(input(f"Numero {i + 1}: "))
    # .append() adiciona o valor ao final da lista
    values.append(value)

# Exibimos o histograma
print("\n=== Histograma ===")
for i in range(len(values)):
    # "bar" = barra de asteriscos
    # "*" * values[i] repete o asterisco N vezes
    bar = "*" * values[i]
    # Exibimos o numero e a barra
    # f"{values[i]:>3}" alinha o numero a direita com 3 espacos
    print(f"{values[i]:>3} | {bar}")
```

---

[<- Parte 2](16-exercicios-logica-parte2.md) | [Voltar ao Modulo 16](16-exercicios-logica.md) | [Parte 4 ->](16-exercicios-logica-parte4.md)
