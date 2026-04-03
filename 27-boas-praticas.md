# 27 — Boas Praticas de Programacao em Python

[<- Anterior: pip e Dependencias](26-pip-dependencias.md) | [Glossario](00-glossario.md) | [Proximo: Modelagem de Dados ->](28-modelagem-dados.md)

---

## Introducao

No modulo anterior, voce aprendeu a instalar e gerenciar bibliotecas externas com pip e ambientes virtuais. Agora vamos aprender algo que separa um codigo amador de um codigo profissional: as **boas praticas de programacao**.

Imagine que voce esta escrevendo uma carta para alguem. Voce pode escrever tudo em uma unica linha, sem paragrafos, sem pontuacao, com letras misturadas entre maiusculas e minusculas. A pessoa ate consegue ler, mas vai ser dificil e cansativo. Agora imagine a mesma carta escrita com paragrafos organizados, pontuacao correta e letra legivel — muito mais facil de entender, certo?

Em programacao, funciona da mesma forma. O computador nao se importa se o seu codigo esta bonito ou feio — ele executa do mesmo jeito. Mas **voce** e **outras pessoas** que lerem o codigo se importam muito. Um codigo bem escrito e mais facil de entender, de corrigir quando tem erros e de melhorar no futuro.

O Python tem um guia oficial de boas praticas chamado **PEP 8** (Python Enhancement Proposal 8 — Proposta de Melhoria do Python numero 8). Esse guia define convencoes que a comunidade Python inteira segue para escrever codigo de forma consistente e legivel.

Neste modulo, voce vai aprender:

- O que e a PEP 8 e por que ela e importante
- Regras de espacamento e comprimento de linhas
- Como organizar imports corretamente
- Convencoes de nomenclatura: snake_case, CamelCase e UPPER_CASE
- A diferenca entre comentarios uteis e desnecessarios
- O que sao docstrings e como usa-las
- Exemplos comparativos de codigo com e sem boas praticas

> **Dica:** Consulte o [Glossario](00-glossario.md) sempre que encontrar um termo desconhecido.

---

## O Que e a PEP 8?

A **PEP 8** e o guia de estilo oficial do Python. PEP significa "Python Enhancement Proposal" (Proposta de Melhoria do Python). O numero 8 e simplesmente o numero dessa proposta especifica.

**Analogia:** Pense na PEP 8 como as regras de formatacao de um trabalho escolar. O professor pede que voce use fonte Arial tamanho 12, espacamento duplo e margens de 3 centimetros. Essas regras nao mudam o conteudo do trabalho, mas garantem que todos os trabalhos tenham a mesma aparencia e sejam faceis de ler. A PEP 8 faz o mesmo para o codigo Python — define regras de formatacao que toda a comunidade segue.

A PEP 8 foi escrita por Guido van Rossum (o criador do Python) junto com outros desenvolvedores. Ela nao e uma lei obrigatoria — o Python nao vai dar erro se voce nao seguir. Mas seguir a PEP 8 traz beneficios enormes:

1. **Legibilidade:** Seu codigo fica mais facil de ler e entender
2. **Consistencia:** Todo codigo Python no mundo segue o mesmo estilo
3. **Colaboracao:** Outros desenvolvedores entendem seu codigo rapidamente
4. **Profissionalismo:** Empresas esperam que desenvolvedores sigam a PEP 8

> **Importante:** Voce nao precisa decorar todas as regras da PEP 8 de uma vez. Neste modulo, vamos aprender as regras mais importantes. Com o tempo e a pratica, elas se tornam naturais.

---

## Espacamento e Comprimento de Linhas

### Comprimento Maximo de Linhas: 79 Caracteres

A PEP 8 recomenda que cada linha de codigo tenha no maximo **79 caracteres**. Isso pode parecer pouco, mas tem boas razoes:

- Permite abrir dois arquivos lado a lado no editor
- Facilita a leitura sem precisar rolar horizontalmente
- Funciona bem em terminais com largura padrao

**Analogia:** Pense em um livro. As linhas de texto nao vao de uma ponta a outra da pagina — elas tem uma largura confortavel para os olhos. Se as linhas fossem muito longas, seus olhos se cansariam tentando acompanhar. O mesmo vale para codigo.

Veja um exemplo de linha muito longa e como quebra-la:

```python
# Exemplo RUIM: linha muito longa, dificil de ler
# "result" = resultado, "calculate" = calcular, "total" = total, "price" = preco, "quantity" = quantidade, "discount" = desconto
result = calculate_total_price_with_discount(product_name, product_price, product_quantity, discount_percentage, tax_rate)
```

```python
# Exemplo BOM: linha quebrada para ficar dentro de 79 caracteres
# "result" = resultado, "calculate" = calcular
# "total" = total, "price" = preco
result = calculate_total_price_with_discount(
    product_name,        # nome do produto
    product_price,       # preco do produto
    product_quantity,    # quantidade do produto
    discount_percentage, # percentual de desconto
    tax_rate             # taxa de imposto
)
```

Saida esperada:
```
(ambos os codigos produzem o mesmo resultado — a diferenca e apenas na legibilidade)
```

### Linhas em Branco para Separar Blocos

A PEP 8 define regras claras sobre linhas em branco:

- **Duas linhas em branco** antes e depois de definicoes de funcoes e classes no nivel do modulo
- **Uma linha em branco** entre metodos dentro de uma classe
- Linhas em branco dentro de funcoes para separar blocos logicos (use com moderacao)

```python
# Importacoes no topo do arquivo
# "import" = importar (trazer modulos externos)
import math


# Duas linhas em branco antes de uma funcao
# "calculate" = calcular, "area" = area, "circle" = circulo
def calculate_circle_area(radius):
    # "radius" = raio
    # "area" = area
    area = math.pi * radius ** 2
    return area


# Duas linhas em branco antes da proxima funcao
# "calculate" = calcular, "perimeter" = perimetro
def calculate_circle_perimeter(radius):
    # "radius" = raio
    # "perimeter" = perimetro
    perimeter = 2 * math.pi * radius
    return perimeter


# Duas linhas em branco antes de uma classe
# "Shape" = Forma (geometrica)
class Shape:
    # "name" = nome
    def __init__(self, name):
        self.name = name

    # Uma linha em branco entre metodos da classe
    # "describe" = descrever
    def describe(self):
        print(f"Esta forma se chama: {self.name}")
```

Saida esperada:
```
(este codigo define funcoes e uma classe — nao produz saida por si so)
```

### Espacos ao Redor de Operadores

A PEP 8 recomenda colocar **um espaco** antes e depois de operadores de atribuicao e comparacao:

```python
# Exemplo BOM: espacos ao redor dos operadores
# "price" = preco, "quantity" = quantidade
price = 10.50
quantity = 3
total = price * quantity
is_expensive = total > 25
```

Saida esperada:
```
(este codigo atribui valores a variaveis — nao produz saida por si so)
```

```python
# Exemplo RUIM: sem espacos, dificil de ler
price=10.50
quantity=3
total=price*quantity
is_expensive=total>25
```

A excecao e em argumentos padrao de funcoes, onde **nao** se usa espaco:

```python
# Exemplo BOM: sem espaco no argumento padrao
# "greet" = cumprimentar, "name" = nome, "greeting" = saudacao
def greet(name, greeting="Ola"):
    print(f"{greeting}, {name}!")


# Chamando a funcao com o valor padrao
greet("Maria")
# Chamando a funcao com saudacao personalizada
greet("Joao", greeting="Bom dia")
```

Saida esperada:
```
Ola, Maria!
Bom dia, Joao!
```

### Espacos Apos Virgulas

Sempre coloque um espaco apos cada virgula em listas, tuplas, argumentos de funcoes e dicionarios:

```python
# Exemplo BOM: espaco apos cada virgula
# "fruits" = frutas
fruits = ["maca", "banana", "laranja", "uva"]

# "calculate" = calcular, "sum" = soma
def calculate_sum(a, b, c):
    return a + b + c


# Chamando a funcao com tres argumentos
# "result" = resultado
result = calculate_sum(10, 20, 30)
print(f"Resultado: {result}")
```

Saida esperada:
```
Resultado: 60
```

```python
# Exemplo RUIM: sem espaco apos virgulas
fruits = ["maca","banana","laranja","uva"]

def calculate_sum(a,b,c):
    return a+b+c
```

---

## Organizacao de Imports

A PEP 8 define uma ordem especifica para organizar as importacoes no topo do arquivo. Isso pode parecer um detalhe pequeno, mas faz uma grande diferenca na organizacao do codigo.

### Ordem dos Imports

Os imports devem ser organizados em **tres grupos**, separados por uma linha em branco:

1. **Biblioteca padrao** do Python (modulos que ja vem com o Python)
2. **Bibliotecas de terceiros** (pacotes instalados com pip)
3. **Modulos locais** (arquivos do seu proprio projeto)

```python
# Grupo 1: Biblioteca padrao do Python
# "import" = importar
import os          # "os" = sistema operacional (operating system)
import json        # "json" = formato de dados
import math        # "math" = matematica
from datetime import datetime  # "datetime" = data e hora

# Grupo 2: Bibliotecas de terceiros (instaladas com pip)
import requests    # "requests" = requisicoes HTTP

# Grupo 3: Modulos locais (arquivos do seu projeto)
from my_module import my_function  # "my_module" = meu modulo
```

Saida esperada:
```
(este codigo apenas importa modulos — nao produz saida por si so)
```

### Imports Absolutos vs Relativos

A PEP 8 recomenda usar **imports absolutos** sempre que possivel:

```python
# Exemplo BOM: import absoluto
# "my_project" = meu projeto, "utils" = utilitarios
# "helpers" = auxiliares, "format" = formatar, "date" = data
from my_project.utils import format_date

# Exemplo ACEITAVEL: import relativo (dentro de pacotes)
# O ponto (.) indica "neste mesmo pacote"
from .helpers import format_date
```

### Evite Imports com Asterisco

Nunca use `from modulo import *` — isso importa tudo do modulo e pode causar conflitos de nomes:

```python
# Exemplo RUIM: import com asterisco
# Importa TUDO do modulo math — voce nao sabe o que esta disponivel
from math import *

# Exemplo BOM: importe apenas o que precisa
# Fica claro quais funcoes voce esta usando
from math import sqrt, pi, ceil
```

### Comparativo: Imports Organizados vs Desorganizados

Veja a diferenca entre um arquivo com imports organizados e outro desorganizado:

```python
# Exemplo RUIM: imports desorganizados
# Tudo misturado, sem ordem, sem separacao
from my_module import my_function
import requests
import os
from datetime import datetime
import json
import math
from .helpers import format_date
```

```python
# Exemplo BOM: imports organizados seguindo a PEP 8
# Grupo 1: Biblioteca padrao (em ordem alfabetica)
import json
import math
import os
from datetime import datetime

# Grupo 2: Bibliotecas de terceiros
import requests

# Grupo 3: Modulos locais
from my_module import my_function
from .helpers import format_date
```

> **Dica:** Dentro de cada grupo, organize os imports em **ordem alfabetica**. Isso facilita encontrar um import especifico quando o arquivo tem muitas importacoes.

---

## Nomenclatura: Como Nomear Variaveis, Funcoes e Classes

A nomenclatura (como voce escolhe os nomes no codigo) e uma das partes mais importantes das boas praticas. Nomes bem escolhidos tornam o codigo autoexplicativo — ou seja, voce entende o que o codigo faz apenas lendo os nomes.

**Analogia:** Imagine que voce esta organizando uma estante de livros. Se voce colocar etiquetas claras nas prateleiras ("Romances", "Ciencia", "Culinaria"), qualquer pessoa encontra o que procura rapidamente. Mas se as etiquetas forem "Prateleira 1", "Prateleira 2", "Prateleira 3", ninguem sabe o que tem em cada uma sem abrir e olhar.

### snake_case para Variaveis e Funcoes

Em Python, variaveis e funcoes usam o padrao **snake_case**: todas as letras minusculas, com palavras separadas por underline (sublinhado `_`).

O nome "snake_case" vem do ingles: "snake" significa cobra, e o underline entre as palavras lembra uma cobra rastejando no chao.

```python
# Exemplos BOM: snake_case para variaveis
# "student" = estudante, "name" = nome
student_name = "Maria Silva"
# "total" = total, "price" = preco
total_price = 45.90
# "is" = e/esta, "active" = ativo
is_active = True
# "max" = maximo, "attempts" = tentativas
max_attempts = 3

# Exemplos BOM: snake_case para funcoes
# "calculate" = calcular, "average" = media
def calculate_average(grades):
    # "grades" = notas
    # "total" = total, "sum" = soma
    total = sum(grades)
    # "average" = media
    average = total / len(grades)
    return average


# "validate" = validar, "email" = email, "address" = endereco
def validate_email_address(email):
    # Verifica se o email contem o simbolo @
    return "@" in email


# Testando as funcoes
# "grades" = notas
grades = [8.5, 7.0, 9.0, 6.5]
print(f"Media: {calculate_average(grades)}")
print(f"Email valido: {validate_email_address('maria@email.com')}")
```

Saida esperada:
```
Media: 7.75
Email valido: True
```

```python
# Exemplos RUIM: nomes que NAO seguem snake_case
studentName = "Maria"       # camelCase — errado para Python
TotalPrice = 45.90          # PascalCase — errado para variaveis
ISACTIVE = True             # tudo maiusculo — errado para variaveis
calculateaverage = None     # sem separacao — dificil de ler
```

### CamelCase (PascalCase) para Classes

Classes em Python usam o padrao **CamelCase** (tambem chamado de PascalCase): cada palavra comeca com letra maiuscula, sem underline entre elas.

O nome "CamelCase" vem do ingles: "camel" significa camelo, e as letras maiusculas lembram as corcovas de um camelo.

```python
# Exemplos BOM: CamelCase para classes
# "Student" = Estudante
class Student:
    # "name" = nome, "age" = idade
    def __init__(self, name, age):
        self.name = name
        self.age = age


# "Shopping" = Compras, "Cart" = Carrinho
class ShoppingCart:
    def __init__(self):
        # "items" = itens
        self.items = []


# "Bank" = Banco, "Account" = Conta
class BankAccount:
    # "owner" = proprietario, "balance" = saldo
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance


# Criando objetos (instancias) das classes
# "student" = estudante (variavel em snake_case)
student = Student("Maria", 25)
print(f"Estudante: {student.name}, Idade: {student.age}")
```

Saida esperada:
```
Estudante: Maria, Idade: 25
```

```python
# Exemplos RUIM: nomes que NAO seguem CamelCase para classes
class shopping_cart:    # snake_case — errado para classes
    pass

class shoppingcart:     # tudo minusculo — errado para classes
    pass

class SHOPPINGCART:     # tudo maiusculo — errado para classes
    pass
```

### UPPER_CASE para Constantes

Constantes sao valores que nao mudam durante a execucao do programa. Em Python, usamos o padrao **UPPER_CASE** (todas as letras maiusculas, com underline separando palavras) para indicar que um valor e uma constante.

**Analogia:** Pense em placas de sinalizacao na estrada. Uma placa de "PARE" nunca muda — ela sempre diz "PARE". Constantes no codigo sao como essas placas: valores fixos que nao devem ser alterados.

> **Nota importante:** O Python nao impede que voce altere o valor de uma constante. A convencao UPPER_CASE e apenas um **aviso visual** para outros programadores: "este valor nao deve ser modificado". E uma questao de disciplina e comunicacao, nao de restricao da linguagem.

```python
# Constantes definidas no topo do arquivo, em UPPER_CASE
# "MAX" = maximo, "ATTEMPTS" = tentativas
MAX_ATTEMPTS = 3
# "DEFAULT" = padrao, "TIMEOUT" = tempo limite (em segundos)
DEFAULT_TIMEOUT = 30
# "BASE" = base, "URL" = endereco na internet
BASE_URL = "https://api.exemplo.com"
# "TAX" = imposto, "RATE" = taxa
TAX_RATE = 0.15
# "DAYS" = dias, "WEEK" = semana
DAYS_IN_WEEK = 7


# Usando as constantes no codigo
# "price" = preco, "final" = final
price = 100.0
# Calculamos o imposto usando a constante TAX_RATE
# "tax" = imposto
tax = price * TAX_RATE
# "final_price" = preco final
final_price = price + tax
print(f"Preco: R$ {price:.2f}")
print(f"Imposto ({TAX_RATE * 100}%): R$ {tax:.2f}")
print(f"Preco final: R$ {final_price:.2f}")
```

Saida esperada:
```
Preco: R$ 100.00
Imposto (15.0%): R$ 15.00
Preco final: R$ 115.00
```

### Resumo das Convencoes de Nomenclatura

| Tipo | Convencao | Exemplo | Quando usar |
|------|-----------|---------|-------------|
| Variaveis | snake_case | `student_name` | Sempre que criar uma variavel |
| Funcoes | snake_case | `calculate_total()` | Sempre que criar uma funcao |
| Classes | CamelCase | `ShoppingCart` | Sempre que criar uma classe |
| Constantes | UPPER_CASE | `MAX_ATTEMPTS` | Valores que nao mudam |
| Modulos/arquivos | snake_case | `my_module.py` | Nomes de arquivos Python |
| Pacotes/pastas | snake_case | `my_package/` | Nomes de pastas de pacotes |

### Nomes Descritivos vs Nomes Genericos

Alem de seguir a convencao correta, e fundamental escolher nomes que **descrevam** o que a variavel, funcao ou classe representa. Nomes genericos como `x`, `data` ou `temp` nao dizem nada sobre o proposito.

```python
# Exemplo RUIM: nomes genericos que nao dizem nada
# O que e "x"? O que e "y"? O que "f" faz?
x = 25
y = 1.75
z = x / (y * y)

def f(a, b):
    return a / (b * b)
```

```python
# Exemplo BOM: nomes descritivos que explicam o proposito
# "weight" = peso (em quilogramas), "kg" = quilogramas
weight_kg = 25
# "height" = altura (em metros), "m" = metros
height_m = 1.75
# "bmi" = IMC (Indice de Massa Corporal, Body Mass Index)
bmi = weight_kg / (height_m * height_m)

# "calculate" = calcular, "bmi" = IMC
def calculate_bmi(weight_kg, height_m):
    # Calcula o IMC dividindo o peso pelo quadrado da altura
    return weight_kg / (height_m * height_m)


# Testando a funcao
# "result" = resultado
result = calculate_bmi(70, 1.75)
print(f"IMC: {result:.2f}")
```

Saida esperada:
```
IMC: 22.86
```

> **Excecao:** Nomes curtos como `i`, `j`, `k` sao aceitaveis em loops curtos (como `for i in range(10)`), pois e uma convencao amplamente conhecida. Mas fora de loops, prefira nomes descritivos.

---

## Comentarios Uteis vs Desnecessarios

Comentarios sao textos no codigo que o Python ignora — eles existem apenas para ajudar humanos a entender o codigo. Mas nem todo comentario e util. Comentarios ruins podem ser piores do que nenhum comentario.

**Analogia:** Imagine que voce esta lendo um livro e alguem colou notas adesivas em todas as paginas. Se as notas dizem coisas uteis como "este capitulo explica o motivo do personagem" — otimo, ajudam na leitura. Mas se as notas dizem "esta pagina tem texto" ou "aqui tem um paragrafo" — sao inuteis e atrapalham.

### Comentarios Uteis: Explicam o "Por Que"

Bons comentarios explicam **por que** algo esta sendo feito, nao **o que** esta sendo feito. O codigo ja mostra o que esta acontecendo — o comentario deve explicar a razao por tras da decisao.

```python
# Exemplo BOM: comentarios que explicam o "por que"

# Usamos 0.15 como taxa porque a legislacao vigente define 15% de imposto
# "TAX_RATE" = taxa de imposto
TAX_RATE = 0.15

# Limitamos a 3 tentativas para evitar bloqueio da conta no servidor
# "MAX_ATTEMPTS" = maximo de tentativas
MAX_ATTEMPTS = 3

# Adicionamos 1 ao indice porque a contagem para o usuario comeca em 1, nao em 0
# "display" = exibicao, "index" = indice
display_index = index + 1

# Ordenamos por preco decrescente porque o cliente quer ver os mais caros primeiro
# "products" = produtos, "sorted" = ordenado
# "key" = chave de ordenacao, "reverse" = inverter (decrescente)
sorted_products = sorted(products, key=lambda p: p["price"], reverse=True)
```

### Comentarios Desnecessarios: Explicam o Obvio

Comentarios ruins repetem o que o codigo ja diz de forma clara. Eles poluem o codigo sem agregar valor.

```python
# Exemplo RUIM: comentarios que repetem o obvio

# Atribui 10 a x
x = 10

# Soma a com b
result = a + b

# Imprime o resultado
print(result)

# Incrementa o contador em 1
counter = counter + 1

# Verifica se a idade e maior que 18
if age > 18:
    # Imprime "Maior de idade"
    print("Maior de idade")
```

```python
# Exemplo BOM: o mesmo codigo sem comentarios desnecessarios
# (os nomes descritivos ja explicam o que o codigo faz)

# "product_count" = quantidade de produtos
product_count = 10

# "total_price" = preco total
total_price = base_price + shipping_cost

print(f"Total: R$ {total_price:.2f}")

# "attempts" = tentativas
attempts = attempts + 1

# Verificamos a maioridade para liberar acesso ao conteudo restrito
if user_age > 18:
    print("Acesso liberado")
```

### Comentarios Desatualizados: O Pior Tipo

O pior tipo de comentario e aquele que **contradiz** o codigo. Isso acontece quando alguem altera o codigo mas esquece de atualizar o comentario. Um comentario desatualizado e pior do que nenhum comentario, porque engana quem esta lendo.

```python
# Exemplo PERIGOSO: comentario desatualizado

# Calcula o desconto de 10%
# (ATENCAO: o codigo abaixo calcula 20%, nao 10%!)
# "discount" = desconto
discount = total * 0.20  # O comentario diz 10%, mas o codigo faz 20%
```

```python
# Exemplo BOM: comentario atualizado e correto

# Calcula o desconto de 20% conforme promocao de verao
# "discount" = desconto
discount = total * 0.20
```

> **Regra de ouro:** Se voce alterar o codigo, **sempre** verifique se os comentarios proximos ainda estao corretos. Comentario desatualizado e como uma placa de sinalizacao apontando para a direcao errada.

---

## Docstrings: Documentacao Dentro do Codigo

Docstrings sao textos especiais que documentam funcoes, classes e modulos. Diferente de comentarios comuns (que usam `#`), docstrings usam **tres aspas** (`"""`) e ficam logo na primeira linha dentro da funcao ou classe.

**Analogia:** Pense em docstrings como a **bula de um remedio**. Quando voce pega um remedio, a bula explica para que serve, como usar e quais os efeitos. Uma docstring faz o mesmo para uma funcao: explica o que ela faz, quais parametros recebe e o que retorna.

### Docstring Simples (Uma Linha)

Para funcoes simples, uma docstring de uma linha e suficiente:

```python
# "calculate" = calcular, "square" = quadrado
def calculate_square(number):
    """Calcula o quadrado de um numero."""
    # "number" = numero
    # "result" = resultado
    result = number ** 2
    return result


# Testando a funcao
print(f"Quadrado de 5: {calculate_square(5)}")
print(f"Quadrado de 3: {calculate_square(3)}")
```

Saida esperada:
```
Quadrado de 5: 25
Quadrado de 3: 9
```

### Docstring Completa (Multiplas Linhas)

Para funcoes mais complexas, use uma docstring com descricao, parametros e retorno:

```python
# "calculate" = calcular, "discount" = desconto, "price" = preco
def calculate_discounted_price(original_price, discount_percent):
    """Calcula o preco final apos aplicar um desconto.

    Parametros:
        original_price (float): Preco original do produto.
        discount_percent (float): Percentual de desconto (0 a 100).

    Retorna:
        float: Preco final com o desconto aplicado.
    """
    # "original_price" = preco original
    # "discount_percent" = percentual de desconto
    # Calculamos o valor do desconto
    # "discount_amount" = valor do desconto
    discount_amount = original_price * (discount_percent / 100)
    # Subtraimos o desconto do preco original
    # "final_price" = preco final
    final_price = original_price - discount_amount
    return final_price


# Testando a funcao
# "price" = preco
price = calculate_discounted_price(200.0, 15)
print(f"Preco com 15% de desconto: R$ {price:.2f}")
```

Saida esperada:
```
Preco com 15% de desconto: R$ 170.00
```

### Acessando Docstrings

Voce pode acessar a docstring de qualquer funcao usando o atributo `__doc__`:

```python
# "calculate" = calcular, "area" = area
def calculate_area(width, height):
    """Calcula a area de um retangulo multiplicando largura por altura."""
    # "width" = largura, "height" = altura
    return width * height


# Acessando a docstring da funcao
# "__doc__" = documentacao (atributo especial do Python)
print(calculate_area.__doc__)
```

Saida esperada:
```
Calcula a area de um retangulo multiplicando largura por altura.
```

> **Dica:** Quando voce usa a funcao `help()` no Python, ela exibe a docstring da funcao. Por isso, escrever boas docstrings ajuda voce e outros desenvolvedores a entender o codigo sem precisar ler a implementacao.

---

## Comparativos: Codigo Com e Sem Boas Praticas

Agora vamos ver exemplos completos de codigo **antes** (sem boas praticas) e **depois** (com boas praticas aplicadas). Esses comparativos mostram como as mesmas regras que aprendemos transformam codigo confuso em codigo profissional.

### Comparativo 1: Calculadora de Notas

**ANTES — Sem boas praticas:**

```python
import math
from datetime import datetime
import os
def f(n):
 s=0
 for i in n:
  s=s+i
 m=s/len(n)
 if m>=7:
  r="Aprovado"
 elif m>=5:
  r="Recuperacao"
 else:
  r="Reprovado"
 return m,r
notas=[8.5,6.0,7.5,9.0]
media,situacao=f(notas)
print(f"Media: {media} - {situacao}")
```

**DEPOIS — Com boas praticas aplicadas:**

```python
# Constante que define a nota minima para aprovacao
# "MIN" = minimo, "PASSING" = aprovacao, "GRADE" = nota
MIN_PASSING_GRADE = 7.0
# Constante que define a nota minima para recuperacao
# "RECOVERY" = recuperacao
MIN_RECOVERY_GRADE = 5.0


def calculate_average(grades):
    """Calcula a media aritmetica de uma lista de notas.

    Parametros:
        grades (list): Lista de notas (float).

    Retorna:
        float: Media aritmetica das notas.
    """
    # "grades" = notas
    # "total" = total (soma de todas as notas)
    total = sum(grades)
    # "average" = media
    average = total / len(grades)
    return average


def determine_status(average):
    """Determina a situacao do aluno com base na media.

    Parametros:
        average (float): Media do aluno.

    Retorna:
        str: Situacao do aluno (Aprovado, Recuperacao ou Reprovado).
    """
    # "average" = media
    # Verificamos se a media atinge o minimo para aprovacao
    if average >= MIN_PASSING_GRADE:
        return "Aprovado"
    # Verificamos se a media atinge o minimo para recuperacao
    elif average >= MIN_RECOVERY_GRADE:
        return "Recuperacao"
    # Se nao atingiu nenhum minimo, o aluno esta reprovado
    else:
        return "Reprovado"


# Lista de notas do aluno
# "grades" = notas
grades = [8.5, 6.0, 7.5, 9.0]

# Calculamos a media
# "average" = media
average = calculate_average(grades)

# Determinamos a situacao
# "status" = situacao
status = determine_status(average)

# Exibimos o resultado formatado
print(f"Media: {average:.2f} - {status}")
```

Saida esperada:
```
Media: 7.75 - Aprovado
```

> Observe as diferencas: o codigo "depois" tem nomes descritivos, funcoes separadas com responsabilidades claras, docstrings, constantes nomeadas, espacamento correto e comentarios que traduzem os termos em ingles. O resultado e o mesmo, mas a legibilidade e incomparavelmente melhor.

### Comparativo 2: Lista de Compras

**ANTES — Sem boas praticas:**

```python
l=[]
def a(l,n,p,q):
 l.append({"n":n,"p":p,"q":q})
def t(l):
 s=0
 for i in l:
  s=s+i["p"]*i["q"]
 return s
a(l,"Arroz",5.99,2)
a(l,"Feijao",8.50,1)
a(l,"Macarrao",3.75,3)
for i in l:
 print(f"{i['n']}: R$ {i['p']:.2f} x {i['q']}")
print(f"Total: R$ {t(l):.2f}")
```

**DEPOIS — Com boas praticas aplicadas:**

```python
def add_item(shopping_list, name, price, quantity):
    """Adiciona um item a lista de compras.

    Parametros:
        shopping_list (list): Lista de compras atual.
        name (str): Nome do produto.
        price (float): Preco unitario do produto.
        quantity (int): Quantidade desejada.
    """
    # "shopping_list" = lista de compras
    # "name" = nome, "price" = preco, "quantity" = quantidade
    # Criamos um dicionario representando o item
    # "item" = item/produto
    item = {
        "name": name,
        "price": price,
        "quantity": quantity
    }
    # Adicionamos o item a lista de compras
    shopping_list.append(item)


def calculate_total(shopping_list):
    """Calcula o valor total da lista de compras.

    Parametros:
        shopping_list (list): Lista de compras com itens.

    Retorna:
        float: Valor total de todos os itens.
    """
    # "total" = total (soma dos valores)
    total = 0
    # Percorremos cada item da lista de compras
    for item in shopping_list:
        # Multiplicamos preco pela quantidade e somamos ao total
        total = total + item["price"] * item["quantity"]
    return total


# Criamos a lista de compras vazia
# "shopping_list" = lista de compras
shopping_list = []

# Adicionamos os produtos a lista
add_item(shopping_list, "Arroz", 5.99, 2)
add_item(shopping_list, "Feijao", 8.50, 1)
add_item(shopping_list, "Macarrao", 3.75, 3)

# Exibimos cada item da lista
for item in shopping_list:
    # Formatamos a saida com nome, preco e quantidade
    print(f"{item['name']}: R$ {item['price']:.2f} x {item['quantity']}")

# Calculamos e exibimos o total
# "total" = total
total = calculate_total(shopping_list)
print(f"Total: R$ {total:.2f}")
```

Saida esperada:
```
Arroz: R$ 5.99 x 2
Feijao: R$ 8.50 x 1
Macarrao: R$ 3.75 x 3
Total: R$ 31.73
```

### Comparativo 3: Validacao de Dados

**ANTES — Sem boas praticas:**

```python
def v(d):
 if d["n"]=="" or d["n"]==None:
  return False
 if d["p"]<0:
  return False
 if d["q"]<0:
  return False
 return True
d={"n":"Arroz","p":5.99,"q":10}
if v(d):
 print("ok")
else:
 print("erro")
```

**DEPOIS — Com boas praticas aplicadas:**

```python
def validate_product(product):
    """Valida os dados de um produto antes de salvar.

    Parametros:
        product (dict): Dicionario com dados do produto.

    Retorna:
        bool: True se os dados sao validos, False caso contrario.
    """
    # "product" = produto
    # Verificamos se o nome esta preenchido
    # "name" = nome
    if not product["name"] or product["name"].strip() == "":
        print("Erro: o nome do produto nao pode ser vazio")
        return False

    # Verificamos se o preco e positivo
    # "price" = preco
    if product["price"] < 0:
        print("Erro: o preco nao pode ser negativo")
        return False

    # Verificamos se a quantidade e positiva
    # "quantity" = quantidade
    if product["quantity"] < 0:
        print("Erro: a quantidade nao pode ser negativa")
        return False

    # Todos os dados sao validos
    return True


# Criamos um produto para testar a validacao
# "product" = produto
product = {
    "name": "Arroz",       # nome do produto
    "price": 5.99,         # preco do produto
    "quantity": 10          # quantidade em estoque
}

# Validamos o produto e exibimos o resultado
# "is_valid" = e valido
is_valid = validate_product(product)

if is_valid:
    print("Produto valido! Dados aceitos.")
else:
    print("Produto invalido! Corrija os dados.")
```

Saida esperada:
```
Produto valido! Dados aceitos.
```

---

## Outras Boas Praticas Importantes

### Evite Numeros Magicos

"Numeros magicos" sao valores numericos que aparecem no codigo sem explicacao. Substitua-os por constantes com nomes descritivos.

```python
# Exemplo RUIM: numeros magicos
# O que significa 0.15? E 3? E 79?
total = price * 0.15
if attempts > 3:
    print("Bloqueado")
if len(line) > 79:
    print("Linha muito longa")
```

```python
# Exemplo BOM: constantes nomeadas
# "TAX_RATE" = taxa de imposto (15%)
TAX_RATE = 0.15
# "MAX_ATTEMPTS" = maximo de tentativas
MAX_ATTEMPTS = 3
# "MAX_LINE_LENGTH" = comprimento maximo da linha (PEP 8)
MAX_LINE_LENGTH = 79

# Agora o codigo e autoexplicativo
# "total" = total, "tax" = imposto
tax = price * TAX_RATE
# "attempts" = tentativas
if attempts > MAX_ATTEMPTS:
    print("Bloqueado")
# "line" = linha
if len(line) > MAX_LINE_LENGTH:
    print("Linha muito longa")
```

### Uma Funcao, Uma Responsabilidade

Cada funcao deve fazer **uma unica coisa** e faze-la bem. Se uma funcao faz muitas coisas, divida-a em funcoes menores.

```python
# Exemplo RUIM: funcao que faz muitas coisas
def process_order(items):
    # Calcula total, aplica desconto, valida, imprime recibo...
    total = 0
    for item in items:
        total += item["price"] * item["quantity"]
    if total > 100:
        total = total * 0.9
    if total <= 0:
        print("Erro: pedido vazio")
        return
    print("=== RECIBO ===")
    for item in items:
        print(f"{item['name']}: R$ {item['price']:.2f}")
    print(f"Total: R$ {total:.2f}")
```

```python
# Exemplo BOM: funcoes separadas, cada uma com uma responsabilidade

# Constante para o desconto em compras acima de R$ 100
# "BULK" = grande quantidade, "DISCOUNT" = desconto
BULK_DISCOUNT_RATE = 0.10
# "BULK" = grande quantidade, "THRESHOLD" = limite
BULK_DISCOUNT_THRESHOLD = 100


def calculate_order_total(items):
    """Calcula o valor total do pedido."""
    # "items" = itens, "total" = total
    total = 0
    for item in items:
        # "price" = preco, "quantity" = quantidade
        total = total + item["price"] * item["quantity"]
    return total


def apply_discount(total):
    """Aplica desconto se o total ultrapassar o limite."""
    # "total" = total
    if total > BULK_DISCOUNT_THRESHOLD:
        # Aplica desconto de 10% para compras acima de R$ 100
        total = total * (1 - BULK_DISCOUNT_RATE)
    return total


def print_receipt(items, total):
    """Imprime o recibo formatado."""
    # "items" = itens, "total" = total
    print("=== RECIBO ===")
    for item in items:
        # Exibe cada item com nome e preco
        print(f"  {item['name']}: R$ {item['price']:.2f}")
    print(f"Total: R$ {total:.2f}")


# Usando as funcoes separadas
# "items" = itens do pedido
items = [
    {"name": "Caderno", "price": 15.90, "quantity": 2},
    {"name": "Caneta", "price": 3.50, "quantity": 5},
    {"name": "Borracha", "price": 2.00, "quantity": 3}
]

# Cada passo e claro e independente
# "total" = total
total = calculate_order_total(items)
total = apply_discount(total)
print_receipt(items, total)
```

Saida esperada:
```
=== RECIBO ===
  Caderno: R$ 15.90
  Caneta: R$ 3.50
  Borracha: R$ 2.00
Total: R$ 55.30
```

### Mantenha o Codigo Simples

O Zen do Python (que voce aprendeu no modulo 05) diz: "Simples e melhor que complexo". Sempre prefira a solucao mais simples e direta.

```python
# Exemplo RUIM: desnecessariamente complexo
# "is_adult" = e adulto
def is_adult(age):
    if age >= 18:
        return True
    else:
        return False
```

```python
# Exemplo BOM: simples e direto
# "is_adult" = e adulto, "age" = idade
def is_adult(age):
    """Verifica se a pessoa e maior de idade."""
    return age >= 18


# Testando a funcao
print(f"25 anos e adulto? {is_adult(25)}")
print(f"15 anos e adulto? {is_adult(15)}")
```

Saida esperada:
```
25 anos e adulto? True
15 anos e adulto? False
```

---

## Para Saber Mais

- [W3Schools — Python PEP 8](https://www.w3schools.com/python/python_syntax.asp)
  _Aqui voce encontra exemplos de sintaxe Python que seguem as boas praticas_
- [PEP 8 — Guia de Estilo Oficial (em ingles)](https://peps.python.org/pep-0008/)
  _O documento oficial completo da PEP 8, escrito pelos criadores do Python_
- [Documentacao Oficial Python — Guia de Estilo](https://docs.python.org/pt-br/3/tutorial/controlflow.html#intermezzo-coding-style)
  _Secao da documentacao oficial em portugues sobre estilo de codigo_
- [W3Schools — Python Comments](https://www.w3schools.com/python/python_comments.asp)
  _Mais exemplos sobre como usar comentarios em Python_
- [W3Schools — Python Functions](https://www.w3schools.com/python/python_functions.asp)
  _Revisao sobre funcoes, incluindo docstrings e boas praticas_
- [Real Python — PEP 8 Guide (em ingles)](https://realpython.com/python-pep8/)
  _Um guia detalhado e pratico sobre a PEP 8 para quem quiser se aprofundar_

> **Dica:** Consulte o [Glossario](00-glossario.md) para revisar termos como "PEP 8", "snake_case", "CamelCase", "docstring" e outros conceitos deste modulo.

---

## Perguntas Frequentes (FAQ)

**P: O que e a PEP 8?**
**R:** A PEP 8 e o guia de estilo oficial do Python. Ela define convencoes de formatacao, nomenclatura e organizacao de codigo que toda a comunidade Python segue. PEP significa "Python Enhancement Proposal" (Proposta de Melhoria do Python) e o numero 8 e o identificador dessa proposta especifica.

**P: Sou obrigado a seguir a PEP 8?**
**R:** Nao, o Python nao vai dar erro se voce nao seguir. Mas seguir a PEP 8 e fortemente recomendado porque torna seu codigo mais legivel, consistente e profissional. Empresas e projetos de codigo aberto esperam que desenvolvedores sigam essas convencoes.

**P: O que acontece se minha linha tiver mais de 79 caracteres?**
**R:** O Python vai executar o codigo normalmente — o limite de 79 caracteres e uma recomendacao de estilo, nao uma regra da linguagem. Mas linhas muito longas sao dificeis de ler, especialmente quando voce abre dois arquivos lado a lado no editor. Quebre linhas longas usando parenteses ou barras invertidas.

**P: O que e snake_case?**
**R:** snake_case e uma convencao de nomenclatura onde todas as letras sao minusculas e as palavras sao separadas por underline (sublinhado `_`). Exemplo: `student_name`, `calculate_total`. O nome vem do ingles: "snake" significa cobra, e o underline entre as palavras lembra uma cobra rastejando. Em Python, usamos snake_case para variaveis e funcoes.

**P: O que e CamelCase?**
**R:** CamelCase (tambem chamado PascalCase) e uma convencao onde cada palavra comeca com letra maiuscula, sem separadores. Exemplo: `ShoppingCart`, `BankAccount`. O nome vem do ingles: "camel" significa camelo, e as letras maiusculas lembram as corcovas de um camelo. Em Python, usamos CamelCase para nomes de classes.

**P: Quando devo usar UPPER_CASE?**
**R:** Use UPPER_CASE (todas as letras maiusculas com underline) para constantes — valores que nao devem mudar durante a execucao do programa. Exemplo: `MAX_ATTEMPTS = 3`, `TAX_RATE = 0.15`. Lembre-se que o Python nao impede a alteracao — e uma convencao visual para comunicar que o valor e fixo.

**P: Qual a diferenca entre comentario e docstring?**
**R:** Comentarios usam `#` e podem aparecer em qualquer lugar do codigo. Docstrings usam tres aspas (`"""`) e ficam na primeira linha dentro de funcoes, classes ou modulos. A principal diferenca e que docstrings podem ser acessadas pelo programa (usando `__doc__` ou `help()`), enquanto comentarios sao completamente ignorados pelo Python.

**P: Preciso colocar comentario em toda linha do codigo?**
**R:** Nao. Comentarios devem ser usados quando agregam valor — explicando o "por que" de uma decisao, traduzindo termos em ingles ou esclarecendo logica complexa. Se o codigo e claro e os nomes sao descritivos, muitas linhas nao precisam de comentario. Comentarios excessivos poluem o codigo.

**P: O que sao "numeros magicos"?**
**R:** Numeros magicos sao valores numericos que aparecem no codigo sem explicacao. Por exemplo, `if attempts > 3` — o que significa esse 3? Substitua por uma constante nomeada: `MAX_ATTEMPTS = 3` e depois `if attempts > MAX_ATTEMPTS`. Agora o codigo e autoexplicativo.

**P: E normal achar dificil escolher bons nomes?**
**R:** Sim, completamente normal. Escolher bons nomes e uma das partes mais dificeis da programacao — ate programadores experientes gastam tempo pensando em nomes. Com a pratica, fica mais natural. Uma dica: se voce nao consegue pensar em um bom nome, talvez a funcao esteja fazendo coisas demais e precise ser dividida.

**P: Posso usar acentos em nomes de variaveis?**
**R:** Tecnicamente, o Python 3 aceita caracteres acentuados em nomes de variaveis (como `preço = 10`). Porem, isso nao e recomendado. A convencao profissional e usar nomes em ingles (sem acentos) para variaveis, funcoes e classes. Acentos podem causar problemas em alguns sistemas e editores.

**P: Por que usar nomes em ingles se estou aprendendo em portugues?**
**R:** Usar nomes em ingles no codigo e uma convencao profissional seguida no mundo inteiro. Isso facilita a colaboracao com desenvolvedores de outros paises, a leitura de codigo de bibliotecas externas e a sua insercao no mercado de trabalho. Os comentarios em portugues garantem que voce entenda tudo enquanto aprende.

**P: O que significa "uma funcao, uma responsabilidade"?**
**R:** Significa que cada funcao deve fazer apenas uma coisa. Se uma funcao calcula, valida e imprime ao mesmo tempo, ela tem muitas responsabilidades. Divida-a em funcoes menores: uma que calcula, outra que valida e outra que imprime. Isso torna o codigo mais facil de entender, testar e reutilizar.

**P: Como sei se meu comentario e util ou desnecessario?**
**R:** Faca o teste: leia o codigo sem o comentario. Se voce entende perfeitamente o que o codigo faz, o comentario provavelmente e desnecessario. Se o codigo e confuso sem o comentario, ele e util. Bons comentarios explicam o "por que", nao o "o que".

**P: O que e uma docstring de funcao?**
**R:** E um texto entre tres aspas (`"""`) colocado na primeira linha dentro de uma funcao. Ela descreve o que a funcao faz, quais parametros recebe e o que retorna. Voce pode acessar a docstring com `funcao.__doc__` ou `help(funcao)`. E como a "bula" da funcao.

**P: Preciso escrever docstrings em todas as funcoes?**
**R:** Para funcoes muito simples e obvias (como `def is_adult(age): return age >= 18`), uma docstring curta de uma linha e suficiente. Para funcoes mais complexas, uma docstring completa com parametros e retorno e muito util. Em projetos profissionais, docstrings sao esperadas em todas as funcoes publicas.

**P: O que e indentacao e por que e importante na PEP 8?**
**R:** Indentacao e o espacamento a esquerda de cada linha de codigo. Em Python, a indentacao define a estrutura do codigo (blocos dentro de funcoes, loops, condicionais). A PEP 8 recomenda usar **4 espacos** por nivel de indentacao — nunca tabulacoes (tabs). Voce aprendeu mais sobre isso no modulo 10.

**P: Posso misturar tabs e espacos na indentacao?**
**R:** Nao. O Python 3 nao permite misturar tabs e espacos na mesma indentacao e vai gerar um erro `TabError`. A PEP 8 recomenda usar sempre 4 espacos. Configure seu editor (VSCode) para inserir espacos quando voce pressionar a tecla Tab.

**P: Boas praticas sao as mesmas em todas as linguagens?**
**R:** Os principios gerais (nomes descritivos, codigo limpo, funcoes pequenas) sao universais. Mas cada linguagem tem suas proprias convencoes de estilo. Em Python, usamos snake_case para variaveis; em Java, usamos camelCase. Em Python, temos a PEP 8; em JavaScript, existem guias como o do Airbnb. O importante e seguir as convencoes da linguagem que voce esta usando.

**P: Existe alguma ferramenta que verifica se meu codigo segue a PEP 8?**
**R:** Sim, existem varias ferramentas chamadas "linters" que analisam seu codigo e apontam violacoes da PEP 8. As mais populares sao `flake8`, `pylint` e `black` (que formata automaticamente). No VSCode, voce pode instalar extensoes que mostram avisos diretamente no editor. Essas ferramentas sao muito uteis para aprender e manter a consistencia.

**P: E normal errar as convencoes no comeco?**
**R:** Completamente normal. Ninguem escreve codigo perfeito desde o primeiro dia. As boas praticas se tornam habito com o tempo e a pratica. O importante e conhecer as regras e tentar aplica-las. Com o tempo, escrever codigo limpo se torna natural, como escrever com boa caligrafia.

---

## Exercicios de Fixacao

Os exercicios deste modulo estao no arquivo separado: [Exercicios — Boas Praticas](27-boas-praticas-exercicios.md)

---

[<- Anterior: pip e Dependencias](26-pip-dependencias.md) | [Glossario](00-glossario.md) | [Proximo: Modelagem de Dados ->](28-modelagem-dados.md)