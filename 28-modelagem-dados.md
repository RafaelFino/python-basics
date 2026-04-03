# 28 — Modelagem de Dados: Planejamento Conceitual

[<- Anterior: Boas Praticas](27-boas-praticas.md) | [Glossario](00-glossario.md) | [Proximo: CRUD em Memoria ->](29-crud-memoria.md)

---

## Introducao

No modulo anterior, voce aprendeu boas praticas para escrever codigo limpo e profissional. Agora vamos dar um passo muito importante antes de comecar a construir o nosso projeto CRUD: **planejar os dados**.

Imagine que voce vai abrir uma loja e precisa criar fichas cadastrais para todos os seus produtos. Antes de preencher qualquer ficha, voce precisa decidir: quais informacoes vou anotar? Nome do produto? Preco? Quantidade em estoque? Categoria? Cada uma dessas informacoes e um **campo** da ficha.

Esse processo de planejar quais informacoes voce precisa guardar, como elas se organizam e quais regras elas devem seguir se chama **modelagem de dados**. E como desenhar a planta de uma casa antes de comecar a construir — voce decide quantos comodos vai ter, onde fica cada um e qual o tamanho de cada porta, tudo antes de colocar o primeiro tijolo.

Neste modulo, voce vai aprender:

- O que e modelagem de dados e por que planejar antes de programar
- Como identificar os campos de uma entidade (como um produto)
- Como escolher o tipo de dado certo para cada campo
- Como representar um modelo de dados usando dicionarios Python
- Como validar dados de entrada para evitar informacoes incorretas
- Como preparar o modelo de dados para o projeto CRUD que comecaremos no proximo modulo

> **Dica:** Consulte o [Glossario](00-glossario.md) sempre que encontrar um termo desconhecido.

---

## O Que e Modelagem de Dados?

**Modelagem de dados** e o processo de planejar como as informacoes serao organizadas antes de escrever qualquer codigo. E pensar sobre os dados antes de trabalhar com eles.

**Analogia:** Pense em uma ficha de cadastro de paciente em um consultorio medico. Antes de atender o primeiro paciente, alguem precisou decidir quais informacoes a ficha teria: nome, data de nascimento, telefone, endereco, alergias, convenio. Essa decisao de "quais campos a ficha vai ter" e exatamente o que fazemos na modelagem de dados.

Outro exemplo: quando voce vai ao mercado e faz uma lista de compras, voce decide quais informacoes anotar. Algumas pessoas escrevem apenas o nome do produto. Outras anotam tambem a quantidade e o preco estimado. Essa decisao sobre "o que anotar" e modelagem de dados no dia a dia.

Em programacao, modelar dados significa responder a tres perguntas fundamentais:

1. **Quais informacoes preciso guardar?** (os campos)
2. **Que tipo de dado cada informacao tem?** (texto, numero, verdadeiro/falso)
3. **Quais regras cada informacao deve seguir?** (validacoes)

---

## Por Que Planejar Antes de Programar?

Voce pode estar pensando: "por que nao comeco logo a programar e vou ajustando depois?". Essa e uma pergunta muito boa, e a resposta e simples: **planejar economiza tempo e evita retrabalho**.

**Analogia:** Imagine que voce vai construir um armario para guardar suas roupas. Se voce comeca a cortar a madeira sem medir, sem desenhar, sem planejar quantas prateleiras precisa, o resultado provavelmente vai ser um armario torto, com prateleiras que nao cabem suas roupas. Mas se voce planeja antes — mede o espaco, decide quantas prateleiras, calcula o tamanho de cada uma — o armario fica perfeito de primeira.

Em programacao, acontece a mesma coisa:

- **Sem planejamento:** Voce comeca a programar, percebe que esqueceu um campo, muda a estrutura, quebra o codigo que ja funcionava, perde tempo corrigindo
- **Com planejamento:** Voce define todos os campos, tipos e regras antes de escrever a primeira linha de codigo, e o programa funciona de forma organizada desde o inicio

No nosso caso, vamos planejar o modelo de dados de um **cadastro de produtos** — o mesmo que usaremos nos proximos quatro modulos para construir o projeto CRUD completo.

---

## Identificando os Campos de uma Entidade

Uma **entidade** e qualquer "coisa" sobre a qual voce precisa guardar informacoes. No nosso caso, a entidade e um **produto** de uma loja.

**Analogia:** Pense em uma ficha cadastral de uma biblioteca. A entidade e o "livro", e os campos sao as informacoes que voce anota sobre cada livro: titulo, autor, editora, ano de publicacao, numero de paginas. Cada campo e uma informacao especifica sobre a entidade.

Para identificar os campos de uma entidade, faca a pergunta: **"Quais informacoes eu preciso saber sobre esse produto?"**

Para o nosso cadastro de produtos, precisamos saber:

| Campo | Descricao | Exemplo |
|-------|-----------|---------|
| Identificador | Um numero unico para cada produto | 1, 2, 3... |
| Nome | O nome do produto | "Arroz Integral" |
| Preco | Quanto o produto custa | 8.99 |
| Quantidade | Quantas unidades temos em estoque | 50 |
| Categoria | O tipo/grupo do produto | "Alimentos" |

Veja como isso se parece em Python:

```python
# Exemplo de uma entidade "produto" representada como dicionario
# "product" = produto
product = {
    "id": 1,                    # Identificador unico do produto (id = identificador)
    "name": "Arroz Integral",   # Nome do produto (name = nome)
    "price": 8.99,              # Preco do produto (price = preco)
    "quantity": 50,             # Quantidade em estoque (quantity = quantidade)
    "category": "Alimentos"     # Categoria do produto (category = categoria)
}

# Exibimos cada campo do produto
# print() mostra o texto no terminal
print(f"Produto: {product['name']}")
print(f"Preco: R$ {product['price']}")
print(f"Quantidade: {product['quantity']} unidades")
print(f"Categoria: {product['category']}")
```

Saida esperada:
```
Produto: Arroz Integral
Preco: R$ 8.99
Quantidade: 50 unidades
Categoria: Alimentos
```

Cada **chave** do dicionario e um campo da nossa entidade, e cada **valor** e a informacao armazenada naquele campo. Voce ja aprendeu sobre dicionarios no modulo 19 — agora estamos usando esse conhecimento para modelar dados de forma organizada.

---

## Escolhendo o Tipo de Dado Adequado para Cada Campo

Depois de identificar os campos, o proximo passo e decidir qual **tipo de dado** cada campo deve ter. Essa decisao e muito importante porque o tipo de dado determina o que voce pode fazer com aquela informacao.

**Analogia:** Pense em um formulario de papel. Alguns campos pedem que voce escreva um texto (nome, endereco), outros pedem que voce escreva um numero (idade, telefone), e outros pedem que voce marque "sim" ou "nao" (tem alergia? tem convenio?). Cada campo tem um tipo de informacao esperado. Se alguem escreve "vinte e cinco" no campo de idade em vez de "25", fica dificil fazer calculos depois.

Em Python, os tipos de dados que usamos com mais frequencia sao:

| Tipo Python | Nome em Portugues | Quando Usar | Exemplo |
|-------------|-------------------|-------------|---------|
| `str` | Texto (string) | Nomes, descricoes, categorias | `"Arroz"` |
| `int` | Numero inteiro | Contagens, identificadores, quantidades | `50` |
| `float` | Numero decimal | Precos, medidas, porcentagens | `8.99` |
| `bool` | Verdadeiro/Falso | Situacoes de sim/nao, ativo/inativo | `True` |
| `list` | Lista | Colecoes de itens relacionados | `["tag1", "tag2"]` |

Agora vamos aplicar isso ao nosso modelo de produto:

```python
# Modelo de produto com tipos de dados adequados
# "product" = produto, "model" = modelo
product_model = {
    "id": 1,                    # int — identificador unico (numero inteiro, nunca decimal)
    "name": "Arroz Integral",   # str — nome do produto (texto)
    "price": 8.99,              # float — preco em reais (numero decimal, pois centavos existem)
    "quantity": 50,             # int — quantidade em estoque (numero inteiro, nao existe meia unidade)
    "category": "Alimentos"     # str — categoria do produto (texto)
}

# Verificamos o tipo de cada campo usando type()
# type() retorna o tipo de dado de um valor
print(f"id: {type(product_model['id'])}")
print(f"name: {type(product_model['name'])}")
print(f"price: {type(product_model['price'])}")
print(f"quantity: {type(product_model['quantity'])}")
print(f"category: {type(product_model['category'])}")
```

Saida esperada:
```
id: <class 'int'>
name: <class 'str'>
price: <class 'float'>
quantity: <class 'int'>
category: <class 'str'>
```

### Por Que Cada Tipo Foi Escolhido?

Vamos entender a razao de cada escolha:

- **id (int):** O identificador e um numero inteiro sequencial (1, 2, 3...). Nunca sera 1.5 ou "um". Usar `int` permite comparacoes e incrementos simples.

- **name (str):** O nome do produto e um texto. Pode conter letras, numeros, espacos e caracteres especiais. Usar `str` e a escolha natural para textos.

- **price (float):** O preco tem centavos (8.99, 12.50, 3.75). Precisamos de um numero decimal, por isso usamos `float`. Se usassemos `int`, perderiamos os centavos.

- **quantity (int):** A quantidade em estoque e um numero inteiro. Voce tem 50 unidades, nao 50.5 unidades. Usar `int` garante que a quantidade seja sempre um numero inteiro.

- **category (str):** A categoria e um texto descritivo como "Alimentos", "Limpeza" ou "Higiene". Usar `str` e a escolha adequada.

Veja o que acontece quando escolhemos o tipo errado:

```python
# Exemplo de tipo ERRADO para preco
# "wrong" = errado, "price" = preco
wrong_price = 8  # int — perdemos os centavos!
# "correct" = correto
correct_price = 8.99  # float — centavos preservados

# Exibimos a diferenca
print(f"Preco errado (int): R$ {wrong_price}")
print(f"Preco correto (float): R$ {correct_price}")

# Exemplo de tipo ERRADO para quantidade
# "wrong" = errado, "quantity" = quantidade
wrong_quantity = "50"  # str — nao podemos fazer calculos!
# "correct" = correto
correct_quantity = 50  # int — podemos somar, subtrair, comparar

# Tentamos somar 10 unidades
# Com int funciona perfeitamente
print(f"Estoque apos receber 10 unidades: {correct_quantity + 10}")
# Com str, o resultado seria concatenacao, nao soma
print(f"Estoque errado (str + str): {wrong_quantity + '10'}")
```

Saida esperada:
```
Preco errado (int): R$ 8
Preco correto (float): R$ 8.99
Estoque apos receber 10 unidades: 60
Estoque errado (str + str): 5010
```

Perceba como usar `str` para a quantidade causou um problema grave: em vez de somar 50 + 10 = 60, o Python concatenou os textos "50" + "10" = "5010". Escolher o tipo certo evita erros como esse.

---

## Representando o Modelo com Dicionarios Python

Agora que sabemos quais campos precisamos e qual tipo cada um tem, vamos criar o modelo completo usando dicionarios Python. Um dicionario e a forma mais natural de representar uma entidade com campos nomeados.

**Analogia:** Um dicionario Python funciona como uma ficha cadastral: cada campo tem um nome (a chave) e um valor preenchido. Assim como voce pode ter varias fichas em uma pasta, voce pode ter varios dicionarios em uma lista.

### Um Unico Produto (Dicionario)

```python
# Um produto representado como dicionario
# "product" = produto
product = {
    "id": 1,                    # Identificador unico (id = identificador)
    "name": "Cafe Torrado",     # Nome do produto (name = nome)
    "price": 15.90,             # Preco em reais (price = preco)
    "quantity": 30,             # Quantidade em estoque (quantity = quantidade)
    "category": "Alimentos"     # Categoria (category = categoria)
}

# Acessamos cada campo usando a chave entre colchetes
# print() mostra o texto no terminal
print(f"ID: {product['id']}")
print(f"Nome: {product['name']}")
print(f"Preco: R$ {product['price']:.2f}")
print(f"Estoque: {product['quantity']} unidades")
print(f"Categoria: {product['category']}")
```

Saida esperada:
```
ID: 1
Nome: Cafe Torrado
Preco: R$ 15.90
Estoque: 30 unidades
Categoria: Alimentos
```

### Varios Produtos (Lista de Dicionarios)

Para armazenar varios produtos, usamos uma **lista de dicionarios**. Cada elemento da lista e um dicionario representando um produto.

```python
# Lista de produtos — cada produto e um dicionario
# "products" = produtos (lista)
products = [
    {
        "id": 1,                        # Identificador do primeiro produto
        "name": "Arroz Integral",       # Nome (name = nome)
        "price": 8.99,                  # Preco (price = preco)
        "quantity": 50,                 # Quantidade (quantity = quantidade)
        "category": "Alimentos"         # Categoria (category = categoria)
    },
    {
        "id": 2,                        # Identificador do segundo produto
        "name": "Detergente Neutro",    # Nome (name = nome)
        "price": 3.50,                  # Preco (price = preco)
        "quantity": 100,                # Quantidade (quantity = quantidade)
        "category": "Limpeza"           # Categoria (category = categoria)
    },
    {
        "id": 3,                        # Identificador do terceiro produto
        "name": "Shampoo Infantil",     # Nome (name = nome)
        "price": 12.75,                 # Preco (price = preco)
        "quantity": 25,                 # Quantidade (quantity = quantidade)
        "category": "Higiene"           # Categoria (category = categoria)
    }
]

# Percorremos a lista e exibimos cada produto
# "product" = produto (cada item da lista)
for product in products:
    # Exibimos os dados formatados
    print(f"[{product['id']}] {product['name']} - R$ {product['price']:.2f} ({product['quantity']} un.) - {product['category']}")
```

Saida esperada:
```
[1] Arroz Integral - R$ 8.99 (50 un.) - Alimentos
[2] Detergente Neutro - R$ 3.50 (100 un.) - Limpeza
[3] Shampoo Infantil - R$ 12.75 (25 un.) - Higiene
```

Essa estrutura — uma lista de dicionarios — e exatamente o que usaremos no modulo 29 para criar o CRUD em memoria. Cada operacao do CRUD (criar, ler, atualizar, excluir) vai manipular essa lista.

### Criando Produtos com uma Funcao

Para manter o codigo organizado, podemos criar uma funcao que monta o dicionario do produto:

```python
# Funcao que cria um dicionario de produto
# "create" = criar, "product" = produto
def create_product(product_id, name, price, quantity, category):
    """Cria e retorna um dicionario representando um produto."""
    # Montamos o dicionario com os dados recebidos
    # "product" = produto
    product = {
        "id": product_id,          # Identificador unico (id = identificador)
        "name": name,              # Nome do produto (name = nome)
        "price": price,            # Preco do produto (price = preco)
        "quantity": quantity,       # Quantidade em estoque (quantity = quantidade)
        "category": category        # Categoria do produto (category = categoria)
    }
    # Retornamos o dicionario pronto
    return product


# Criamos tres produtos usando a funcao
# "product" = produto
product_1 = create_product(1, "Feijao Preto", 7.50, 40, "Alimentos")
product_2 = create_product(2, "Sabao em Po", 14.90, 60, "Limpeza")
product_3 = create_product(3, "Escova de Dentes", 5.99, 80, "Higiene")

# Exibimos os produtos criados
print(f"Produto 1: {product_1}")
print(f"Produto 2: {product_2}")
print(f"Produto 3: {product_3}")
```

Saida esperada:
```
Produto 1: {'id': 1, 'name': 'Feijao Preto', 'price': 7.5, 'quantity': 40, 'category': 'Alimentos'}
Produto 2: {'id': 2, 'name': 'Sabao em Po', 'price': 14.9, 'quantity': 60, 'category': 'Limpeza'}
Produto 3: {'id': 3, 'name': 'Escova de Dentes', 'price': 5.99, 'quantity': 80, 'category': 'Higiene'}
```

---

## Validacao de Dados de Entrada

Agora vem uma parte muito importante: **validar os dados antes de aceita-los**. Validacao significa verificar se os dados fazem sentido antes de armazena-los.

**Analogia:** Quando voce preenche um formulario online, o site verifica se o email tem o formato correto, se o telefone tem a quantidade certa de digitos, se a data de nascimento nao e no futuro. Essas verificacoes sao validacoes — elas impedem que dados incorretos entrem no sistema.

No nosso cadastro de produtos, precisamos validar:

| Campo | Regra de Validacao | Por Que? |
|-------|-------------------|----------|
| name | Nao pode ser vazio | Um produto sem nome nao faz sentido |
| price | Deve ser maior ou igual a zero | Preco negativo nao existe |
| quantity | Deve ser um numero inteiro maior ou igual a zero | Nao existe estoque negativo |
| category | Nao pode ser vazio | Todo produto precisa de uma categoria |

### Validacao Simples com Condicionais

```python
# Funcao que valida os dados de um produto
# "validate" = validar, "product" = produto, "data" = dados
def validate_product_data(name, price, quantity, category):
    """Valida os dados de um produto e retorna uma lista de erros."""
    # "errors" = erros (lista que armazena mensagens de erro)
    errors = []

    # Validacao do nome: nao pode ser vazio
    # strip() remove espacos em branco das pontas
    if not name or name.strip() == "":
        # Adicionamos uma mensagem de erro a lista
        errors.append("O nome do produto nao pode ser vazio")

    # Validacao do preco: deve ser um numero maior ou igual a zero
    if not isinstance(price, (int, float)):
        # isinstance() verifica se o valor e do tipo esperado
        errors.append("O preco deve ser um numero")
    elif price < 0:
        # Preco negativo nao faz sentido
        errors.append("O preco nao pode ser negativo")

    # Validacao da quantidade: deve ser um numero inteiro maior ou igual a zero
    if not isinstance(quantity, int):
        # A quantidade deve ser inteira (nao existe meia unidade)
        errors.append("A quantidade deve ser um numero inteiro")
    elif quantity < 0:
        # Estoque negativo nao faz sentido
        errors.append("A quantidade nao pode ser negativa")

    # Validacao da categoria: nao pode ser vazia
    if not category or category.strip() == "":
        # Adicionamos uma mensagem de erro a lista
        errors.append("A categoria nao pode ser vazia")

    # Retornamos a lista de erros (vazia se tudo estiver correto)
    return errors


# Testamos com dados validos
# "errors" = erros
errors = validate_product_data("Arroz", 8.99, 50, "Alimentos")
# Verificamos se a lista de erros esta vazia
if len(errors) == 0:
    print("Dados validos! Produto pode ser cadastrado.")
else:
    print("Erros encontrados:")
    # Percorremos cada erro e exibimos
    # "error" = erro
    for error in errors:
        print(f"  - {error}")
```

Saida esperada:
```
Dados validos! Produto pode ser cadastrado.
```

Agora vamos testar com dados invalidos:

```python
# Funcao que valida os dados de um produto (mesma funcao anterior)
# "validate" = validar, "product" = produto, "data" = dados
def validate_product_data(name, price, quantity, category):
    """Valida os dados de um produto e retorna uma lista de erros."""
    # "errors" = erros
    errors = []
    # Validacao do nome
    if not name or name.strip() == "":
        errors.append("O nome do produto nao pode ser vazio")
    # Validacao do preco
    if not isinstance(price, (int, float)):
        errors.append("O preco deve ser um numero")
    elif price < 0:
        errors.append("O preco nao pode ser negativo")
    # Validacao da quantidade
    if not isinstance(quantity, int):
        errors.append("A quantidade deve ser um numero inteiro")
    elif quantity < 0:
        errors.append("A quantidade nao pode ser negativa")
    # Validacao da categoria
    if not category or category.strip() == "":
        errors.append("A categoria nao pode ser vazia")
    # Retornamos a lista de erros
    return errors


# Testamos com dados INVALIDOS
# Nome vazio, preco negativo, quantidade negativa, categoria vazia
errors = validate_product_data("", -5.00, -10, "")
# Verificamos se ha erros
if len(errors) == 0:
    print("Dados validos!")
else:
    print("Erros encontrados:")
    # "error" = erro
    for error in errors:
        print(f"  - {error}")
```

Saida esperada:
```
Erros encontrados:
  - O nome do produto nao pode ser vazio
  - O preco nao pode ser negativo
  - A quantidade nao pode ser negativa
  - A categoria nao pode ser vazia
```

### Combinando Validacao com Criacao

Agora vamos juntar a validacao com a funcao de criacao para garantir que so criamos produtos com dados validos:

```python
# Funcao que valida os dados de um produto
# "validate" = validar, "product" = produto, "data" = dados
def validate_product_data(name, price, quantity, category):
    """Valida os dados de um produto e retorna uma lista de erros."""
    # "errors" = erros
    errors = []
    # Validacao do nome: nao pode ser vazio
    if not name or name.strip() == "":
        errors.append("O nome do produto nao pode ser vazio")
    # Validacao do preco: deve ser numero >= 0
    if not isinstance(price, (int, float)):
        errors.append("O preco deve ser um numero")
    elif price < 0:
        errors.append("O preco nao pode ser negativo")
    # Validacao da quantidade: deve ser inteiro >= 0
    if not isinstance(quantity, int):
        errors.append("A quantidade deve ser um numero inteiro")
    elif quantity < 0:
        errors.append("A quantidade nao pode ser negativa")
    # Validacao da categoria: nao pode ser vazia
    if not category or category.strip() == "":
        errors.append("A categoria nao pode ser vazia")
    return errors


# Funcao que cria um produto somente se os dados forem validos
# "create" = criar, "validated" = validado
def create_validated_product(product_id, name, price, quantity, category):
    """Cria um produto somente se os dados passarem na validacao."""
    # Primeiro validamos os dados
    # "errors" = erros
    errors = validate_product_data(name, price, quantity, category)

    # Se houver erros, exibimos e retornamos None (nenhum produto criado)
    if len(errors) > 0:
        print(f"Erro ao criar produto '{name}':")
        # "error" = erro
        for error in errors:
            print(f"  - {error}")
        # None significa "nenhum valor" — o produto nao foi criado
        return None

    # Se nao houver erros, criamos o dicionario do produto
    # "product" = produto
    product = {
        "id": product_id,
        "name": name,
        "price": price,
        "quantity": quantity,
        "category": category
    }
    # Informamos que o produto foi criado com sucesso
    print(f"Produto '{name}' criado com sucesso!")
    return product


# Testamos com dados validos
# "product" = produto
product_1 = create_validated_product(1, "Arroz", 8.99, 50, "Alimentos")

# Testamos com dados invalidos (preco negativo)
product_2 = create_validated_product(2, "Feijao", -3.00, 30, "Alimentos")

# Verificamos os resultados
# None significa que o produto nao foi criado
print(f"\nProduto 1: {product_1}")
print(f"Produto 2: {product_2}")
```

Saida esperada:
```
Produto 'Arroz' criado com sucesso!
Erro ao criar produto 'Feijao':
  - O preco nao pode ser negativo

Produto 1: {'id': 1, 'name': 'Arroz', 'price': 8.99, 'quantity': 50, 'category': 'Alimentos'}
Produto 2: None
```

---

## Validacao de Dados Digitados pelo Usuario

No projeto CRUD, os dados virao do usuario atraves do teclado (funcao `input()`). Isso traz um desafio extra: o usuario pode digitar qualquer coisa, e precisamos lidar com isso.

**Analogia:** Imagine um caixa de supermercado que precisa digitar o preco de um produto. Se ele digitar "abc" em vez de um numero, o sistema precisa avisar que o valor e invalido e pedir para digitar novamente. Nosso programa precisa fazer a mesma coisa.

```python
# Funcao que le um numero decimal do usuario com validacao
# "read" = ler, "price" = preco, "input" = entrada
def read_price():
    """Le um preco valido do usuario (numero decimal >= 0)."""
    # Loop que repete ate o usuario digitar um valor valido
    # "while True" cria um loop infinito que so para com "break"
    while True:
        # Pedimos ao usuario que digite o preco
        # "user" = usuario, "input" = entrada
        user_input = input("Digite o preco do produto: R$ ")
        # Tentamos converter o texto para numero decimal
        try:
            # float() converte texto para numero decimal
            # "price" = preco
            price = float(user_input)
            # Verificamos se o preco nao e negativo
            if price < 0:
                print("Erro: o preco nao pode ser negativo. Tente novamente.")
            else:
                # Preco valido — saimos do loop
                return price
        except ValueError:
            # Se a conversao falhar, o usuario digitou algo que nao e numero
            # ValueError = erro de valor (o texto nao pode ser convertido)
            print("Erro: digite um numero valido. Exemplo: 8.99")


# Funcao que le um numero inteiro do usuario com validacao
# "read" = ler, "quantity" = quantidade
def read_quantity():
    """Le uma quantidade valida do usuario (numero inteiro >= 0)."""
    # Loop que repete ate o usuario digitar um valor valido
    while True:
        # Pedimos ao usuario que digite a quantidade
        user_input = input("Digite a quantidade em estoque: ")
        # Tentamos converter o texto para numero inteiro
        try:
            # int() converte texto para numero inteiro
            # "quantity" = quantidade
            quantity = int(user_input)
            # Verificamos se a quantidade nao e negativa
            if quantity < 0:
                print("Erro: a quantidade nao pode ser negativa. Tente novamente.")
            else:
                # Quantidade valida — saimos do loop
                return quantity
        except ValueError:
            # Se a conversao falhar, o usuario digitou algo que nao e inteiro
            print("Erro: digite um numero inteiro valido. Exemplo: 50")


# Funcao que le um texto nao vazio do usuario
# "read" = ler, "not" = nao, "empty" = vazio, "text" = texto
def read_not_empty_text(prompt):
    """Le um texto nao vazio do usuario."""
    # "prompt" = mensagem exibida ao usuario
    while True:
        # Pedimos ao usuario que digite o texto
        # "text" = texto
        text = input(prompt)
        # strip() remove espacos em branco das pontas
        if text.strip() == "":
            print("Erro: este campo nao pode ficar vazio. Tente novamente.")
        else:
            # Texto valido — retornamos sem espacos extras
            return text.strip()


# Exemplo de uso (simulacao — em um programa real, o usuario digitaria)
print("=== Cadastro de Produto ===")
print("(Este exemplo mostra como as funcoes seriam usadas)")
print("(No proximo modulo, voce vai usar essas funcoes no CRUD)")
```

Saida esperada:
```
=== Cadastro de Produto ===
(Este exemplo mostra como as funcoes seriam usadas)
(No proximo modulo, voce vai usar essas funcoes no CRUD)
```

Essas funcoes de leitura com validacao serao muito uteis no modulo 29, quando construiremos o CRUD completo com interface de terminal.

---

## Modelo Completo para o Projeto CRUD

Vamos reunir tudo o que aprendemos em um modelo completo que sera a base do nosso projeto CRUD:

```python
# ============================================================
# Modelo de dados para o Cadastro de Produtos
# Este modelo sera usado nos modulos 29 a 32 (projeto CRUD)
# ============================================================

# Lista que armazena todos os produtos cadastrados
# "products" = produtos (lista vazia no inicio)
products = []

# Contador para gerar identificadores unicos
# "next" = proximo, "id" = identificador
next_id = 1


# Funcao que valida os dados de um produto
# "validate" = validar, "product" = produto, "data" = dados
def validate_product_data(name, price, quantity, category):
    """Valida os dados e retorna uma lista de erros encontrados."""
    # "errors" = erros
    errors = []
    # Nome nao pode ser vazio
    if not name or name.strip() == "":
        errors.append("O nome nao pode ser vazio")
    # Preco deve ser numero >= 0
    if not isinstance(price, (int, float)):
        errors.append("O preco deve ser um numero")
    elif price < 0:
        errors.append("O preco nao pode ser negativo")
    # Quantidade deve ser inteiro >= 0
    if not isinstance(quantity, int):
        errors.append("A quantidade deve ser um numero inteiro")
    elif quantity < 0:
        errors.append("A quantidade nao pode ser negativa")
    # Categoria nao pode ser vazia
    if not category or category.strip() == "":
        errors.append("A categoria nao pode ser vazia")
    return errors


# Funcao que cria um produto validado e adiciona a lista
# "add" = adicionar, "product" = produto
def add_product(name, price, quantity, category):
    """Cria um produto validado e adiciona a lista de produtos."""
    # Usamos "global" para acessar a variavel next_id definida fora da funcao
    global next_id

    # Validamos os dados antes de criar
    errors = validate_product_data(name, price, quantity, category)

    # Se houver erros, exibimos e nao criamos o produto
    if len(errors) > 0:
        print(f"Erro ao cadastrar produto:")
        for error in errors:
            print(f"  - {error}")
        return None

    # Criamos o dicionario do produto
    # "product" = produto
    product = {
        "id": next_id,
        "name": name,
        "price": price,
        "quantity": quantity,
        "category": category
    }

    # Adicionamos o produto a lista
    # append() adiciona um item ao final da lista
    products.append(product)

    # Incrementamos o contador de identificadores
    next_id = next_id + 1

    # Informamos o sucesso
    print(f"Produto '{name}' cadastrado com ID {product['id']}")
    return product


# Cadastramos alguns produtos de exemplo
add_product("Arroz Integral", 8.99, 50, "Alimentos")
add_product("Detergente", 3.50, 100, "Limpeza")
add_product("Shampoo", 12.75, 25, "Higiene")
add_product("", -5.00, -10, "")  # Dados invalidos — sera rejeitado

# Exibimos todos os produtos cadastrados
print(f"\nTotal de produtos cadastrados: {len(products)}")
# "product" = produto
for product in products:
    print(f"  [{product['id']}] {product['name']} - R$ {product['price']:.2f}")
```

Saida esperada:
```
Produto 'Arroz Integral' cadastrado com ID 1
Produto 'Detergente' cadastrado com ID 2
Produto 'Shampoo' cadastrado com ID 3
Erro ao cadastrar produto:
  - O nome nao pode ser vazio
  - O preco nao pode ser negativo
  - A quantidade nao pode ser negativa
  - A categoria nao pode ser vazia

Total de produtos cadastrados: 3
  [1] Arroz Integral - R$ 8.99
  [2] Detergente - R$ 3.50
  [3] Shampoo - R$ 12.75
```

Este modelo completo ja tem a estrutura basica que usaremos no projeto CRUD. No modulo 29, vamos expandir esse modelo adicionando as operacoes de leitura, atualizacao e exclusao, alem de uma interface de menu no terminal.

---

## Para Saber Mais

- [W3Schools — Dicionarios em Python](https://www.w3schools.com/python/python_dictionaries.asp)
  _Aqui voce encontra mais exemplos de como criar e manipular dicionarios, que sao a base da nossa modelagem de dados_

- [W3Schools — Tipos de Dados em Python](https://www.w3schools.com/python/python_datatypes.asp)
  _Referencia completa sobre todos os tipos de dados do Python, incluindo str, int, float e bool_

- [W3Schools — Funcoes em Python](https://www.w3schools.com/python/python_functions.asp)
  _Revisao sobre funcoes, que usamos para criar e validar produtos_

- [Documentacao Oficial Python — Tipos Embutidos](https://docs.python.org/pt-br/3/library/stdtypes.html)
  _Referencia tecnica completa sobre os tipos de dados do Python_

- [Documentacao Oficial Python — Dicionarios](https://docs.python.org/pt-br/3/tutorial/datastructures.html#dictionaries)
  _Tutorial oficial sobre dicionarios com exemplos detalhados_

- [W3Schools — Try/Except em Python](https://www.w3schools.com/python/python_try_except.asp)
  _Revisao sobre tratamento de erros, que usamos na validacao de dados digitados pelo usuario_

---

## Perguntas Frequentes (FAQ)

**P: O que e modelagem de dados?**
**R:** Modelagem de dados e o processo de planejar como as informacoes serao organizadas antes de escrever codigo. E como desenhar a planta de uma casa antes de construir — voce decide quais campos (informacoes) precisa, qual o tipo de cada campo e quais regras os dados devem seguir.

**P: Por que preciso planejar os dados antes de programar?**
**R:** Planejar evita retrabalho. Se voce comeca a programar sem saber quais dados vai usar, provavelmente vai precisar mudar a estrutura depois, o que pode quebrar o codigo que ja funcionava. Com um modelo definido, voce programa com seguranca desde o inicio.

**P: O que e uma entidade?**
**R:** Uma entidade e qualquer "coisa" sobre a qual voce precisa guardar informacoes. No nosso caso, a entidade e um "produto". Em outros sistemas, entidades podem ser "cliente", "pedido", "aluno", "livro" — qualquer coisa que tenha dados associados.

**P: O que e um campo?**
**R:** Um campo e uma informacao especifica sobre uma entidade. Por exemplo, o campo "nome" de um produto guarda o nome do produto, o campo "preco" guarda o preco. E como cada linha de uma ficha cadastral.

**P: Por que usar dicionarios para representar entidades?**
**R:** Dicionarios sao perfeitos para representar entidades porque cada campo tem um nome (a chave) e um valor. Isso torna o codigo legivel e organizado. Quando voce escreve `product["name"]`, fica claro que esta acessando o nome do produto.

**P: Posso usar uma lista em vez de um dicionario para representar um produto?**
**R:** Tecnicamente sim, mas nao e recomendado. Com uma lista, voce acessaria os campos por posicao (`product[0]` para o nome, `product[1]` para o preco), o que torna o codigo confuso. Com um dicionario, voce acessa por nome (`product["name"]`), que e muito mais claro.

**P: O que significa validar dados?**
**R:** Validar dados significa verificar se as informacoes fazem sentido antes de aceita-las. Por exemplo: verificar se o preco nao e negativo, se o nome nao esta vazio, se a quantidade e um numero inteiro. Validacao impede que dados incorretos entrem no sistema.

**P: Por que o preco e float e nao int?**
**R:** Porque precos tem centavos. Um produto pode custar R$ 8.99, e o tipo `int` so armazena numeros inteiros (sem casas decimais). O tipo `float` armazena numeros com casas decimais, perfeito para representar valores monetarios.

**P: Por que a quantidade e int e nao float?**
**R:** Porque a quantidade em estoque e sempre um numero inteiro. Voce tem 50 unidades de um produto, nao 50.5 unidades. Usar `int` garante que ninguem cadastre uma quantidade como 3.7, o que nao faria sentido.

**P: O que e o campo "id" e por que ele e importante?**
**R:** O campo "id" (identificador) e um numero unico que diferencia cada produto dos demais. Mesmo que dois produtos tenham o mesmo nome, eles terao ids diferentes. E como o numero de matricula de um aluno — cada aluno tem um numero unico, mesmo que dois alunos tenham o mesmo nome.

**P: O que acontece se eu nao validar os dados?**
**R:** Sem validacao, dados incorretos podem entrar no sistema e causar problemas. Um preco negativo pode gerar calculos errados, um nome vazio pode confundir o usuario, uma quantidade como "abc" pode causar erros no programa. Validacao e uma camada de protecao.

**P: O que e isinstance() e para que serve?**
**R:** A funcao `isinstance()` verifica se um valor e de um determinado tipo. Por exemplo, `isinstance(50, int)` retorna `True` porque 50 e um numero inteiro. Usamos essa funcao na validacao para garantir que o preco e um numero e que a quantidade e um inteiro.

**P: O que significa None em Python?**
**R:** `None` e um valor especial que significa "nenhum valor" ou "vazio". Quando uma funcao retorna `None`, significa que ela nao produziu um resultado. No nosso caso, a funcao de criacao retorna `None` quando os dados sao invalidos, indicando que o produto nao foi criado.

**P: O que e a palavra-chave global?**
**R:** A palavra-chave `global` permite que uma funcao modifique uma variavel definida fora dela. No nosso exemplo, usamos `global next_id` para que a funcao `add_product` possa incrementar o contador de identificadores. Sem `global`, a funcao criaria uma variavel local com o mesmo nome, sem alterar a original.

**P: Posso ter mais campos no meu produto?**
**R:** Sim, voce pode adicionar quantos campos quiser. Por exemplo: "marca", "peso", "data_de_validade", "fornecedor". O importante e que cada campo tenha um proposito claro e um tipo de dado adequado. No nosso projeto CRUD, usamos cinco campos para manter a simplicidade.

**P: E normal achar dificil pensar nos campos de uma entidade?**
**R:** Sim, completamente normal. Modelar dados e uma habilidade que melhora com a pratica. No inicio, voce pode esquecer campos ou escolher tipos errados — e tudo bem. O importante e pensar antes de programar, mesmo que o modelo nao fique perfeito de primeira.

**P: O que e um CRUD?**
**R:** CRUD e uma sigla em ingles para as quatro operacoes basicas de um cadastro: Create (criar), Read (ler), Update (atualizar) e Delete (excluir). Nos proximos modulos, voce vai construir um sistema CRUD completo para o cadastro de produtos que estamos modelando aqui.

**P: Vou usar esse modelo de produto nos proximos modulos?**
**R:** Sim! O modelo que definimos aqui (id, name, price, quantity, category) sera usado nos modulos 29 a 32. No modulo 29, criaremos o CRUD em memoria. No 30, adicionaremos banco de dados SQLite. No 31, criaremos uma API HTTP com FastAPI. E no 32, adicionaremos documentacao Swagger.

**P: Qual a diferenca entre modelagem de dados e banco de dados?**
**R:** Modelagem de dados e o planejamento — decidir quais informacoes guardar e como organiza-las. Banco de dados e onde os dados sao efetivamente armazenados. Primeiro voce modela (planeja), depois implementa (armazena). Neste modulo, estamos modelando. No modulo 30, usaremos um banco de dados (SQLite).

**P: Preciso decorar todas as funcoes de validacao?**
**R:** Nao. O importante e entender o conceito: antes de aceitar dados, verifique se eles fazem sentido. As funcoes especificas voce pode consultar e adaptar conforme a necessidade. Com a pratica, escrever validacoes se torna natural.

---

## Exercicios de Fixacao

Os exercicios deste modulo estao no arquivo separado: [Exercicios — Modelagem de Dados](28-modelagem-dados-exercicios.md)

---

[<- Anterior: Boas Praticas](27-boas-praticas.md) | [Glossario](00-glossario.md) | [Proximo: CRUD em Memoria ->](29-crud-memoria.md)
