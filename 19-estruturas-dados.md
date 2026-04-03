# 19 — Estruturas de Dados: Listas, Tuplas, Dicionarios e Conjuntos

[<- Anterior: Tratamento de Erros](18-tratamento-erros.md) | [Glossario](00-glossario.md) | [Proximo: Leitura e Escrita de Arquivos ->](20-leitura-escrita-arquivos.md)

---

## Introducao

Ate agora, voce trabalhou com variaveis que guardam um unico valor — um numero, um texto, um verdadeiro ou falso. Mas e quando voce precisa guardar **varios valores** ao mesmo tempo?

Imagine que voce esta fazendo compras no mercado. Voce nao anota cada item em um papel separado — voce faz uma **lista de compras** com todos os itens juntos. Em Python, temos estruturas que funcionam exatamente assim: elas guardam varios valores organizados em um unico lugar.

Neste modulo, voce vai aprender as quatro principais estruturas de dados do Python:

- **Listas** — como uma lista de compras: voce pode adicionar, remover e reorganizar itens
- **Tuplas** — como uma data de nascimento: uma vez definida, nao muda
- **Dicionarios** — como uma agenda telefonica: cada nome (chave) tem um telefone (valor) associado
- **Conjuntos (sets)** — como um album de figurinhas sem repetidas: cada elemento aparece apenas uma vez

> **Dica:** Consulte o [Glossario](00-glossario.md) sempre que encontrar um termo desconhecido.

---

## Como Executar os Exemplos Deste Modulo

1. Copie o codigo e cole em um novo arquivo no VSCode
2. Salve na pasta `~/meus-projetos/python-curso/modulo-19/`
3. No terminal: `cd ~/meus-projetos/python-curso/modulo-19`
4. Execute: `python3 nome_do_arquivo.py`

---

## Quando Usar Cada Estrutura

Antes de entrar nos detalhes, veja um resumo com analogias do dia a dia:

| Estrutura | Analogia | Quando usar |
|-----------|----------|-------------|
| Lista | Lista de compras | Colecao ordenada que pode mudar (adicionar, remover, reordenar) |
| Tupla | Data de nascimento | Dados que nao devem mudar depois de criados |
| Dicionario | Agenda telefonica | Quando voce precisa buscar um valor por uma chave (nome → telefone) |
| Conjunto | Album de figurinhas sem repetidas | Quando voce precisa de elementos unicos, sem repeticao |

---

## Listas

### O Que e Uma Lista

Uma lista e uma colecao **ordenada** e **mutavel** de elementos. "Ordenada" significa que os itens tem posicao (primeiro, segundo, terceiro...). "Mutavel" significa que voce pode adicionar, remover e alterar itens depois de criar a lista.

Pense em uma **lista de compras**: voce escreve os itens em ordem, pode riscar um item, adicionar outro no final, ou trocar um item por outro.

### Criando Listas

```python
# Criando uma lista vazia
# "shopping_list" = lista de compras
shopping_list = []

# Criando uma lista com itens
# "fruits" = frutas
fruits = ["maca", "banana", "laranja", "uva", "manga"]

# Listas podem ter diferentes tipos de dados
# "mixed" = misturado
mixed = ["Ana", 25, 1.70, True]

# Verificando o tipo
print(type(fruits))
```

Saida esperada:
```
<class 'list'>
```

### Indexacao — Acessando Itens pela Posicao

Cada item da lista tem uma posicao chamada **indice** (index). O primeiro item tem indice **0** (zero), nao 1. Isso e uma convencao da programacao.

Pense em um predio: o terreo e o andar 0, o primeiro andar e o 1, e assim por diante.

```python
# "fruits" = frutas
fruits = ["maca", "banana", "laranja", "uva", "manga"]

# Acessando pelo indice (index = posicao)
# Indice:   0        1         2        3       4
print(fruits[0])   # Primeiro item
print(fruits[1])   # Segundo item
print(fruits[4])   # Ultimo item
print(fruits[-1])  # Ultimo item (indice negativo conta de tras para frente)
print(fruits[-2])  # Penultimo item
```

Saida esperada:
```
maca
banana
manga
manga
uva
```

### Fatiamento (Slicing) — Pegando Pedacos da Lista

Fatiamento e como cortar um pedaco de um bolo: voce escolhe onde comecar e onde parar.

A sintaxe e `lista[inicio:fim]` — o inicio e incluido, mas o fim **nao** e incluido.

```python
# "fruits" = frutas
fruits = ["maca", "banana", "laranja", "uva", "manga"]

# Fatiamento (slicing = fatiar)
# Do indice 1 ate o 3 (o 3 nao entra)
print(fruits[1:3])

# Do inicio ate o indice 3 (o 3 nao entra)
print(fruits[:3])

# Do indice 2 ate o final
print(fruits[2:])

# Copia completa da lista
print(fruits[:])
```

Saida esperada:
```
['banana', 'laranja']
['maca', 'banana', 'laranja']
['laranja', 'uva', 'manga']
['maca', 'banana', 'laranja', 'uva', 'manga']
```

### Alterando Itens da Lista

Como listas sao mutaveis, voce pode trocar qualquer item:

```python
# "fruits" = frutas
fruits = ["maca", "banana", "laranja"]

# Trocando o item na posicao 1
# Antes: banana. Depois: abacaxi
fruits[1] = "abacaxi"

print(fruits)
```

Saida esperada:
```
['maca', 'abacaxi', 'laranja']
```

### Metodos de Lista

Metodos sao funcoes que "pertencem" a lista. Voce chama um metodo usando o ponto: `lista.metodo()`.

#### append() — Adicionar no Final

```python
# "shopping_list" = lista de compras
shopping_list = ["arroz", "feijao"]

# append() = acrescentar/adicionar ao final
shopping_list.append("macarrao")
shopping_list.append("leite")

print(shopping_list)
```

Saida esperada:
```
['arroz', 'feijao', 'macarrao', 'leite']
```

#### insert() — Adicionar em Posicao Especifica

```python
# "fruits" = frutas
fruits = ["maca", "laranja", "uva"]

# insert(posicao, item) = inserir na posicao especificada
# Inserindo "banana" na posicao 1
fruits.insert(1, "banana")

print(fruits)
```

Saida esperada:
```
['maca', 'banana', 'laranja', 'uva']
```

#### extend() — Juntar Duas Listas

```python
# "fruits" = frutas, "more_fruits" = mais frutas
fruits = ["maca", "banana"]
more_fruits = ["uva", "manga"]

# extend() = estender/juntar outra lista ao final
fruits.extend(more_fruits)

print(fruits)
```

Saida esperada:
```
['maca', 'banana', 'uva', 'manga']
```

#### remove() — Remover pelo Valor

```python
# "fruits" = frutas
fruits = ["maca", "banana", "laranja", "banana"]

# remove() = remover a PRIMEIRA ocorrencia do valor
fruits.remove("banana")

print(fruits)
```

Saida esperada:
```
['maca', 'laranja', 'banana']
```

> **Nota:** O remove() so remove a **primeira** ocorrencia. A segunda "banana" permaneceu.

#### pop() — Remover pela Posicao

```python
# "fruits" = frutas
fruits = ["maca", "banana", "laranja", "uva"]

# pop() sem argumento remove o ULTIMO item e retorna ele
# "last" = ultimo
last = fruits.pop()
print(f"Removido: {last}")
print(f"Lista: {fruits}")

# pop(indice) remove o item na posicao especificada
# "first" = primeiro
first = fruits.pop(0)
print(f"Removido: {first}")
print(f"Lista: {fruits}")
```

Saida esperada:
```
Removido: uva
Lista: ['maca', 'banana', 'laranja']
Removido: maca
Lista: ['banana', 'laranja']
```

#### sort() — Ordenar a Lista

```python
# "numbers" = numeros
numbers = [5, 2, 8, 1, 9, 3]

# sort() = ordenar em ordem crescente (modifica a lista original)
numbers.sort()
print(f"Crescente: {numbers}")

# sort(reverse=True) = ordenar em ordem decrescente
# "reverse" = reverso/inverso
numbers.sort(reverse=True)
print(f"Decrescente: {numbers}")
```

Saida esperada:
```
Crescente: [1, 2, 3, 5, 8, 9]
Decrescente: [9, 8, 5, 3, 2, 1]
```

#### reverse() — Inverter a Ordem

```python
# "letters" = letras
letters = ["a", "b", "c", "d"]

# reverse() = inverter a ordem dos itens
letters.reverse()

print(letters)
```

Saida esperada:
```
['d', 'c', 'b', 'a']
```

#### index() — Encontrar a Posicao de um Item

```python
# "fruits" = frutas
fruits = ["maca", "banana", "laranja", "uva"]

# index() = encontrar o indice (posicao) de um item
# "position" = posicao
position = fruits.index("laranja")
print(f"Laranja esta na posicao: {position}")
```

Saida esperada:
```
Laranja esta na posicao: 2
```

#### count() — Contar Ocorrencias

```python
# "grades" = notas
grades = [7, 8, 7, 9, 7, 10, 8]

# count() = contar quantas vezes um valor aparece
# "count_seven" = contagem de setes
count_seven = grades.count(7)
print(f"A nota 7 aparece {count_seven} vezes")
```

Saida esperada:
```
A nota 7 aparece 3 vezes
```

#### len() — Tamanho da Lista

```python
# "fruits" = frutas
fruits = ["maca", "banana", "laranja", "uva", "manga"]

# len() = length = comprimento/tamanho
# Retorna quantos itens a lista tem
# "size" = tamanho
size = len(fruits)
print(f"A lista tem {size} frutas")
```

Saida esperada:
```
A lista tem 5 frutas
```

> **Nota:** `len()` nao e um metodo da lista — e uma funcao do Python que funciona com varias estruturas de dados.

### Percorrendo Listas com for

```python
# "fruits" = frutas
fruits = ["maca", "banana", "laranja"]

# Percorrendo cada item da lista
for fruit in fruits:
    # "fruit" = fruta (cada item da vez)
    print(f"Eu gosto de {fruit}")
```

Saida esperada:
```
Eu gosto de maca
Eu gosto de banana
Eu gosto de laranja
```

### Verificando se um Item Existe na Lista

```python
# "fruits" = frutas
fruits = ["maca", "banana", "laranja"]

# "in" verifica se o item esta na lista
if "banana" in fruits:
    print("Banana esta na lista!")

if "abacaxi" not in fruits:
    print("Abacaxi NAO esta na lista!")
```

Saida esperada:
```
Banana esta na lista!
Abacaxi NAO esta na lista!
```

---

## Tuplas

### O Que e Uma Tupla

Uma tupla e uma colecao **ordenada** e **imutavel** de elementos. "Imutavel" significa que, depois de criada, voce **nao pode** adicionar, remover ou alterar itens.

Pense em uma **data de nascimento**: uma vez que voce nasceu em 15/03/1990, essa data nunca vai mudar. Ela tem tres partes (dia, mes, ano) em uma ordem fixa. Isso e uma tupla.

### Criando Tuplas

```python
# Criando uma tupla com parenteses
# "birth_date" = data de nascimento
# (dia, mes, ano)
birth_date = (15, 3, 1990)

# Tupla com um unico item — precisa da virgula!
# "single" = unico
single = (42,)

# Sem a virgula, Python entende como um numero entre parenteses, nao como tupla
not_a_tuple = (42)

print(type(birth_date))
print(type(single))
print(type(not_a_tuple))
```

Saida esperada:
```
<class 'tuple'>
<class 'tuple'>
<class 'int'>
```

> **Atencao:** Para criar uma tupla com um unico item, voce **precisa** colocar uma virgula depois do item: `(42,)`. Sem a virgula, o Python entende como um numero comum entre parenteses.

### Acessando Itens da Tupla

O acesso funciona igual ao de listas — por indice:

```python
# "birth_date" = data de nascimento
birth_date = (15, 3, 1990)

# Acessando pelo indice
# "day" = dia, "month" = mes, "year" = ano
day = birth_date[0]
month = birth_date[1]
year = birth_date[2]

print(f"Nascimento: {day}/{month}/{year}")
```

Saida esperada:
```
Nascimento: 15/3/1990
```

### Imutabilidade — Nao Pode Alterar

```python
# "colors" = cores
colors = ("vermelho", "verde", "azul")

# Tentar alterar gera um erro!
# colors[0] = "amarelo"  # TypeError: 'tuple' object does not support item assignment

# Voce pode ler, mas nao pode modificar
print(colors[0])
```

Saida esperada:
```
vermelho
```

> **Por que usar tuplas se nao posso alterar?** Justamente por isso! Quando voce quer garantir que os dados nao sejam modificados acidentalmente, use uma tupla. Alem disso, tuplas sao mais rapidas que listas e podem ser usadas como chaves de dicionario (listas nao podem).

### Packing e Unpacking — Empacotar e Desempacotar

**Packing** (empacotar) e quando voce coloca varios valores em uma tupla. **Unpacking** (desempacotar) e quando voce extrai os valores da tupla para variaveis separadas.

```python
# Packing (empacotar) — varios valores viram uma tupla
# "coordinates" = coordenadas
coordinates = (10, 20)

# Unpacking (desempacotar) — a tupla vira variaveis separadas
# "x" e "y" recebem os valores da tupla
x, y = coordinates

print(f"x = {x}")
print(f"y = {y}")
```

Saida esperada:
```
x = 10
y = 20
```

```python
# Unpacking com mais valores
# "person" = pessoa
person = ("Ana", 25, "Sao Paulo")

# "name" = nome, "age" = idade, "city" = cidade
name, age, city = person

print(f"{name} tem {age} anos e mora em {city}")
```

Saida esperada:
```
Ana tem 25 anos e mora em Sao Paulo
```

> **Importante:** O numero de variaveis no unpacking deve ser igual ao numero de itens na tupla. Se forem diferentes, o Python gera um erro.

### Tuplas como Retorno Multiplo de Funcoes

Funcoes podem retornar varios valores de uma vez usando tuplas:

```python
# "calculate_rectangle" = calcular retangulo
# "width" = largura, "height" = altura
def calculate_rectangle(width, height):
    # "area" = area, "perimeter" = perimetro
    area = width * height
    perimeter = 2 * (width + height)
    # Retornamos dois valores — o Python empacota em uma tupla
    return area, perimeter

# Desempacotamos os dois valores retornados
# "area" = area, "perimeter" = perimetro
area, perimeter = calculate_rectangle(5, 3)

print(f"Area: {area}")
print(f"Perimetro: {perimeter}")
```

Saida esperada:
```
Area: 15
Perimetro: 16
```

### Tuplas como Chaves de Dicionario

Listas nao podem ser chaves de dicionario porque sao mutaveis. Tuplas podem, porque sao imutaveis:

```python
# Usando tuplas como chaves de dicionario
# Cada chave e uma coordenada (linha, coluna)
# "board" = tabuleiro
board = {}
board[(0, 0)] = "X"
board[(0, 1)] = "O"
board[(1, 1)] = "X"

print(board)
print(f"Posicao (0, 0): {board[(0, 0)]}")
```

Saida esperada:
```
{(0, 0): 'X', (0, 1): 'O', (1, 1): 'X'}
Posicao (0, 0): X
```

---

## Dicionarios

### O Que e Um Dicionario

Um dicionario e uma colecao de pares **chave: valor**. Cada chave e unica e aponta para um valor. E como uma **agenda telefonica**: voce procura pelo nome (chave) e encontra o telefone (valor).

Dicionarios sao **mutaveis** (voce pode adicionar, remover e alterar itens) e, a partir do Python 3.7, mantem a **ordem de insercao**.

### Criando Dicionarios

```python
# Criando um dicionario vazio
# "contacts" = contatos
contacts = {}

# Criando um dicionario com dados
# "student" = estudante
# "name" = nome, "age" = idade, "city" = cidade
student = {
    "name": "Carlos",
    "age": 20,
    "city": "Belo Horizonte"
}

print(student)
print(type(student))
```

Saida esperada:
```
{'name': 'Carlos', 'age': 20, 'city': 'Belo Horizonte'}
<class 'dict'>
```

### Acessando Valores por Chave

```python
# "student" = estudante
student = {
    "name": "Carlos",
    "age": 20,
    "city": "Belo Horizonte"
}

# Acessando pelo nome da chave (key = chave)
print(student["name"])
print(student["age"])
```

Saida esperada:
```
Carlos
20
```

> **Cuidado:** Se voce tentar acessar uma chave que nao existe com `[]`, o Python gera um erro `KeyError`. Para evitar isso, use o metodo `get()`.

### O Metodo get() — Acesso Seguro

```python
# "student" = estudante
student = {
    "name": "Carlos",
    "age": 20
}

# get() retorna o valor se a chave existir
print(student.get("name"))

# Se a chave nao existir, retorna None (nenhum valor)
print(student.get("phone"))

# Voce pode definir um valor padrao para quando a chave nao existir
# "default" = padrao
print(student.get("phone", "Nao informado"))
```

Saida esperada:
```
Carlos
None
Nao informado
```

### Adicionando e Alterando Itens

```python
# "student" = estudante
student = {
    "name": "Carlos",
    "age": 20
}

# Adicionando uma nova chave
# "email" = email
student["email"] = "carlos@email.com"

# Alterando um valor existente
student["age"] = 21

print(student)
```

Saida esperada:
```
{'name': 'Carlos', 'age': 21, 'email': 'carlos@email.com'}
```

### Metodos de Dicionario

#### keys() — Todas as Chaves

```python
# "product" = produto
product = {"name": "Arroz", "price": 5.99, "quantity": 10}

# keys() = chaves — retorna todas as chaves do dicionario
# "all_keys" = todas as chaves
all_keys = product.keys()
print(all_keys)
```

Saida esperada:
```
dict_keys(['name', 'price', 'quantity'])
```

#### values() — Todos os Valores

```python
# "product" = produto
product = {"name": "Arroz", "price": 5.99, "quantity": 10}

# values() = valores — retorna todos os valores do dicionario
# "all_values" = todos os valores
all_values = product.values()
print(all_values)
```

Saida esperada:
```
dict_values(['Arroz', 5.99, 10])
```

#### items() — Pares Chave-Valor

```python
# "product" = produto
product = {"name": "Arroz", "price": 5.99, "quantity": 10}

# items() = itens — retorna pares (chave, valor) como tuplas
# "all_items" = todos os itens
all_items = product.items()
print(all_items)
```

Saida esperada:
```
dict_items([('name', 'Arroz'), ('price', 5.99), ('quantity', 10)])
```

#### update() — Atualizar com Outro Dicionario

```python
# "product" = produto
product = {"name": "Arroz", "price": 5.99}

# "new_data" = novos dados
new_data = {"price": 6.49, "category": "Alimentos"}

# update() = atualizar — adiciona/atualiza com os dados do outro dicionario
product.update(new_data)

print(product)
```

Saida esperada:
```
{'name': 'Arroz', 'price': 6.49, 'category': 'Alimentos'}
```

> **Nota:** O preco (price) foi atualizado de 5.99 para 6.49, e a categoria (category) foi adicionada.

#### pop() — Remover por Chave

```python
# "product" = produto
product = {"name": "Arroz", "price": 5.99, "quantity": 10}

# pop(chave) = remover o item com a chave especificada e retornar o valor
# "removed_price" = preco removido
removed_price = product.pop("price")

print(f"Preco removido: {removed_price}")
print(f"Dicionario: {product}")
```

Saida esperada:
```
Preco removido: 5.99
Dicionario: {'name': 'Arroz', 'quantity': 10}
```

### Percorrendo Dicionarios com for

```python
# "student" = estudante
student = {"name": "Ana", "age": 22, "city": "Recife"}

# Percorrendo as chaves
print("--- Chaves ---")
for key in student:
    # "key" = chave
    print(key)

# Percorrendo os valores
print("--- Valores ---")
for value in student.values():
    # "value" = valor
    print(value)

# Percorrendo chaves E valores juntos
print("--- Chaves e Valores ---")
for key, value in student.items():
    print(f"{key}: {value}")
```

Saida esperada:
```
--- Chaves ---
name
age
city
--- Valores ---
Ana
22
Recife
--- Chaves e Valores ---
name: Ana
age: 22
city: Recife
```

### Verificando se uma Chave Existe

```python
# "student" = estudante
student = {"name": "Ana", "age": 22}

# "in" verifica se a CHAVE existe no dicionario
if "name" in student:
    print("A chave 'name' existe!")

if "phone" not in student:
    print("A chave 'phone' NAO existe!")
```

Saida esperada:
```
A chave 'name' existe!
A chave 'phone' NAO existe!
```

### Dicionarios Aninhados

Dicionarios podem conter outros dicionarios como valores. Isso e util para representar dados mais complexos.

Pense em uma **ficha de cadastro** que tem uma secao de endereco dentro dela:

```python
# "student" = estudante
# "address" = endereco, "street" = rua, "number" = numero
student = {
    "name": "Maria",
    "age": 19,
    "address": {
        "street": "Rua das Flores",
        "number": 123,
        "city": "Curitiba"
    }
}

# Acessando dados do dicionario interno
print(student["name"])
print(student["address"]["street"])
print(student["address"]["city"])
```

Saida esperada:
```
Maria
Rua das Flores
Curitiba
```

```python
# Lista de dicionarios — muito comum em programas reais
# "products" = produtos
products = [
    {"name": "Arroz", "price": 5.99},
    {"name": "Feijao", "price": 7.49},
    {"name": "Macarrao", "price": 3.29}
]

# Percorrendo a lista de dicionarios
for product in products:
    # "product" = produto (cada dicionario da vez)
    print(f"{product['name']}: R$ {product['price']}")
```

Saida esperada:
```
Arroz: R$ 5.99
Feijao: R$ 7.49
Macarrao: R$ 3.29
```

---

## Conjuntos (Sets)

### O Que e Um Conjunto

Um conjunto (set) e uma colecao **nao ordenada** de elementos **unicos**. "Nao ordenada" significa que os itens nao tem posicao fixa. "Unicos" significa que nao pode haver itens repetidos.

Pense em um **album de figurinhas sem repetidas**: se voce ja tem a figurinha numero 5, nao adianta tentar colocar outra numero 5 — o album so aceita uma de cada.

### Criando Conjuntos

```python
# Criando um conjunto com chaves {}
# "fruits" = frutas
fruits = {"maca", "banana", "laranja"}

# Criando um conjunto a partir de uma lista (remove duplicatas!)
# "numbers" = numeros
numbers = {1, 2, 3, 2, 1, 4, 3, 5}

print(fruits)
print(numbers)
print(type(fruits))
```

Saida esperada:
```
{'maca', 'banana', 'laranja'}
{1, 2, 3, 4, 5}
<class 'set'>
```

> **Nota:** Os numeros repetidos foram removidos automaticamente! O conjunto so mantem uma copia de cada valor.

> **Atencao:** Para criar um conjunto **vazio**, use `set()`, nao `{}`. As chaves vazias `{}` criam um dicionario vazio, nao um conjunto.

```python
# Conjunto vazio — use set(), nao {}
# "empty_set" = conjunto vazio
empty_set = set()

# Isso cria um DICIONARIO vazio, nao um conjunto!
# "empty_dict" = dicionario vazio
empty_dict = {}

print(type(empty_set))
print(type(empty_dict))
```

Saida esperada:
```
<class 'set'>
<class 'dict'>
```

### Adicionando e Removendo Elementos

```python
# "fruits" = frutas
fruits = {"maca", "banana"}

# add() = adicionar um elemento ao conjunto
fruits.add("laranja")
fruits.add("uva")
print(f"Apos adicionar: {fruits}")

# Adicionar um item que ja existe nao faz nada (sem erro)
fruits.add("maca")
print(f"Apos adicionar 'maca' de novo: {fruits}")

# discard() = descartar/remover um elemento (sem erro se nao existir)
fruits.discard("banana")
print(f"Apos remover 'banana': {fruits}")

# discard() de item que nao existe — nao gera erro
fruits.discard("abacaxi")

# remove() = remover um elemento (gera erro se nao existir!)
# fruits.remove("abacaxi")  # KeyError!
```

Saida esperada:
```
Apos adicionar: {'maca', 'banana', 'laranja', 'uva'}
Apos adicionar 'maca' de novo: {'maca', 'banana', 'laranja', 'uva'}
Apos remover 'banana': {'maca', 'laranja', 'uva'}
```

> **Dica:** Prefira `discard()` em vez de `remove()` quando nao tiver certeza se o item existe. O `discard()` nao gera erro se o item nao for encontrado.

> **Nota:** A ordem dos itens exibidos pode variar porque conjuntos nao tem ordem fixa.

### Verificando Pertencimento

```python
# "fruits" = frutas
fruits = {"maca", "banana", "laranja"}

# "in" verifica se o item pertence ao conjunto
if "banana" in fruits:
    print("Banana esta no conjunto!")

if "abacaxi" not in fruits:
    print("Abacaxi NAO esta no conjunto!")
```

Saida esperada:
```
Banana esta no conjunto!
Abacaxi NAO esta no conjunto!
```

### Operacoes de Conjuntos

Conjuntos suportam operacoes matematicas que sao muito uteis. Pense em dois grupos de amigos e as operacoes que voce pode fazer com eles:

#### Uniao — Todos os Elementos de Ambos

```python
# "group_a" = grupo A, "group_b" = grupo B
group_a = {"Ana", "Bruno", "Carlos"}
group_b = {"Bruno", "Diana", "Carlos", "Eva"}

# union() = uniao — todos os elementos de ambos (sem repetir)
# "all_people" = todas as pessoas
all_people = group_a.union(group_b)
print(f"Uniao: {all_people}")
```

Saida esperada:
```
Uniao: {'Ana', 'Bruno', 'Carlos', 'Diana', 'Eva'}
```

#### Intersecao — Elementos em Comum

```python
# "group_a" = grupo A, "group_b" = grupo B
group_a = {"Ana", "Bruno", "Carlos"}
group_b = {"Bruno", "Diana", "Carlos", "Eva"}

# intersection() = intersecao — elementos que estao em AMBOS
# "common" = em comum
common = group_a.intersection(group_b)
print(f"Em comum: {common}")
```

Saida esperada:
```
Em comum: {'Bruno', 'Carlos'}
```

#### Diferenca — Elementos Exclusivos

```python
# "group_a" = grupo A, "group_b" = grupo B
group_a = {"Ana", "Bruno", "Carlos"}
group_b = {"Bruno", "Diana", "Carlos", "Eva"}

# difference() = diferenca — elementos que estao em A mas NAO em B
# "only_a" = somente no grupo A
only_a = group_a.difference(group_b)
print(f"So no grupo A: {only_a}")

# Diferenca no sentido contrario
# "only_b" = somente no grupo B
only_b = group_b.difference(group_a)
print(f"So no grupo B: {only_b}")
```

Saida esperada:
```
So no grupo A: {'Ana'}
So no grupo B: {'Diana', 'Eva'}
```

### Removendo Duplicatas de uma Lista com set()

Um uso muito pratico de conjuntos e remover itens duplicados de uma lista:

```python
# Lista com itens repetidos
# "names_with_duplicates" = nomes com duplicatas
names_with_duplicates = ["Ana", "Bruno", "Ana", "Carlos", "Bruno", "Ana"]

# Convertemos para conjunto (remove duplicatas) e depois de volta para lista
# "unique_names" = nomes unicos
unique_names = list(set(names_with_duplicates))

print(f"Com duplicatas: {names_with_duplicates}")
print(f"Sem duplicatas: {unique_names}")
```

Saida esperada:
```
Com duplicatas: ['Ana', 'Bruno', 'Ana', 'Carlos', 'Bruno', 'Ana']
Sem duplicatas: ['Ana', 'Bruno', 'Carlos']
```

> **Nota:** A ordem pode mudar ao converter para conjunto e de volta para lista, porque conjuntos nao mantem ordem.

---

## Comparacao entre as Estruturas

| Caracteristica | Lista | Tupla | Dicionario | Conjunto |
|----------------|-------|-------|------------|----------|
| Sintaxe | `[1, 2, 3]` | `(1, 2, 3)` | `{"a": 1}` | `{1, 2, 3}` |
| Ordenada | Sim | Sim | Sim (3.7+) | Nao |
| Mutavel | Sim | Nao | Sim | Sim |
| Permite duplicatas | Sim | Sim | Chaves unicas | Nao |
| Acesso por indice | Sim | Sim | Por chave | Nao |
| Analogia | Lista de compras | Data de nascimento | Agenda telefonica | Figurinhas sem repetidas |

### Quando Usar Cada Uma

- **Lista**: quando voce precisa de uma colecao ordenada que pode mudar. Exemplo: lista de tarefas, notas de alunos.
- **Tupla**: quando os dados nao devem mudar. Exemplo: coordenadas (x, y), retorno de funcoes com multiplos valores.
- **Dicionario**: quando voce precisa associar chaves a valores. Exemplo: cadastro de produtos, dados de um usuario.
- **Conjunto**: quando voce precisa de elementos unicos ou fazer operacoes de conjuntos. Exemplo: verificar quais alunos estao em duas turmas.

---

## Para Saber Mais

- [W3Schools — Python Lists](https://www.w3schools.com/python/python_lists.asp) — _Listas em Python com exemplos interativos_
- [W3Schools — Python Tuples](https://www.w3schools.com/python/python_tuples.asp) — _Tuplas em Python_
- [W3Schools — Python Dictionaries](https://www.w3schools.com/python/python_dictionaries.asp) — _Dicionarios em Python_
- [W3Schools — Python Sets](https://www.w3schools.com/python/python_sets.asp) — _Conjuntos em Python_
- [Documentacao Python — Estruturas de Dados](https://docs.python.org/pt-br/3/tutorial/datastructures.html) — _Referencia oficial em portugues_

---

## Perguntas Frequentes (FAQ)

**P: Qual a diferenca entre lista e tupla?**
R: A principal diferenca e que listas sao mutaveis (voce pode alterar, adicionar e remover itens) e tuplas sao imutaveis (uma vez criadas, nao podem ser modificadas). Use listas quando os dados podem mudar e tuplas quando os dados devem permanecer fixos.

**P: Quando devo usar um dicionario em vez de uma lista?**
R: Use um dicionario quando voce precisa buscar valores por um nome (chave), como buscar o telefone de alguem pelo nome. Use uma lista quando a ordem dos itens importa e voce acessa por posicao (indice).

**P: O que acontece se eu tentar acessar um indice que nao existe na lista?**
R: O Python gera um erro `IndexError`. Por exemplo, se a lista tem 3 itens (indices 0, 1, 2) e voce tentar acessar o indice 5, vai dar erro. Sempre verifique o tamanho da lista com `len()` antes de acessar.

**P: Posso misturar tipos diferentes em uma lista?**
R: Sim! Uma lista pode conter inteiros, strings, floats, booleanos e ate outras listas ou dicionarios. Exemplo: `["Ana", 25, True, 1.70]`. Porem, na pratica, e mais comum ter listas com itens do mesmo tipo.

**P: O que e "mutavel" e "imutavel"?**
R: Mutavel significa que pode ser alterado depois de criado — voce pode adicionar, remover ou trocar itens. Imutavel significa que nao pode ser alterado — uma vez criado, permanece igual. Listas e dicionarios sao mutaveis. Tuplas e strings sao imutaveis.

**P: Por que o indice comeca em 0 e nao em 1?**
R: E uma convencao da programacao que vem da forma como o computador organiza a memoria. O indice 0 significa "zero posicoes de distancia do inicio". Com o tempo, voce se acostuma e isso se torna natural.

**P: Posso ter uma lista dentro de outra lista?**
R: Sim! Isso se chama lista aninhada. Exemplo: `matrix = [[1, 2, 3], [4, 5, 6]]`. Para acessar um item, use dois indices: `matrix[0][1]` retorna `2` (primeira lista, segundo item).

**P: Qual a diferenca entre remove() e pop() em listas?**
R: `remove()` busca pelo **valor** e remove a primeira ocorrencia. `pop()` remove pelo **indice** (posicao) e retorna o item removido. Se voce sabe o valor, use `remove()`. Se sabe a posicao, use `pop()`.

**P: O que acontece se eu usar append() com uma lista como argumento?**
R: O `append()` adiciona o item como um unico elemento. Se voce fizer `lista.append([4, 5])`, a lista interna sera adicionada como um unico item. Para juntar duas listas, use `extend()`.

**P: Posso ordenar uma lista de strings?**
R: Sim! O `sort()` ordena strings em ordem alfabetica. Exemplo: `["banana", "abacaxi", "uva"].sort()` resulta em `["abacaxi", "banana", "uva"]`. Letras maiusculas vem antes de minusculas na ordenacao padrao.

**P: O que e um dicionario aninhado?**
R: E um dicionario que contem outro dicionario como valor. Exemplo: um cadastro de aluno com endereco, onde o endereco e outro dicionario com rua, numero e cidade. Voce acessa com chaves encadeadas: `aluno["address"]["city"]`.

**P: Posso usar numeros como chaves de dicionario?**
R: Sim! Chaves podem ser qualquer tipo imutavel: strings, numeros inteiros, floats ou tuplas. Nao podem ser listas ou outros dicionarios (porque sao mutaveis).

**P: O que acontece se eu adicionar um item repetido a um conjunto?**
R: Nada! O conjunto simplesmente ignora o item duplicado, sem gerar erro. Essa e justamente a utilidade dos conjuntos — garantir que cada elemento apareca apenas uma vez.

**P: Posso acessar itens de um conjunto pelo indice?**
R: Nao! Conjuntos nao tem ordem fixa, entao nao suportam acesso por indice. Se voce precisa de acesso por posicao, use uma lista. Conjuntos sao uteis para verificar pertencimento (`in`) e operacoes de conjuntos (uniao, intersecao).

**P: Qual a diferenca entre discard() e remove() em conjuntos?**
R: Ambos removem um elemento, mas `remove()` gera erro `KeyError` se o item nao existir, enquanto `discard()` nao gera erro. Prefira `discard()` quando nao tiver certeza se o item esta no conjunto.

**P: Posso converter entre as estruturas?**
R: Sim! Use `list()`, `tuple()`, `set()` e `dict()` para converter. Exemplo: `list({1, 2, 3})` converte um conjunto em lista. Para dicionarios, a conversao e mais especifica — voce precisa de pares chave-valor.

**P: O que e "fatiamento" (slicing)?**
R: E uma forma de pegar um pedaco de uma lista ou tupla usando a sintaxe `[inicio:fim]`. O inicio e incluido e o fim nao. Exemplo: `[1, 2, 3, 4, 5][1:3]` retorna `[2, 3]`.

**P: Posso usar for para percorrer qualquer estrutura de dados?**
R: Sim! O `for` funciona com listas, tuplas, dicionarios, conjuntos e strings. Em dicionarios, o `for` percorre as chaves por padrao. Use `.values()` para percorrer valores e `.items()` para percorrer pares chave-valor.

**P: O que e "unpacking" de tupla?**
R: E extrair os valores de uma tupla para variaveis separadas. Exemplo: `x, y = (10, 20)` coloca 10 em `x` e 20 em `y`. O numero de variaveis deve ser igual ao numero de itens na tupla.

**P: E normal achar estruturas de dados confusas no inicio?**
R: Completamente normal! Estruturas de dados sao um dos topicos mais importantes da programacao e levam tempo para dominar. A dica e praticar bastante com os exercicios e voltar a este modulo sempre que precisar. Com o tempo, voce vai saber instintivamente qual estrutura usar em cada situacao.

**P: Preciso decorar todos os metodos de lista e dicionario?**
R: Nao! Programadores profissionais consultam a documentacao o tempo todo. O importante e saber que os metodos existem e onde encontra-los. Com a pratica, os mais usados (como `append`, `get`, `keys`) ficam naturais.

---

## Exercicios de Fixacao

Os exercicios deste modulo estao em um arquivo separado:

**[Acessar Exercicios do Modulo 19](19-estruturas-dados-exercicios.md)**

---

[<- Anterior: Tratamento de Erros](18-tratamento-erros.md) | [Glossario](00-glossario.md) | [Proximo: Leitura e Escrita de Arquivos ->](20-leitura-escrita-arquivos.md)
