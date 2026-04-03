# 07 — Variaveis e Tipos Basicos

[<- Anterior: Entrada e Saida de Dados](06-entrada-saida.md) | [Glossario](00-glossario.md) | [Proximo: Conversao de Tipos ->](08-conversao-tipos.md)

---

## Introducao

No modulo anterior, voce aprendeu a usar `input()` e `print()` para conversar com o usuario. Agora vamos dar um passo adiante e entender como o Python **guarda informacoes na memoria** do computador.

Imagine que voce esta organizando uma mudanca. Voce tem varias caixas, e em cada caixa coloca um tipo de objeto diferente: roupas em uma, livros em outra, utensilios de cozinha em outra. Cada caixa tem uma **etiqueta** com o nome do que esta dentro. Em programacao, essas caixas sao as **variaveis** — e as etiquetas sao os **nomes** que damos a elas.

> **Dica:** Termos novos? Consulte o [Glossario](00-glossario.md) a qualquer momento.

---

## Como Executar os Exemplos Deste Modulo

1. Copie o codigo de exemplo
2. Cole em um novo arquivo no VSCode
3. Salve com extensao `.py` (exemplo: `variaveis.py`)
4. Abra o terminal (`Ctrl + Alt + T`)
5. Navegue ate a pasta: `cd ~/meus-projetos/python-curso/modulo-07`
6. Execute: `python3 variaveis.py`

---

## O que e uma Variavel?

Uma [variavel](00-glossario-q-z.md#variavel) e um espaco na memoria do computador que guarda um valor e tem um nome. Voce cria uma variavel, da um nome a ela e coloca um valor dentro. Depois, pode usar esse nome para acessar o valor guardado.

Pense em uma variavel como uma **caixa etiquetada**:

- A **etiqueta** e o nome da variavel (por exemplo: `age`)
- O **conteudo** da caixa e o valor guardado (por exemplo: `25`)
- Voce pode **trocar o conteudo** a qualquer momento (a caixa continua a mesma, mas o que esta dentro muda)

### Criando uma variavel

Em Python, voce cria uma variavel simplesmente atribuindo um valor a um nome usando o sinal de igual (`=`):

```python
# Criando uma variavel chamada "name" (nome)
# O sinal = significa "recebe" ou "guarda o valor"
# "name" = nome — a variavel guarda o texto "Maria"
name = "Maria"

# Criando uma variavel chamada "age" (idade)
# "age" = idade — a variavel guarda o numero 30
age = 30

# Exibindo os valores guardados nas variaveis
print("Nome:", name)
print("Idade:", age)
```

**Saida esperada:**
```
Nome: Maria
Idade: 30
```

> **Nota:** O sinal `=` em programacao nao significa "igual a" como na matematica. Ele significa **"recebe"** ou **"guarda o valor"**. Quando escrevemos `age = 30`, estamos dizendo: "a variavel age recebe o valor 30".

### Trocando o valor de uma variavel

Voce pode mudar o valor de uma variavel a qualquer momento. O valor antigo e substituido pelo novo:

```python
# Criando a variavel "price" (preco) com valor inicial
# "price" = preco
price = 10.50
print("Preco original:", price)

# Trocando o valor da variavel
# Agora price guarda 8.99 em vez de 10.50
price = 8.99
print("Preco com desconto:", price)
```

**Saida esperada:**
```
Preco original: 10.5
Preco com desconto: 8.99
```

> **Nota:** Quando voce atribui um novo valor a uma variavel, o valor anterior e perdido. A caixa so guarda um valor por vez.

---

## Os Quatro Tipos Basicos de Dados

Em Python, cada valor tem um **tipo** que define que tipo de informacao ele representa. Os quatro tipos basicos sao:

### 1. int — Numeros Inteiros

O tipo `int` (abreviacao de "integer", que significa "inteiro" em ingles) representa numeros sem casas decimais. Podem ser positivos, negativos ou zero.

```python
# Exemplos de numeros inteiros (int)
# "quantity" = quantidade, "temperature" = temperatura, "year" = ano
quantity = 10
temperature = -5
year = 2025
zero = 0

print("Quantidade:", quantity)
print("Temperatura:", temperature)
print("Ano:", year)
print("Zero:", zero)
```

**Saida esperada:**
```
Quantidade: 10
Temperatura: -5
Ano: 2025
Zero: 0
```

Numeros inteiros sao usados para contar coisas: quantidade de produtos, idade, ano, numero de alunos em uma sala.

### 2. float — Numeros Decimais

O tipo `float` (abreviacao de "floating point", que significa "ponto flutuante" em ingles) representa numeros com casas decimais. Em Python, usamos **ponto** (nao virgula) para separar a parte inteira da decimal.

```python
# Exemplos de numeros decimais (float)
# "price" = preco, "height" = altura, "weight" = peso
price = 19.99
height = 1.75
weight = 68.5

print("Preco:", price)
print("Altura:", height, "metros")
print("Peso:", weight, "kg")
```

**Saida esperada:**
```
Preco: 19.99
Altura: 1.75 metros
Peso: 68.5 kg
```

> **Atencao:** Em Python, o separador decimal e o **ponto** (`.`), nao a virgula. Escrevemos `19.99` e nao `19,99`. Isso e diferente do que usamos no dia a dia no Brasil, mas e o padrao em programacao.

### 3. str — Textos (Strings)

O tipo `str` (abreviacao de "string", que significa "cadeia de caracteres" em ingles) representa textos. Strings sao criadas colocando o texto entre aspas simples ou duplas.

```python
# Exemplos de textos (str / string)
# "greeting" = saudacao, "city" = cidade, "document" = documento
greeting = "Bom dia!"
city = 'Sao Paulo'
document = "123.456.789-00"

print("Saudacao:", greeting)
print("Cidade:", city)
print("Documento:", document)
```

**Saida esperada:**
```
Saudacao: Bom dia!
Cidade: Sao Paulo
Documento: 123.456.789-00
```

> **Nota:** Mesmo que uma string contenha numeros (como "123.456.789-00"), ela continua sendo texto. O Python nao faz calculos com strings — ele as trata como sequencias de caracteres.

### 4. bool — Verdadeiro ou Falso

O tipo `bool` (abreviacao de "boolean", que significa "booleano" em ingles — em homenagem ao matematico George Boole) representa apenas dois valores possiveis: `True` (verdadeiro) ou `False` (falso).

```python
# Exemplos de booleanos (bool)
# "is_active" = esta ativo, "has_discount" = tem desconto
# "is_student" = e estudante
is_active = True
has_discount = False
is_student = True

print("Ativo:", is_active)
print("Tem desconto:", has_discount)
print("E estudante:", is_student)
```

**Saida esperada:**
```
Ativo: True
Tem desconto: False
E estudante: True
```

> **Atencao:** `True` e `False` comecam com letra **maiuscula**. Escrever `true` ou `false` (com minuscula) causa erro no Python.

Booleanos sao como interruptores de luz: ou esta ligado (`True`) ou desligado (`False`). Sao muito usados em condicoes e decisoes, que vamos aprender no modulo 12.

---

## Verificando o Tipo de uma Variavel com type()

A funcao `type()` mostra qual e o tipo de um valor ou variavel. E muito util para verificar se uma variavel contem o tipo de dado que voce espera:

```python
# Verificando o tipo de cada variavel
# type() retorna o tipo do valor
name = "Carlos"
age = 28
height = 1.80
is_enrolled = True

# Exibindo o valor e o tipo de cada variavel
print("name:", name, "- Tipo:", type(name))
print("age:", age, "- Tipo:", type(age))
print("height:", height, "- Tipo:", type(height))
print("is_enrolled:", is_enrolled, "- Tipo:", type(is_enrolled))
```

**Saida esperada:**
```
name: Carlos - Tipo: <class 'str'>
age: 28 - Tipo: <class 'int'>
height: 1.8 - Tipo: <class 'float'>
is_enrolled: True - Tipo: <class 'bool'>
```

O que cada resultado significa:

| Resultado | Tipo | Significado |
|-----------|------|-------------|
| `<class 'str'>` | str | Texto (string) |
| `<class 'int'>` | int | Numero inteiro |
| `<class 'float'>` | float | Numero decimal |
| `<class 'bool'>` | bool | Verdadeiro ou falso |

---

## Regras e Convencoes para Nomes de Variaveis

Nem todo nome e valido para uma variavel em Python. Existem regras obrigatorias e convencoes recomendadas.

### Regras obrigatorias (se nao seguir, da erro)

| Regra | Exemplo valido | Exemplo invalido | Por que |
|-------|---------------|-----------------|---------|
| Deve comecar com letra ou `_` | `name`, `_total` | `1name` | Nao pode comecar com numero |
| Nao pode conter espacos | `first_name` | `first name` | Espacos nao sao permitidos |
| Nao pode usar palavras reservadas | `my_class` | `class` | `class` e uma palavra reservada do Python |
| Diferencia maiusculas de minusculas | `Name` e `name` sao diferentes | — | Python e case-sensitive |

### Convencoes recomendadas (boas praticas)

| Convencao | Exemplo | Quando usar |
|-----------|---------|-------------|
| snake_case | `product_name`, `total_price` | Variaveis e funcoes |
| CamelCase | `ProductManager`, `ShoppingCart` | Classes (vamos ver no modulo 22) |
| MAIUSCULAS | `MAX_ATTEMPTS`, `TAX_RATE` | Constantes (valores que nao mudam) |

> **Nota:** [snake_case](00-glossario-q-z.md#snake_case) significa escrever tudo em minusculas e separar palavras com underscore (`_`). E o padrao do Python para variaveis e funcoes.

```python
# Bons nomes de variaveis (snake_case, descritivos)
# "product_name" = nome do produto
product_name = "Arroz"

# "unit_price" = preco unitario
unit_price = 5.99

# "stock_quantity" = quantidade em estoque
stock_quantity = 150

# Nomes ruins (evite estes)
# x = "Arroz"        # O que e "x"? Nao diz nada
# p = 5.99           # O que e "p"? Impossivel saber
# n = 150            # O que e "n"? Confuso

print("Produto:", product_name)
print("Preco:", unit_price)
print("Estoque:", stock_quantity)
```

**Saida esperada:**
```
Produto: Arroz
Preco: 5.99
Estoque: 150
```

Dar nomes claros e descritivos as variaveis e uma das praticas mais importantes em programacao. Um bom nome de variavel funciona como uma etiqueta bem escrita: qualquer pessoa que leia o codigo entende o que aquela variavel guarda.

---

## Resumo dos Tipos Basicos

| Tipo | Nome em ingles | O que guarda | Exemplos |
|------|---------------|-------------|----------|
| `int` | integer (inteiro) | Numeros sem decimais | `10`, `-3`, `0`, `2025` |
| `float` | floating point (ponto flutuante) | Numeros com decimais | `3.14`, `19.99`, `-0.5` |
| `str` | string (cadeia de caracteres) | Textos | `"Ola"`, `'Python'`, `"123"` |
| `bool` | boolean (booleano) | Verdadeiro ou falso | `True`, `False` |

---

## Para Saber Mais

- [W3Schools — Python Variables](https://www.w3schools.com/python/python_variables.asp) — _Como criar e usar variaveis_
- [W3Schools — Python Data Types](https://www.w3schools.com/python/python_datatypes.asp) — _Todos os tipos de dados do Python_
- [W3Schools — Python Numbers](https://www.w3schools.com/python/python_numbers.asp) — _Tipos numericos em detalhes_
- [W3Schools — Python Strings](https://www.w3schools.com/python/python_strings.asp) — _Trabalhando com textos_
- [W3Schools — Python Booleans](https://www.w3schools.com/python/python_booleans.asp) — _Valores verdadeiro e falso_
- [Documentacao Oficial Python — Tipos Built-in](https://docs.python.org/pt-br/3/library/stdtypes.html) — _Referencia completa_

---

## Perguntas Frequentes (FAQ)

**P: O que acontece se eu usar uma variavel que nao existe?**
R: O Python mostra um erro chamado `NameError`. Por exemplo, se voce escrever `print(nome)` sem ter criado a variavel `nome` antes, vai aparecer: `NameError: name 'nome' is not defined`. Isso significa que o Python nao encontrou nenhuma variavel com esse nome.

**P: Posso usar acentos nos nomes de variaveis?**
R: Tecnicamente sim, o Python 3 aceita. Mas nao e recomendado. Siga a convencao de usar nomes em ingles sem acentos, como `product_name` em vez de `nome_produto`. Isso segue o padrao profissional.

**P: Qual a diferenca entre `=` e `==`?**
R: `=` e o operador de **atribuicao** — ele guarda um valor em uma variavel (`age = 25`). `==` e o operador de **comparacao** — ele verifica se dois valores sao iguais (`age == 25` retorna `True` ou `False`). Vamos aprender sobre `==` no modulo 11.

**P: Posso guardar qualquer coisa em uma variavel?**
R: Sim! Variaveis em Python podem guardar qualquer tipo de dado: numeros, textos, booleanos, listas, dicionarios e muito mais. O Python e flexivel nesse sentido.

**P: O que e "case-sensitive"?**
R: Significa que o Python diferencia letras maiusculas de minusculas. `Name`, `name` e `NAME` sao tres variaveis diferentes. Tenha cuidado com isso ao escrever seus programas.

**P: Por que usar nomes em ingles para variaveis?**
R: E a convencao profissional no mundo todo. Quando voce trabalhar em equipe ou ler codigo de outras pessoas, os nomes estarao em ingles. Neste curso, todos os nomes de variaveis sao em ingles com traducao nos comentarios para voce se acostumar.

**P: O que sao "palavras reservadas"?**
R: Sao palavras que o Python ja usa para funcoes especificas e que voce nao pode usar como nomes de variaveis. Exemplos: `if`, `for`, `while`, `class`, `def`, `return`, `True`, `False`, `None`. Se tentar usar, o Python mostra um erro de sintaxe.

**P: Posso criar uma variavel sem dar valor a ela?**
R: Nao diretamente. Em Python, uma variavel so existe quando voce atribui um valor a ela. Mas voce pode usar `None` como valor inicial: `result = None` significa "a variavel result existe, mas ainda nao tem um valor definido".

**P: O que e `None`?**
R: `None` e um valor especial do Python que significa "nada" ou "vazio". E diferente de zero (`0`) ou de texto vazio (`""`). `None` significa que a variavel existe mas nao tem valor atribuido.

**P: Por que `"123"` e string e nao int?**
R: Porque esta entre aspas. Tudo que esta entre aspas e tratado como texto (string) pelo Python, mesmo que pareca um numero. Para o Python, `"123"` e uma sequencia de caracteres, nao um numero. Se quiser usar como numero, precisa converter com `int("123")`.

**P: Posso usar uma variavel antes de cria-la?**
R: Nao. O Python le o codigo de cima para baixo. Se voce tentar usar uma variavel antes de atribuir um valor a ela, vai receber um `NameError`. Sempre crie a variavel antes de usa-la.

**P: O que acontece se eu escrever `True` com t minusculo?**
R: O Python nao vai reconhecer `true` como booleano — vai pensar que e o nome de uma variavel. Como essa variavel provavelmente nao existe, vai dar `NameError`. Sempre use `True` e `False` com a primeira letra maiuscula.

**P: Posso mudar o tipo de uma variavel?**
R: Sim! Em Python, voce pode atribuir um valor de tipo diferente a uma variavel que ja existe. Por exemplo: `x = 10` (int) e depois `x = "dez"` (str). Isso funciona, mas pode causar confusao. Evite mudar o tipo de uma variavel no meio do programa.

**P: O que e "ponto flutuante"?**
R: E o nome tecnico para numeros decimais em computacao. O "ponto" se refere ao ponto decimal (`.`), e "flutuante" porque o ponto pode "flutuar" para diferentes posicoes (1.5, 15.0, 0.15). Na pratica, `float` e simplesmente um numero com casas decimais.

**P: Por que o Python mostra `10.0` em vez de `10` quando uso float?**
R: Porque `float` sempre mostra o ponto decimal para indicar que e um numero decimal, mesmo quando nao tem casas decimais significativas. `10.0` e `10` tem o mesmo valor, mas sao de tipos diferentes (`float` e `int`).

**P: Posso usar underscore no meio de numeros?**
R: Sim! O Python permite usar `_` para separar grupos de digitos e facilitar a leitura: `1_000_000` e o mesmo que `1000000`. E como usar ponto para separar milhares no dia a dia.

**P: O que e uma constante?**
R: E uma variavel cujo valor nao deveria mudar durante o programa. Em Python, nao existe uma forma de impedir a mudanca, mas a convencao e usar nomes em MAIUSCULAS: `TAX_RATE = 0.10`. Isso sinaliza para outros programadores que aquele valor nao deve ser alterado.

**P: Quantas variaveis posso criar?**
R: Nao ha limite pratico. Voce pode criar quantas variaveis precisar. O importante e dar nomes claros e descritivos para nao se perder.

**P: Posso criar varias variaveis na mesma linha?**
R: Sim! Python permite atribuicao multipla: `name, age, city = "Ana", 25, "SP"`. Mas para iniciantes, e mais claro criar uma variavel por linha para facilitar a leitura.

**P: E normal confundir os tipos no inicio?**
R: Completamente normal. Com o tempo, voce vai identificar os tipos naturalmente. Use `type()` sempre que tiver duvida — e para isso que ela existe. Nao tenha vergonha de verificar.

---

## Exercicios de Fixacao

Os exercicios deste modulo estao em um arquivo separado para facilitar a consulta:

**[Acessar Exercicios do Modulo 07](07-variaveis-tipos-exercicios.md)**

---

[<- Anterior: Entrada e Saida de Dados](06-entrada-saida.md) | [Glossario](00-glossario.md) | [Proximo: Conversao de Tipos ->](08-conversao-tipos.md)
