# Exercicios — Modulo 18: Tratamento de Erros

[<- Voltar ao Modulo 18](18-tratamento-erros.md) | [Glossario](00-glossario.md)

> **Como usar estes exercicios:**
> 1. Leia o enunciado com atencao
> 2. Leia as dicas antes de comecar
> 3. Tente resolver sozinho
> 4. Use a Proposta de Teste para verificar se sua solucao funciona
> 5. So depois consulte a Resposta Comentada
>
> **Como testar:** Salve na pasta `~/meus-projetos/python-curso/modulo-18/` e execute com `python3 nome_do_arquivo.py`.

---

## Exercicio 1 — Entrada Segura de Inteiro — Nivel: Basico
**Conceitos:** try/except, ValueError, input

### Enunciado
Peca um numero inteiro ao usuario. Se ele digitar algo invalido, exiba uma mensagem de erro em vez de o programa parar.

### Dicas
- Use `try/except ValueError` para capturar o erro de conversao
- Coloque o `int(input(...))` dentro do bloco `try`
- A mensagem de erro vai no bloco `except`

### Proposta de Teste
- Digite `5` — Saida: `Voce digitou: 5`
- Digite `abc` — Saida: `Erro: digite um numero inteiro!`

### Resposta Comentada
```python
# Tentamos converter a entrada para inteiro
try:
    # "number" = numero
    number = int(input("Digite um numero inteiro: "))
    # Se chegou aqui, a conversao deu certo
    print(f"Voce digitou: {number}")
except ValueError:
    # Se a conversao falhou, o Python gera ValueError
    # Capturamos o erro e exibimos uma mensagem amigavel
    print("Erro: digite um numero inteiro!")
```

---

## Exercicio 2 — Divisao Segura — Nivel: Basico
**Conceitos:** try/except, ZeroDivisionError, ValueError

### Enunciado
Peca dois numeros e divida o primeiro pelo segundo. Trate tanto a entrada invalida quanto a divisao por zero.

### Dicas
- Use dois blocos `except`: um para `ValueError` e outro para `ZeroDivisionError`
- Converta as entradas com `float()` dentro do `try`
- Cada tipo de erro tem sua propria mensagem

### Proposta de Teste
- Numeros: `10` e `3` — Saida: `Resultado: 3.333...`
- Numeros: `10` e `0` — Saida: `Erro: divisao por zero!`
- Numeros: `10` e `abc` — Saida: `Erro: digite numeros validos!`

### Resposta Comentada
```python
try:
    # "numerator" = numerador, "denominator" = denominador
    numerator = float(input("Numerador: "))
    denominator = float(input("Denominador: "))
    # "result" = resultado da divisao
    result = numerator / denominator
    print(f"Resultado: {result}")
except ValueError:
    # Erro na conversao — o usuario nao digitou um numero
    print("Erro: digite numeros validos!")
except ZeroDivisionError:
    # Erro de divisao por zero
    print("Erro: divisao por zero!")
```

---

## Exercicio 3 — Entrada Repetida ate Acertar — Nivel: Basico
**Conceitos:** try/except, while, break

### Enunciado
Peca um numero ao usuario repetidamente ate que ele digite um numero valido.

### Dicas
- Use `while True` para repetir ate acertar
- Use `break` para sair do loop quando a conversao der certo
- O `except` exibe a mensagem e o loop continua automaticamente

### Proposta de Teste
- Digitar `abc`, depois `xyz`, depois `5` — Saida: `Numero aceito: 5`

### Resposta Comentada
```python
# Loop que repete ate o usuario digitar um numero valido
while True:
    try:
        # "number" = numero
        number = float(input("Digite um numero: "))
        # Se chegou aqui, a conversao deu certo — saimos do loop
        print(f"Numero aceito: {number}")
        break  # Sai do while
    except ValueError:
        # Conversao falhou — pedimos novamente
        print("Valor invalido! Tente novamente.")
```

---

## Exercicio 4 — Acesso Seguro a Lista — Nivel: Intermediario
**Conceitos:** try/except, IndexError, listas

### Enunciado
Crie uma lista com 5 frutas. Peca ao usuario um indice e exiba a fruta correspondente. Trate o caso de indice invalido.

### Dicas
- Use `except IndexError` para tratar posicoes fora da lista
- Use `except ValueError` para tratar entradas que nao sao numeros
- Lembre-se que indices validos vao de 0 a `len(lista) - 1`

### Proposta de Teste
- Indice: `2` — Saida: `Fruta: laranja`
- Indice: `10` — Saida: `Erro: posicao invalida!`
- Indice: `abc` — Saida: `Erro: digite um numero!`

### Resposta Comentada
```python
# "fruits" = frutas
fruits = ["maca", "banana", "laranja", "uva", "manga"]

try:
    # "index" = indice (posicao na lista)
    index = int(input("Digite a posicao (0 a 4): "))
    # Tentamos acessar a posicao na lista
    print(f"Fruta: {fruits[index]}")
except ValueError:
    # O usuario nao digitou um numero
    print("Erro: digite um numero!")
except IndexError:
    # A posicao nao existe na lista
    print(f"Erro: posicao invalida! Use de 0 a {len(fruits) - 1}.")
```

---

## Exercicio 5 — Calculadora Robusta — Nivel: Intermediario
**Conceitos:** try/except, funcoes, multiplos erros

### Enunciado
Crie uma funcao `safe_calculator` que peca dois numeros e uma operacao, realize o calculo e trate todos os erros possiveis.

### Dicas
- Use `if/elif` para escolher a operacao (+, -, *, /)
- Trate `ValueError` para entradas invalidas e `ZeroDivisionError` para divisao por zero
- Use `return` para encerrar a funcao se a operacao for invalida

### Proposta de Teste
- `10 + 5` — Saida: `15.0`
- `10 / 0` — Saida: `Erro: divisao por zero!`
- `abc + 5` — Saida: `Erro: valores invalidos!`

### Resposta Comentada
```python
# "safe_calculator" = calculadora segura
def safe_calculator():
    try:
        # Pedimos os dados
        # "num_a" = primeiro numero, "num_b" = segundo numero
        num_a = float(input("Primeiro numero: "))
        num_b = float(input("Segundo numero: "))
        # "op" = operacao
        op = input("Operacao (+, -, *, /): ")

        # Realizamos o calculo
        if op == "+":
            result = num_a + num_b
        elif op == "-":
            result = num_a - num_b
        elif op == "*":
            result = num_a * num_b
        elif op == "/":
            result = num_a / num_b
        else:
            print("Operacao invalida!")
            return  # Encerra a funcao

        print(f"Resultado: {result}")

    except ValueError:
        # Erro na conversao dos numeros
        print("Erro: valores invalidos! Digite apenas numeros.")
    except ZeroDivisionError:
        # Erro de divisao por zero
        print("Erro: divisao por zero!")

# Chamamos a calculadora
safe_calculator()
```

---

## Exercicio 6 — try/except/else — Nivel: Intermediario
**Conceitos:** try/except/else

### Enunciado
Peca a idade do usuario. Se for valida, exiba a classificacao (menor/maior de idade) no bloco else. Se for invalida, exiba erro no except.

### Dicas
- O bloco `else` executa apenas se nao houve erro no `try`
- Coloque a logica de classificacao no `else`, nao no `try`
- Use `int()` para converter a entrada

### Proposta de Teste
- Idade: `25` — Saida: `Maior de idade`
- Idade: `abc` — Saida: `Erro: digite um numero!`

### Resposta Comentada
```python
try:
    # "age" = idade
    age = int(input("Sua idade: "))
except ValueError:
    # Erro na conversao
    print("Erro: digite um numero inteiro!")
else:
    # Executa APENAS se nao houve erro no try
    # Aqui sabemos que age e um int valido
    if age >= 18:
        print("Maior de idade.")
    else:
        print("Menor de idade.")
```

---

## Exercicio 7 — try/except/finally — Nivel: Intermediario
**Conceitos:** try/except/finally

### Enunciado
Crie um programa que peca um numero e calcule 100 dividido por ele. Use finally para exibir "Operacao finalizada" independente do resultado.

### Dicas
- O bloco `finally` executa sempre, com ou sem erro
- Coloque a mensagem "Operacao finalizada" no `finally`
- Trate tanto `ValueError` quanto `ZeroDivisionError`

### Proposta de Teste
- Numero: `5` — Saida: `Resultado: 20.0` e `Operacao finalizada`
- Numero: `0` — Saida: `Erro: divisao por zero!` e `Operacao finalizada`

### Resposta Comentada
```python
try:
    # "number" = numero
    number = float(input("Digite um numero: "))
    # "result" = resultado
    result = 100 / number
    print(f"Resultado: {result}")
except ValueError:
    print("Erro: digite um numero valido!")
except ZeroDivisionError:
    print("Erro: divisao por zero!")
finally:
    # Este bloco SEMPRE executa, com ou sem erro
    # E como limpar a cozinha — acontece independente do resultado
    print("Operacao finalizada.")
```

---

## Exercicio 8 — Validacao de Cadastro — Nivel: Avancado
**Conceitos:** try/except, funcoes, validacao completa

### Enunciado
Crie uma funcao `register_user` que peca nome, idade e email. Valide cada campo: nome nao pode ser vazio, idade deve ser um numero entre 0 e 150, email deve conter @. Trate os erros e so exiba o cadastro se tudo estiver valido.

### Dicas
- Use `raise ValueError("mensagem")` para gerar erros personalizados
- Use `strip()` para remover espacos do nome e email
- Use o bloco `else` para exibir o cadastro apenas se tudo deu certo

### Proposta de Teste
- Nome: `Ana`, Idade: `25`, Email: `ana@email.com` — Cadastro exibido
- Nome: ``, Idade: `25`, Email: `ana@email.com` — Erro: nome vazio
- Nome: `Ana`, Idade: `abc`, Email: `ana@email.com` — Erro: idade invalida

### Resposta Comentada
```python
# "register_user" = registrar usuario
def register_user():
    try:
        # Pedimos o nome
        # "name" = nome
        name = input("Nome: ").strip()
        if name == "":
            # Se o nome estiver vazio, geramos um erro manualmente
            # raise = levantar/gerar uma excecao
            raise ValueError("Nome nao pode ser vazio!")

        # Pedimos a idade
        # "age" = idade
        age = int(input("Idade: "))
        if age < 0 or age > 150:
            raise ValueError("Idade deve ser entre 0 e 150!")

        # Pedimos o email
        # "email" = email
        email = input("Email: ").strip()
        if "@" not in email:
            raise ValueError("Email deve conter @!")

    except ValueError as error:
        # "error" = o erro capturado — contem a mensagem
        # "as" permite acessar a mensagem do erro
        print(f"Erro no cadastro: {error}")
    else:
        # Tudo valido — exibimos o cadastro
        print("\n=== Cadastro Realizado ===")
        print(f"Nome: {name}")
        print(f"Idade: {age}")
        print(f"Email: {email}")

# Chamamos a funcao
register_user()
```

---

## Exercicio 9 — Menu com Tratamento de Erros — Nivel: Avancado
**Conceitos:** try/except, while, funcoes, logica completa

### Enunciado
Crie um menu com opcoes (1-Somar, 2-Subtrair, 3-Multiplicar, 4-Dividir, 0-Sair). O menu deve se repetir ate o usuario escolher sair. Trate todos os erros possiveis.

### Dicas
- Use `while True` com `break` para sair quando a opcao for 0
- Use `continue` para voltar ao menu quando a opcao for invalida
- Trate `ValueError` e `ZeroDivisionError` dentro do loop

### Proposta de Teste
- Opcao: `1`, Numeros: `10` e `5` — Saida: `15.0`
- Opcao: `4`, Numeros: `10` e `0` — Saida: `Erro: divisao por zero!`
- Opcao: `abc` — Saida: `Erro: digite um numero!`
- Opcao: `0` — Saida: `Ate logo!`

### Resposta Comentada
```python
# "calculator_menu" = menu da calculadora
def calculator_menu():
    while True:
        print("\n=== Calculadora ===")
        print("1 - Somar")
        print("2 - Subtrair")
        print("3 - Multiplicar")
        print("4 - Dividir")
        print("0 - Sair")

        try:
            # "option" = opcao
            option = int(input("Opcao: "))

            if option == 0:
                print("Ate logo!")
                break  # Sai do while

            if option < 1 or option > 4:
                print("Opcao invalida! Escolha de 0 a 4.")
                continue  # Volta ao inicio do while

            # Pedimos os numeros
            # "num_a" = primeiro numero, "num_b" = segundo numero
            num_a = float(input("Primeiro numero: "))
            num_b = float(input("Segundo numero: "))

            # Realizamos a operacao
            if option == 1:
                print(f"Resultado: {num_a + num_b}")
            elif option == 2:
                print(f"Resultado: {num_a - num_b}")
            elif option == 3:
                print(f"Resultado: {num_a * num_b}")
            elif option == 4:
                print(f"Resultado: {num_a / num_b}")

        except ValueError:
            print("Erro: digite apenas numeros!")
        except ZeroDivisionError:
            print("Erro: divisao por zero!")

# Chamamos o menu
calculator_menu()
```

---

## Exercicio 10 — Entrada Segura Generica — Nivel: Avancado
**Conceitos:** try/except, funcoes com parametros, reutilizacao

### Enunciado
Crie uma funcao generica `safe_input` que receba uma mensagem e um tipo (int ou float) e retorne o valor convertido. Se a conversao falhar, peca novamente ate o usuario digitar algo valido.

### Dicas
- A funcao recebe o tipo como parametro (ex: `int` ou `float`)
- Use `data_type(input(...))` para converter dinamicamente
- Use `while True` com `try/except` para repetir ate acertar

### Proposta de Teste
- `safe_input("Idade: ", int)` com entrada `abc`, depois `25` — Retorno: `25`
- `safe_input("Preco: ", float)` com entrada `xyz`, depois `9.99` — Retorno: `9.99`

### Resposta Comentada
```python
# "safe_input" = entrada segura
# "message" = mensagem a exibir
# "data_type" = tipo de dado esperado (int ou float)
def safe_input(message, data_type):
    while True:
        try:
            # Tentamos converter a entrada para o tipo especificado
            # data_type() chama int() ou float() dependendo do que foi passado
            # "value" = valor convertido
            value = data_type(input(message))
            return value  # Conversao deu certo — retornamos o valor
        except ValueError:
            # Conversao falhou — pedimos novamente
            # "type_name" = nome do tipo (para a mensagem de erro)
            type_name = "inteiro" if data_type == int else "decimal"
            print(f"Valor invalido! Digite um numero {type_name}.")

# Usando a funcao
# "age" = idade — pede int
age = safe_input("Sua idade: ", int)
print(f"Idade: {age}")

# "price" = preco — pede float
price = safe_input("Preco do produto: R$ ", float)
print(f"Preco: R$ {price}")
```

---

[<- Voltar ao Modulo 18](18-tratamento-erros.md) | [Glossario](00-glossario.md)
