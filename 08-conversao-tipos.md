# 08 — Conversao entre Tipos de Dados (Type Casting)

[<- Anterior: Variaveis e Tipos Basicos](07-variaveis-tipos.md) | [Glossario](00-glossario.md) | [Proximo: Manipulacao de Strings ->](09-manipulacao-strings.md)

---

## Introducao

No modulo anterior, voce aprendeu que o Python tem quatro tipos basicos de dados: `int`, `float`, `str` e `bool`. Agora vamos entender um problema muito comum que todo programador iniciante enfrenta: **e se voce tem um valor de um tipo, mas precisa dele em outro tipo?**

Imagine que voce recebeu uma encomenda pelo correio. Dentro da caixa veio um numero de telefone escrito em um papel. O numero esta ali, mas esta em formato de texto — voce nao consegue ligar para ele diretamente a partir do papel. Voce precisa "converter" aquele texto em um numero que o telefone entenda.

Em programacao, isso se chama **conversao de tipos** (ou **type casting**, em ingles). E o processo de transformar um valor de um tipo para outro.

> **Dica:** Consulte o [Glossario](00-glossario.md) sempre que encontrar um termo desconhecido.

---

## Como Executar os Exemplos Deste Modulo

1. Copie o codigo de exemplo
2. Cole em um novo arquivo no VSCode
3. Salve com extensao `.py` (exemplo: `conversao.py`)
4. Abra o terminal (`Ctrl + Alt + T`)
5. Navegue ate a pasta: `cd ~/meus-projetos/python-curso/modulo-08`
6. Execute: `python3 conversao.py`

---

## Por que Precisamos Converter Tipos?

O motivo mais comum e o `input()`. Como vimos no modulo 06, a funcao `input()` **sempre retorna uma string** (texto), mesmo quando o usuario digita um numero. Se voce tentar fazer calculos com esse texto, o Python vai se confundir:

```python
# O usuario digita "10", mas input() retorna o TEXTO "10"
# "number" = numero
number = input("Digite um numero: ")

# Tentamos somar 5 ao numero
# Isso NAO vai funcionar como esperado!
result = number + 5
```

Se voce executar esse codigo e digitar `10`, o Python vai mostrar um erro:

```
TypeError: can only concatenate str (not "int") to str
```

Esse erro esta dizendo: "Erro de Tipo: so consigo juntar texto com texto, nao texto com numero". O Python nao sabe se voce quer somar matematicamente (10 + 5 = 15) ou juntar textos ("10" + "5" = "105"). Por isso, voce precisa **converter** o texto para numero antes de fazer calculos.

---

## As Funcoes de Conversao

O Python oferece funcoes para converter valores entre tipos. Cada funcao tem o nome do tipo para o qual voce quer converter:

### int() — Converter para numero inteiro

A funcao `int()` transforma um valor em numero inteiro (sem casas decimais):

```python
# Convertendo texto para numero inteiro
# "text_number" = numero em formato de texto
text_number = "42"

# int() transforma o texto "42" no numero 42
# "real_number" = numero real (de verdade, nao o tipo)
real_number = int(text_number)

print("Texto:", text_number, "- Tipo:", type(text_number))
print("Numero:", real_number, "- Tipo:", type(real_number))
```

**Saida esperada:**
```
Texto: 42 - Tipo: <class 'str'>
Numero: 42 - Tipo: <class 'int'>
```

`int()` tambem converte float para int, **cortando as casas decimais** (nao arredonda, apenas remove):

```python
# Convertendo float para int — as casas decimais sao CORTADAS
# "price" = preco
price = 19.99

# int() remove as casas decimais (nao arredonda!)
# "price_rounded" = preco arredondado (na verdade, truncado)
price_truncated = int(price)

print("Float:", price)
print("Int:", price_truncated)
```

**Saida esperada:**
```
Float: 19.99
Int: 19
```

> **Atencao:** `int(19.99)` resulta em `19`, nao em `20`. A funcao `int()` simplesmente corta as casas decimais — ela nao arredonda. Se voce precisa arredondar, use a funcao `round()`.

### float() — Converter para numero decimal

A funcao `float()` transforma um valor em numero decimal:

```python
# Convertendo texto para numero decimal
# "text_price" = preco em formato de texto
text_price = "9.99"

# float() transforma o texto "9.99" no numero 9.99
# "real_price" = preco como numero
real_price = float(text_price)

print("Texto:", text_price, "- Tipo:", type(text_price))
print("Numero:", real_price, "- Tipo:", type(real_price))
```

**Saida esperada:**
```
Texto: 9.99 - Tipo: <class 'str'>
Numero: 9.99 - Tipo: <class 'float'>
```

`float()` tambem converte int para float, adicionando `.0`:

```python
# Convertendo int para float
# "quantity" = quantidade
quantity = 10

# float() adiciona .0 ao numero inteiro
# "quantity_float" = quantidade como decimal
quantity_float = float(quantity)

print("Int:", quantity)
print("Float:", quantity_float)
```

**Saida esperada:**
```
Int: 10
Float: 10.0
```

### str() — Converter para texto

A funcao `str()` transforma qualquer valor em texto (string):

```python
# Convertendo numero para texto
# "age" = idade
age = 25

# str() transforma o numero 25 no texto "25"
# "age_text" = idade como texto
age_text = str(age)

print("Numero:", age, "- Tipo:", type(age))
print("Texto:", age_text, "- Tipo:", type(age_text))
```

**Saida esperada:**
```
Numero: 25 - Tipo: <class 'int'>
Texto: 25 - Tipo: <class 'str'>
```

> **Nota:** `str()` e util quando voce precisa juntar um numero com um texto usando o operador `+`. Mas na maioria dos casos, usar `print()` com virgulas ou f-strings (modulo 09) e mais simples.

### bool() — Converter para booleano

A funcao `bool()` transforma um valor em `True` ou `False`. A regra geral e:

- Valores "vazios" ou "zero" viram `False`
- Qualquer outro valor vira `True`

```python
# Valores que viram False
print("bool(0):", bool(0))           # zero inteiro
print("bool(0.0):", bool(0.0))       # zero decimal
print('bool(""):', bool(""))         # texto vazio
print("bool(None):", bool(None))     # valor nulo

print()  # linha em branco para separar

# Valores que viram True
print("bool(1):", bool(1))           # qualquer numero diferente de zero
print("bool(-5):", bool(-5))         # numeros negativos tambem
print("bool(3.14):", bool(3.14))     # qualquer decimal diferente de zero
print('bool("ola"):', bool("ola"))   # qualquer texto nao vazio
```

**Saida esperada:**
```
bool(0): False
bool(0.0): False
bool(""): False
bool(None): False

bool(1): True
bool(-5): True
bool(3.14): True
bool("ola"): True
```

---

## Conversoes que Funcionam e Conversoes que Falham

Nem toda conversao e possivel. Quando voce tenta converter algo que nao faz sentido, o Python mostra um erro.

### Conversoes que funcionam

| De | Para | Exemplo | Resultado |
|----|------|---------|-----------|
| str (numerico) | int | `int("42")` | `42` |
| str (numerico) | float | `float("3.14")` | `3.14` |
| int | float | `float(10)` | `10.0` |
| float | int | `int(9.99)` | `9` (corta decimais) |
| int | str | `str(42)` | `"42"` |
| float | str | `str(3.14)` | `"3.14"` |
| qualquer valor | bool | `bool(valor)` | `True` ou `False` |

### Conversoes que falham (geram erro)

```python
# Tentar converter texto nao numerico para int
# Isso gera um ERRO!
# "text" = texto
text = "abc"
number = int(text)  # ValueError!
```

**Mensagem de erro:**
```
ValueError: invalid literal for int() with base 10: 'abc'
```

Traduzindo: "Erro de Valor: 'abc' nao e um valor valido para converter em numero inteiro".

```python
# Tentar converter texto com ponto para int (precisa ser float primeiro)
# "text_decimal" = texto decimal
text_decimal = "3.14"
number = int(text_decimal)  # ValueError!
```

**Mensagem de erro:**
```
ValueError: invalid literal for int() with base 10: '3.14'
```

> **Dica:** Para converter "3.14" para inteiro, faca em dois passos: primeiro converta para float, depois para int: `int(float("3.14"))` resulta em `3`.

---

## Uso Pratico: Combinando input() com Conversao

O caso mais comum de conversao e quando voce le dados do usuario com `input()` e precisa fazer calculos:

```python
# Programa que calcula o dobro de um numero
# "number" = numero
# int() converte o texto digitado pelo usuario em numero inteiro
number = int(input("Digite um numero inteiro: "))

# "double" = dobro
# Multiplicamos o numero por 2 para obter o dobro
double = number * 2

print("O dobro de", number, "e", double)
```

**Saida esperada (se digitar 7):**
```
Digite um numero inteiro: 7
O dobro de 7 e 14
```

```python
# Programa que calcula o preco total com desconto
# "original_price" = preco original
original_price = float(input("Preco original: R$ "))

# "discount_percent" = porcentagem de desconto
# Porcentagem e uma forma de representar uma parte de 100
# 20% significa 20 de cada 100
discount_percent = float(input("Desconto (%): "))

# Calculamos o valor do desconto
# Para calcular a porcentagem, dividimos por 100 e multiplicamos pelo preco
# Exemplo: 20% de 100 = (20 / 100) * 100 = 0.20 * 100 = 20
# "discount_value" = valor do desconto
discount_value = original_price * (discount_percent / 100)

# "final_price" = preco final (original menos o desconto)
final_price = original_price - discount_value

print("Preco original: R$", original_price)
print("Desconto:", discount_percent, "%")
print("Valor do desconto: R$", discount_value)
print("Preco final: R$", final_price)
```

**Saida esperada (se digitar 100 e 20):**
```
Preco original: R$ 100
Desconto: 20 %
Valor do desconto: R$ 20.0
Preco final: R$ 80.0
```

---

## Resumo das Funcoes de Conversao

| Funcao | Converte para | Exemplo | Resultado |
|--------|--------------|---------|-----------|
| `int()` | Numero inteiro | `int("42")` | `42` |
| `float()` | Numero decimal | `float("3.14")` | `3.14` |
| `str()` | Texto | `str(42)` | `"42"` |
| `bool()` | Verdadeiro/Falso | `bool(0)` | `False` |

---

## Para Saber Mais

- [W3Schools — Python Casting](https://www.w3schools.com/python/python_casting.asp) — _Conversao de tipos em Python_
- [W3Schools — Python Data Types](https://www.w3schools.com/python/python_datatypes.asp) — _Tipos de dados_
- [Documentacao Python — Funcoes Built-in](https://docs.python.org/pt-br/3/library/functions.html) — _Referencia completa das funcoes_

---

## Perguntas Frequentes (FAQ)

**P: Por que o input() nao retorna numero automaticamente?**
R: Porque o Python nao tem como adivinhar o que o usuario vai digitar. Pode ser um nome, um numero, um endereco — tudo chega como texto. Cabe a voce, programador, decidir o que fazer com esse texto e converter quando necessario.

**P: Qual a diferenca entre int() e float()?**
R: `int()` converte para numero inteiro (sem casas decimais): `int("42")` resulta em `42`. `float()` converte para numero decimal (com casas decimais): `float("42")` resulta em `42.0`. Use `int()` para quantidades e contagens, `float()` para precos, medidas e valores com decimais.

**P: O que acontece se eu tentar converter "abc" para int()?**
R: O Python mostra um `ValueError` porque "abc" nao e um numero. Isso e normal — o Python esta dizendo que nao consegue transformar letras em numeros. No modulo 18, vamos aprender a tratar esses erros para que o programa nao pare.

**P: int() arredonda o numero?**
R: Nao! `int()` apenas corta as casas decimais. `int(9.99)` resulta em `9`, nao em `10`. Se voce precisa arredondar, use `round()`: `round(9.99)` resulta em `10`.

**P: Posso converter "3.14" diretamente para int?**
R: Nao diretamente. `int("3.14")` gera erro porque o texto contem um ponto. Faca em dois passos: primeiro converta para float, depois para int: `int(float("3.14"))` resulta em `3`.

**P: O que e ValueError?**
R: E um tipo de erro que o Python mostra quando voce passa um valor invalido para uma funcao. Por exemplo, `int("abc")` gera ValueError porque "abc" nao pode ser convertido em numero. O nome vem de "Value Error" (erro de valor).

**P: O que e TypeError?**
R: E um tipo de erro que aparece quando voce tenta fazer uma operacao com tipos incompativeis. Por exemplo, `"10" + 5` gera TypeError porque voce esta tentando somar texto com numero. O nome vem de "Type Error" (erro de tipo).

**P: Quando devo usar int() e quando devo usar float()?**
R: Use `int()` quando o valor nao tem casas decimais: idade, quantidade, ano. Use `float()` quando o valor pode ter casas decimais: preco, peso, altura, temperatura.

**P: bool() e util na pratica?**
R: Sim, mas voce raramente vai usar `bool()` diretamente. O Python faz conversoes para booleano automaticamente em condicoes (if/while). Saber como funciona ajuda a entender por que `if 0:` nunca executa (porque `bool(0)` e `False`).

**P: O que significa "truncar"?**
R: Truncar e cortar algo sem arredondar. Quando `int()` converte `9.99` para `9`, ele esta truncando — cortando as casas decimais sem considerar se o numero esta mais perto de 9 ou de 10.

**P: Posso converter True e False para numero?**
R: Sim! `int(True)` resulta em `1` e `int(False)` resulta em `0`. Isso porque, internamente, o Python trata `True` como 1 e `False` como 0.

**P: O que e round()?**
R: E uma funcao que arredonda um numero decimal. `round(3.7)` resulta em `4`, `round(3.2)` resulta em `3`. Voce tambem pode especificar quantas casas decimais: `round(3.14159, 2)` resulta em `3.14`.

**P: Posso converter uma lista para int?**
R: Nao. `int()` so aceita strings numericas, floats e booleanos. Tentar converter outros tipos gera erro. Cada funcao de conversao tem suas regras sobre o que aceita.

**P: O que acontece se o usuario digitar um espaco antes do numero?**
R: `int(" 42 ")` funciona! O Python automaticamente ignora espacos no inicio e no fim ao converter. Mas `int("4 2")` (espaco no meio) gera erro.

**P: Posso fazer varias conversoes na mesma linha?**
R: Sim! `int(float("3.14"))` faz duas conversoes: primeiro converte o texto para float (3.14), depois converte o float para int (3). Isso e chamado de "conversao encadeada".

**P: O que e "casting" em programacao?**
R: Casting (ou type casting) e o nome tecnico para conversao de tipos. Quando voce escreve `int("42")`, esta fazendo um "cast" de string para int. O termo vem do ingles e significa "moldar" — voce esta moldando o valor para um novo formato.

**P: str() e util? Quando eu usaria?**
R: `str()` e util quando voce precisa juntar um numero com texto usando o operador `+`. Por exemplo: `"Idade: " + str(25)` resulta em `"Idade: 25"`. Mas na pratica, usar `print()` com virgulas ou f-strings (proximo modulo) e mais simples.

**P: O que acontece se eu converter um texto vazio para int?**
R: `int("")` gera `ValueError`. Um texto vazio nao e um numero, entao o Python nao consegue converter. Isso pode acontecer se o usuario apertar Enter sem digitar nada.

**P: Existe conversao automatica no Python?**
R: Sim, em alguns casos. Quando voce soma um int com um float (`10 + 3.14`), o Python automaticamente converte o int para float e o resultado e float (`13.14`). Isso se chama "conversao implicita".

**P: E normal errar nas conversoes no inicio?**
R: Muito normal! Conversao de tipos e um dos pontos que mais confunde iniciantes. Com pratica, voce vai identificar rapidamente quando precisa converter e qual funcao usar. Nao desanime se errar — cada erro e uma oportunidade de aprender.

---

## Exercicios de Fixacao

Os exercicios deste modulo estao em um arquivo separado para facilitar a consulta:

**[Acessar Exercicios do Modulo 08](08-conversao-tipos-exercicios.md)**

---

[<- Anterior: Variaveis e Tipos Basicos](07-variaveis-tipos.md) | [Glossario](00-glossario.md) | [Proximo: Manipulacao de Strings ->](09-manipulacao-strings.md)
