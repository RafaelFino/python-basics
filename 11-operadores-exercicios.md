# Exercicios — Modulo 11: Operadores Logicos e Matematicos

[<- Voltar ao Modulo 11](11-operadores.md) | [Glossario](00-glossario.md)

> **Como usar estes exercicios:**
> 1. Leia o enunciado com atencao
> 2. Leia as dicas antes de comecar
> 3. Tente resolver sozinho
> 4. Use a Proposta de Teste para verificar se sua solucao funciona
> 5. So depois consulte a Resposta Comentada
>
> **Como testar:** Salve seu codigo na pasta `~/meus-projetos/python-curso/modulo-11/` e execute com `python3 nome_do_arquivo.py`.

---

## Exercicio 1 — Calculadora Basica — Nivel: Basico

### Enunciado
Peca dois numeros ao usuario e exiba o resultado das quatro operacoes basicas: soma, subtracao, multiplicacao e divisao.

### Dicas
- Use `float()` para aceitar numeros decimais
- Calcule cada operacao separadamente

### Proposta de Teste
- **Caso basico:** Numeros: `10` e `3` — Soma: 13.0, Subtracao: 7.0, Multiplicacao: 30.0, Divisao: 3.333...
- **Caso de borda:** Numeros: `0` e `5` — Soma: 5.0, Subtracao: -5.0, Multiplicacao: 0.0, Divisao: 0.0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos dois numeros ao usuario
# "number_a" = primeiro numero, "number_b" = segundo numero
number_a = float(input("Primeiro numero: "))
number_b = float(input("Segundo numero: "))

# Calculamos as quatro operacoes
# + soma, - subtrai, * multiplica, / divide
print(f"{number_a} + {number_b} = {number_a + number_b}")
print(f"{number_a} - {number_b} = {number_a - number_b}")
print(f"{number_a} * {number_b} = {number_a * number_b}")
print(f"{number_a} / {number_b} = {number_a / number_b}")
```

---

## Exercicio 2 — Par ou Impar — Nivel: Basico

### Enunciado
Peca um numero inteiro ao usuario e exiba se ele e par ou impar. (Um numero e par quando o resto da divisao por 2 e zero. Exemplo: 8 dividido por 2 = 4 com resto 0, entao 8 e par.)

### Dicas
- Use o operador modulo `%`: `numero % 2`
- Se o resultado for `0`, e par; se for `1`, e impar

### Proposta de Teste
- **Caso basico:** Numero: `8` — Resto: 0, Par
- **Caso de borda:** Numero: `7` — Resto: 1, Impar

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos um numero inteiro
# "number" = numero
number = int(input("Digite um numero inteiro: "))

# Calculamos o resto da divisao por 2 usando o operador %
# "remainder" = resto
# Se o resto for 0, o numero e divisivel por 2 (par)
remainder = number % 2

# Exibimos o resultado
print(f"Numero: {number}")
print(f"Resto da divisao por 2: {remainder}")

# Verificamos se e par ou impar
# == compara se o resto e igual a zero
if remainder == 0:
    print("O numero e PAR")
else:
    print("O numero e IMPAR")
```

---

## Exercicio 3 — Potencia de Numeros — Nivel: Basico

### Enunciado
Peca um numero (base) e um expoente ao usuario e calcule a potencia. (Potencia e multiplicar a base por ela mesma o numero de vezes indicado pelo expoente. Exemplo: 3 elevado a 4 = 3 x 3 x 3 x 3 = 81.)

### Dicas
- Use o operador `**` para exponenciacao
- Base e expoente podem ser inteiros

### Proposta de Teste
- **Caso basico:** Base: `2`, Expoente: `10` — Resultado: 1024
- **Caso de borda:** Base: `5`, Expoente: `0` — Resultado: 1 (qualquer numero elevado a 0 e 1)

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos a base e o expoente
# "base" = base (o numero que sera multiplicado)
base = int(input("Base: "))

# "exponent" = expoente (quantas vezes multiplicar)
exponent = int(input("Expoente: "))

# Calculamos a potencia usando **
# ** e o operador de exponenciacao
# "result" = resultado
result = base ** exponent

# Exibimos o resultado
print(f"{base} elevado a {exponent} = {result}")
```

---

## Exercicio 4 — Divisao Completa — Nivel: Basico

### Enunciado
Peca dois numeros inteiros e exiba: o resultado da divisao decimal, o resultado da divisao inteira e o resto da divisao.

### Dicas
- Divisao decimal: `/`
- Divisao inteira: `//`
- Resto (modulo): `%`

### Proposta de Teste
- **Caso basico:** Numeros: `17` e `5` — Decimal: 3.4, Inteira: 3, Resto: 2
- **Caso de borda:** Numeros: `10` e `2` — Decimal: 5.0, Inteira: 5, Resto: 0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos dois numeros inteiros
# "dividend" = dividendo (numero a ser dividido)
dividend = int(input("Dividendo: "))

# "divisor" = divisor (numero pelo qual dividimos)
divisor = int(input("Divisor: "))

# Calculamos os tres tipos de resultado
# / = divisao decimal (resultado com casas decimais)
# // = divisao inteira (apenas a parte inteira)
# % = modulo (o resto da divisao)
print(f"Divisao decimal: {dividend} / {divisor} = {dividend / divisor}")
print(f"Divisao inteira: {dividend} // {divisor} = {dividend // divisor}")
print(f"Resto (modulo): {dividend} % {divisor} = {dividend % divisor}")
```

---

## Exercicio 5 — Comparando Idades — Nivel: Intermediario

### Enunciado
Peca a idade de duas pessoas e exiba o resultado de todas as comparacoes possiveis entre elas.

### Dicas
- Use todos os operadores de comparacao: `==`, `!=`, `>`, `<`, `>=`, `<=`
- Cada comparacao retorna True ou False

### Proposta de Teste
- **Caso basico:** Idades: `25` e `30` — Igual: False, Diferente: True, Maior: False, Menor: True, etc.
- **Caso de borda:** Idades: `20` e `20` — Igual: True, Diferente: False

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos as idades de duas pessoas
# "age_a" = idade da pessoa A, "age_b" = idade da pessoa B
age_a = int(input("Idade da pessoa A: "))
age_b = int(input("Idade da pessoa B: "))

# Realizamos todas as comparacoes
# Cada comparacao retorna True (verdadeiro) ou False (falso)
print(f"\nComparacoes entre {age_a} e {age_b}:")
print(f"Igual (==): {age_a == age_b}")
print(f"Diferente (!=): {age_a != age_b}")
print(f"A maior que B (>): {age_a > age_b}")
print(f"A menor que B (<): {age_a < age_b}")
print(f"A maior ou igual a B (>=): {age_a >= age_b}")
print(f"A menor ou igual a B (<=): {age_a <= age_b}")
```

---

## Exercicio 6 — Verificacao de Acesso — Nivel: Intermediario

### Enunciado
Peca a idade e se a pessoa tem ingresso (sim/nao). Exiba se a pessoa pode entrar no evento (precisa ter 18 anos ou mais E ter ingresso).

### Dicas
- Use `and` para combinar as duas condicoes
- Converta a resposta "sim"/"nao" para booleano

### Proposta de Teste
- **Caso basico:** Idade: `20`, Ingresso: `sim` — Pode entrar: True
- **Caso de borda:** Idade: `20`, Ingresso: `nao` — Pode entrar: False
- **Caso de borda:** Idade: `16`, Ingresso: `sim` — Pode entrar: False

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos a idade
# "age" = idade
age = int(input("Sua idade: "))

# Pedimos se tem ingresso
# "ticket_input" = entrada sobre ingresso
ticket_input = input("Tem ingresso? (sim/nao): ")

# Convertemos para booleano: "sim" vira True, qualquer outra coisa vira False
# "has_ticket" = tem ingresso
has_ticket = ticket_input == "sim"

# Verificamos se pode entrar: precisa ter 18+ E ter ingresso
# and = E — ambas as condicoes precisam ser verdadeiras
# "can_enter" = pode entrar
can_enter = age >= 18 and has_ticket

# Exibimos o resultado
print(f"Idade: {age}")
print(f"Tem ingresso: {has_ticket}")
print(f"Pode entrar: {can_enter}")
```

---

## Exercicio 7 — Desconto por Condicao — Nivel: Intermediario

### Enunciado
Peca a idade e se a pessoa e estudante (sim/nao). A pessoa tem desconto se for menor de 12 anos OU maior de 60 anos OU for estudante.

### Dicas
- Use `or` para combinar as condicoes (qualquer uma basta)
- Tres condicoes separadas por `or`

### Proposta de Teste
- **Caso basico:** Idade: `10`, Estudante: `nao` — Desconto: True (menor de 12)
- **Caso de borda:** Idade: `30`, Estudante: `sim` — Desconto: True (estudante)
- **Caso de borda:** Idade: `30`, Estudante: `nao` — Desconto: False

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos a idade e se e estudante
# "age" = idade
age = int(input("Idade: "))

# "student_input" = entrada sobre ser estudante
student_input = input("E estudante? (sim/nao): ")
# "is_student" = e estudante
is_student = student_input == "sim"

# Verificamos se tem desconto
# or = OU — basta UMA condicao ser verdadeira
# Tem desconto se: menor de 12 OU maior de 60 OU estudante
# "has_discount" = tem desconto
has_discount = age < 12 or age > 60 or is_student

# Exibimos o resultado
print(f"Idade: {age}")
print(f"Estudante: {is_student}")
print(f"Tem desconto: {has_discount}")
```

---

## Exercicio 8 — Precedencia na Pratica — Nivel: Intermediario

### Enunciado
Sem executar, preveja o resultado de cada expressao. Depois execute para conferir.

```
a) 2 + 3 * 4
b) (2 + 3) * 4
c) 10 - 2 ** 3
d) 20 / 4 + 1
e) 15 % 4 * 2
```

### Dicas
- Lembre da precedencia: `**` primeiro, depois `*`, `/`, `//`, `%`, depois `+`, `-`
- Use parenteses mentalmente para visualizar a ordem

### Proposta de Teste
- a) 14, b) 20, c) 2, d) 6.0, e) 6

### Resposta Comentada

> **Importante:** Tente prever os resultados antes de executar!

```python
# a) Multiplicacao (*) tem precedencia sobre soma (+)
# Python calcula: 3 * 4 = 12, depois 2 + 12 = 14
print("a) 2 + 3 * 4 =", 2 + 3 * 4)

# b) Parenteses forcam a soma primeiro
# Python calcula: (2 + 3) = 5, depois 5 * 4 = 20
print("b) (2 + 3) * 4 =", (2 + 3) * 4)

# c) Exponenciacao (**) tem precedencia sobre subtracao (-)
# Python calcula: 2 ** 3 = 8, depois 10 - 8 = 2
print("c) 10 - 2 ** 3 =", 10 - 2 ** 3)

# d) Divisao (/) tem precedencia sobre soma (+)
# Python calcula: 20 / 4 = 5.0, depois 5.0 + 1 = 6.0
print("d) 20 / 4 + 1 =", 20 / 4 + 1)

# e) Modulo (%) e multiplicacao (*) tem mesma precedencia — avalia da esquerda para direita
# Python calcula: 15 % 4 = 3, depois 3 * 2 = 6
print("e) 15 % 4 * 2 =", 15 % 4 * 2)
```

---

## Exercicio 9 — Calculadora de Gorjeta — Nivel: Avancado

### Enunciado
Peca o valor da conta do restaurante e a porcentagem de gorjeta desejada. Calcule o valor da gorjeta e o total a pagar. (Gorjeta e um valor extra que voce paga alem da conta, como agradecimento pelo servico. Para calcular: valor da conta multiplicado pela porcentagem dividida por 100.)

### Dicas
- Gorjeta: `conta * (porcentagem / 100)`
- Total: conta + gorjeta
- Use `float()` para ambos os valores

### Proposta de Teste
- **Caso basico:** Conta: `80`, Gorjeta: `15` — Valor gorjeta: 12.0, Total: 92.0
- **Caso de borda:** Conta: `100`, Gorjeta: `0` — Valor gorjeta: 0.0, Total: 100.0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos o valor da conta e a porcentagem de gorjeta
# "bill_amount" = valor da conta (bill = conta)
bill_amount = float(input("Valor da conta: R$ "))

# "tip_percentage" = porcentagem da gorjeta (tip = gorjeta)
# Porcentagem e uma forma de representar uma parte de 100
# 15% significa 15 de cada 100
tip_percentage = float(input("Porcentagem de gorjeta (%): "))

# Calculamos o valor da gorjeta
# "tip_value" = valor da gorjeta
# Para calcular a porcentagem: valor * (porcentagem / 100)
# Exemplo: 15% de 80 = 80 * (15 / 100) = 80 * 0.15 = 12
tip_value = bill_amount * (tip_percentage / 100)

# Calculamos o total a pagar (conta + gorjeta)
# "total" = total
total = bill_amount + tip_value

# Exibimos o resultado
print(f"Conta: R$ {bill_amount}")
print(f"Gorjeta ({tip_percentage}%): R$ {tip_value}")
print(f"Total a pagar: R$ {total}")
```

---

## Exercicio 10 — Distribuindo Itens — Nivel: Avancado

### Enunciado
Voce tem uma quantidade de itens para distribuir igualmente entre grupos. Peca a quantidade de itens e o numero de grupos. Exiba quantos itens cada grupo recebe e quantos sobram. (Use divisao inteira para os itens por grupo e modulo para a sobra.)

### Dicas
- Itens por grupo: `//` (divisao inteira)
- Sobra: `%` (modulo)

### Proposta de Teste
- **Caso basico:** Itens: `23`, Grupos: `5` — Cada grupo: 4, Sobram: 3
- **Caso de borda:** Itens: `10`, Grupos: `2` — Cada grupo: 5, Sobram: 0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos a quantidade de itens e o numero de grupos
# "total_items" = total de itens
total_items = int(input("Quantidade de itens: "))

# "groups" = grupos (numero de grupos para distribuir)
groups = int(input("Numero de grupos: "))

# Calculamos quantos itens cada grupo recebe
# // = divisao inteira (apenas a parte inteira, sem decimais)
# "items_per_group" = itens por grupo
items_per_group = total_items // groups

# Calculamos quantos itens sobram
# % = modulo (o resto da divisao)
# "leftover" = sobra
leftover = total_items % groups

# Exibimos o resultado
print(f"Total de itens: {total_items}")
print(f"Numero de grupos: {groups}")
print(f"Itens por grupo: {items_per_group}")
print(f"Itens que sobram: {leftover}")
```

---

## Exercicio 11 — Expressao Logica Complexa — Nivel: Avancado

### Enunciado
Um cinema oferece desconto se a pessoa atender a PELO MENOS UMA das condicoes: (1) ter menos de 12 anos, (2) ter 60 anos ou mais, (3) ser estudante E o dia ser quarta-feira. Peca os dados e verifique se tem desconto.

### Dicas
- Combine `and` e `or` com parenteses
- A condicao 3 usa `and` (estudante E quarta)
- As tres condicoes sao combinadas com `or`

### Proposta de Teste
- **Caso basico:** Idade: `25`, Estudante: `sim`, Dia: `quarta` — Desconto: True
- **Caso de borda:** Idade: `25`, Estudante: `sim`, Dia: `segunda` — Desconto: False
- **Caso de borda:** Idade: `65`, Estudante: `nao`, Dia: `segunda` — Desconto: True

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Coletamos os dados
# "age" = idade
age = int(input("Idade: "))

# "student_input" = entrada sobre ser estudante
student_input = input("E estudante? (sim/nao): ")
# "is_student" = e estudante
is_student = student_input == "sim"

# "day" = dia da semana
day = input("Dia da semana (ex: quarta): ")

# Verificamos cada condicao separadamente para clareza
# "is_child" = e crianca (menor de 12)
is_child = age < 12

# "is_senior" = e idoso (60 anos ou mais)
is_senior = age >= 60

# "student_on_wednesday" = estudante na quarta-feira
# and = E — precisa ser estudante E ser quarta
student_on_wednesday = is_student and day == "quarta"

# Combinamos com or: qualquer uma das condicoes basta
# "has_discount" = tem desconto
has_discount = is_child or is_senior or student_on_wednesday

# Exibimos o resultado
print(f"\nIdade: {age}")
print(f"Estudante: {is_student}")
print(f"Dia: {day}")
print(f"Tem desconto: {has_discount}")
```

---

## Exercicio 12 — Calculadora de Juros Simples — Nivel: Avancado

### Enunciado
Peca o valor inicial (capital), a taxa de juros mensal (em porcentagem) e o numero de meses. Calcule o valor dos juros e o valor final. (Juros simples: capital multiplicado pela taxa dividida por 100, multiplicado pelo numero de meses. Juros e o valor extra que voce paga ou recebe por emprestar dinheiro.)

### Dicas
- Juros = capital * (taxa / 100) * meses
- Valor final = capital + juros
- Use `float()` para capital e taxa, `int()` para meses

### Proposta de Teste
- **Caso basico:** Capital: `1000`, Taxa: `2`, Meses: `12` — Juros: 240.0, Final: 1240.0
- **Caso de borda:** Capital: `500`, Taxa: `0`, Meses: `6` — Juros: 0.0, Final: 500.0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos os dados do calculo de juros
# "capital" = capital (valor inicial do dinheiro)
capital = float(input("Valor inicial (capital): R$ "))

# "interest_rate" = taxa de juros (interest = juros, rate = taxa)
# Porcentagem: 2% significa 2 de cada 100
interest_rate = float(input("Taxa de juros mensal (%): "))

# "months" = meses (periodo de tempo)
months = int(input("Numero de meses: "))

# Calculamos os juros simples
# "interest_value" = valor dos juros
# Formula: capital * (taxa / 100) * meses
# Exemplo: 1000 * (2 / 100) * 12 = 1000 * 0.02 * 12 = 240
interest_value = capital * (interest_rate / 100) * months

# Calculamos o valor final (capital + juros)
# "final_amount" = valor final
final_amount = capital + interest_value

# Exibimos o resultado
print(f"\nCapital inicial: R$ {capital}")
print(f"Taxa mensal: {interest_rate}%")
print(f"Periodo: {months} meses")
print(f"Juros acumulados: R$ {interest_value}")
print(f"Valor final: R$ {final_amount}")
```

---

[<- Voltar ao Modulo 11](11-operadores.md) | [Glossario](00-glossario.md)
