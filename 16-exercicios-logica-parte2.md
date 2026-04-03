# Exercicios de Logica — Parte 2: Processamento de Listas

[<- Parte 1](16-exercicios-logica-parte1.md) | [Voltar ao Modulo 16](16-exercicios-logica.md) | [Parte 3 ->](16-exercicios-logica-parte3.md)

> **Nota:** Listas serao aprofundadas no modulo 19. Aqui usamos listas de forma basica: uma colecao de itens entre colchetes `[]`. Voce pode percorrer com `for item in lista:` e acessar por posicao com `lista[0]`.

---

## Exercicio 6 — Soma de Lista — Nivel: Basico
**Conceitos praticados:** loops, acumulador, listas

### Enunciado
Crie uma funcao `calculate_sum` que receba uma lista de numeros e retorne a soma de todos. Nao use a funcao `sum()` do Python.

### Dicas
- Use um acumulador que comeca em 0
- Percorra cada item com `for`

### Proposta de Teste
- Lista: `[1, 2, 3, 4, 5]` — Retorno: `15`
- Lista: `[10, -5, 3]` — Retorno: `8`
- Lista: `[]` — Retorno: `0`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Funcao que calcula a soma de uma lista de numeros
# "calculate_sum" = calcular soma
# "numbers" = numeros (a lista de numeros)
def calculate_sum(numbers):
    # Acumulador — comeca em 0
    # "total" = total
    total = 0
    # Percorremos cada numero da lista
    for number in numbers:
        # "number" = cada numero individual da lista
        # Somamos ao total
        total += number
    # Retornamos a soma total
    return total

# Testamos a funcao
print(f"Soma de [1,2,3,4,5]: {calculate_sum([1, 2, 3, 4, 5])}")
print(f"Soma de [10,-5,3]: {calculate_sum([10, -5, 3])}")
print(f"Soma de []: {calculate_sum([])}")
```

---

## Exercicio 7 — Maior e Menor de uma Lista — Nivel: Basico
**Conceitos praticados:** loops, comparacao, listas

### Enunciado
Crie uma funcao `find_min_max` que receba uma lista de numeros e retorne o menor e o maior valor. Nao use `min()` ou `max()`.

### Dicas
- Comece assumindo que o primeiro item e o menor e o maior
- Percorra a lista comparando cada item

### Proposta de Teste
- Lista: `[3, 7, 1, 9, 4]` — Menor: `1`, Maior: `9`
- Lista: `[5]` — Menor: `5`, Maior: `5`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Funcao que encontra o menor e o maior valor de uma lista
# "find_min_max" = encontrar minimo e maximo
# "numbers" = numeros
def find_min_max(numbers):
    # Comecamos assumindo que o primeiro item e o menor e o maior
    # "minimum" = minimo (menor valor)
    minimum = numbers[0]
    # "maximum" = maximo (maior valor)
    maximum = numbers[0]

    # Percorremos cada numero da lista
    for number in numbers:
        # Se encontramos um numero menor que o minimo atual, atualizamos
        if number < minimum:
            minimum = number
        # Se encontramos um numero maior que o maximo atual, atualizamos
        if number > maximum:
            maximum = number

    # Retornamos os dois valores
    return minimum, maximum

# Testamos a funcao
# Recebemos os dois valores retornados em duas variaveis
min_val, max_val = find_min_max([3, 7, 1, 9, 4])
print(f"Menor: {min_val}, Maior: {max_val}")

min_val, max_val = find_min_max([5])
print(f"Menor: {min_val}, Maior: {max_val}")
```

---

## Exercicio 8 — Media de uma Lista — Nivel: Intermediario
**Conceitos praticados:** loops, acumulador, contador, listas, funcoes

### Enunciado
Crie uma funcao `calculate_average` que receba uma lista de numeros e retorne a media. (Media = soma de todos os valores dividida pela quantidade de valores.)

### Dicas
- Calcule a soma (acumulador) e conte os itens (len ou contador)
- Divida a soma pela quantidade

### Proposta de Teste
- Lista: `[7, 8, 9]` — Media: `8.0`
- Lista: `[10]` — Media: `10.0`
- Lista: `[0, 0, 0]` — Media: `0.0`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Funcao que calcula a media de uma lista de numeros
# "calculate_average" = calcular media
# "numbers" = numeros
def calculate_average(numbers):
    # Verificamos se a lista nao esta vazia para evitar divisao por zero
    if len(numbers) == 0:
        return 0

    # Calculamos a soma de todos os numeros
    # "total" = total (soma)
    total = 0
    for number in numbers:
        total += number

    # Calculamos a media: soma dividida pela quantidade
    # len(numbers) retorna a quantidade de itens na lista
    # "average" = media
    average = total / len(numbers)

    return average

# Testamos a funcao
print(f"Media de [7,8,9]: {calculate_average([7, 8, 9])}")
print(f"Media de [10]: {calculate_average([10])}")
print(f"Media de [0,0,0]: {calculate_average([0, 0, 0])}")
```

---

## Exercicio 9 — Inverter uma Lista — Nivel: Intermediario
**Conceitos praticados:** loops, listas, logica de construcao

### Enunciado
Crie uma funcao `reverse_list` que receba uma lista e retorne uma nova lista com os elementos na ordem inversa. Nao use `.reverse()` ou `[::-1]`.

### Dicas
- Crie uma lista vazia
- Percorra a lista original e insira cada item no inicio da nova lista
- Ou percorra de tras para frente com range

### Proposta de Teste
- Lista: `[1, 2, 3, 4, 5]` — Retorno: `[5, 4, 3, 2, 1]`
- Lista: `["a"]` — Retorno: `["a"]`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Funcao que inverte uma lista
# "reverse_list" = inverter lista
# "original" = lista original
def reverse_list(original):
    # Criamos uma lista vazia para guardar o resultado
    # "reversed_list" = lista invertida
    reversed_list = []

    # Percorremos a lista original de tras para frente
    # range(len(original) - 1, -1, -1) gera indices do ultimo ao primeiro
    # len(original) - 1 = indice do ultimo item
    # -1 = para antes do indice -1 (ou seja, para no 0)
    # -1 = passo negativo (conta de tras para frente)
    for i in range(len(original) - 1, -1, -1):
        # "i" = indice atual (de tras para frente)
        # Adicionamos o item na nova lista
        # .append() adiciona um item ao final da lista
        reversed_list.append(original[i])

    return reversed_list

# Testamos a funcao
print(f"Invertida: {reverse_list([1, 2, 3, 4, 5])}")
print(f"Invertida: {reverse_list(['a'])}")
print(f"Invertida: {reverse_list([10, 20, 30])}")
```

---

## Exercicio 10 — Remover Duplicatas — Nivel: Avancado
**Conceitos praticados:** loops, listas, condicionais, logica de busca

### Enunciado
Crie uma funcao `remove_duplicates` que receba uma lista e retorne uma nova lista sem elementos repetidos, mantendo a ordem original.

### Dicas
- Crie uma lista vazia para o resultado
- Para cada item da original, verifique se ja esta no resultado antes de adicionar
- Use `if item not in resultado:` para verificar

### Proposta de Teste
- Lista: `[1, 2, 2, 3, 3, 3, 4]` — Retorno: `[1, 2, 3, 4]`
- Lista: `["a", "b", "a", "c"]` — Retorno: `["a", "b", "c"]`
- Lista: `[1, 1, 1]` — Retorno: `[1]`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Funcao que remove elementos duplicados mantendo a ordem
# "remove_duplicates" = remover duplicatas
# "original" = lista original
def remove_duplicates(original):
    # Lista para guardar o resultado sem duplicatas
    # "unique" = unicos (sem repeticao)
    unique = []

    # Percorremos cada item da lista original
    for item in original:
        # "item" = cada elemento da lista
        # Verificamos se o item ja esta na lista de unicos
        # "not in" verifica se o item NAO esta na lista
        if item not in unique:
            # Se nao esta, adicionamos
            unique.append(item)
        # Se ja esta, ignoramos (nao adicionamos de novo)

    return unique

# Testamos a funcao
print(f"Sem duplicatas: {remove_duplicates([1, 2, 2, 3, 3, 3, 4])}")
print(f"Sem duplicatas: {remove_duplicates(['a', 'b', 'a', 'c'])}")
print(f"Sem duplicatas: {remove_duplicates([1, 1, 1])}")
```

---

[<- Parte 1](16-exercicios-logica-parte1.md) | [Voltar ao Modulo 16](16-exercicios-logica.md) | [Parte 3 ->](16-exercicios-logica-parte3.md)
