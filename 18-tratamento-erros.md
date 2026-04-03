# 18 — Tratamento de Erros: try, except, finally

[<- Anterior: Debugging](17-debugging.md) | [Glossario](00-glossario.md) | [Proximo: Estruturas de Dados ->](19-estruturas-dados.md)

---

## Introducao

No modulo anterior, voce aprendeu a identificar erros. Agora vai aprender a **tratar** esses erros para que seu programa nao pare de funcionar quando algo inesperado acontece.

Imagine que voce esta cozinhando e percebe que falta um ingrediente. Voce tem duas opcoes: desistir da receita (o programa para com erro) ou improvisar com o que tem (tratar o erro e continuar). O tratamento de erros e a segunda opcao — voce prepara o programa para lidar com situacoes inesperadas.

Em Python, usamos as estruturas `try`, `except`, `else` e `finally` para tratar erros em tempo de execucao (chamados de **excecoes**).

> **Dica:** Consulte o [Glossario](00-glossario.md) sempre que encontrar um termo desconhecido.

---

## Como Executar os Exemplos Deste Modulo

1. Copie o codigo e cole em um novo arquivo no VSCode
2. Salve na pasta `~/meus-projetos/python-curso/modulo-18/`
3. No terminal: `cd ~/meus-projetos/python-curso/modulo-18`
4. Execute: `python3 nome_do_arquivo.py`

---

## Erros de Sintaxe vs Excecoes

Existem dois tipos de erros em Python:

- **Erros de sintaxe** (SyntaxError): o Python detecta antes de executar. Sao erros de escrita — como esquecer um parentese. Nao podem ser tratados com try/except.

- **Excecoes** (erros em tempo de execucao): acontecem durante a execucao do programa. Sao situacoes inesperadas — como o usuario digitar texto quando o programa espera um numero. Podem ser tratados com try/except.

---

## A Estrutura try/except

A forma mais basica de tratar erros:

```python
# Sem tratamento — o programa para se o usuario digitar texto
# number = int(input("Digite um numero: "))  # ValueError se digitar "abc"

# Com tratamento — o programa nao para
try:
    # O bloco try contem o codigo que PODE gerar um erro
    # "number" = numero
    number = int(input("Digite um numero: "))
    print(f"Voce digitou: {number}")
except ValueError:
    # O bloco except executa APENAS se ocorrer o erro especificado
    # ValueError acontece quando a conversao falha
    print("Erro: voce nao digitou um numero valido!")

# O programa continua normalmente apos o try/except
print("Programa encerrado.")
```

**Se o usuario digitar "5":**
```
Digite um numero: 5
Voce digitou: 5
Programa encerrado.
```

**Se o usuario digitar "abc":**
```
Digite um numero: abc
Erro: voce nao digitou um numero valido!
Programa encerrado.
```

> **Nota:** O programa nao para quando o erro acontece — ele executa o bloco `except` e continua normalmente. Sem o try/except, o programa pararia com uma mensagem de erro.

### Anatomia do try/except

```
try:
    codigo_que_pode_dar_erro    <-- tenta executar este codigo
except TipoDoErro:
    codigo_de_tratamento        <-- executa se o erro especificado ocorrer
```

---

## Tratando Diferentes Tipos de Erro

Voce pode ter varios blocos `except` para tratar diferentes tipos de erro:

```python
# Tratando diferentes tipos de erro
try:
    # "numerator" = numerador, "denominator" = denominador
    numerator = int(input("Numerador: "))
    denominator = int(input("Denominador: "))
    # "result" = resultado
    result = numerator / denominator
    print(f"Resultado: {result}")
except ValueError:
    # Erro de conversao — o usuario nao digitou um numero
    print("Erro: digite apenas numeros!")
except ZeroDivisionError:
    # Erro de divisao por zero
    print("Erro: nao e possivel dividir por zero!")
```

---

## O Bloco else — Quando Nao Ha Erro

O bloco `else` executa **apenas quando nenhum erro ocorreu** no bloco `try`:

```python
try:
    # "age" = idade
    age = int(input("Sua idade: "))
except ValueError:
    print("Erro: digite um numero inteiro!")
else:
    # Este bloco executa APENAS se nao houve erro no try
    # E um bom lugar para codigo que depende do sucesso do try
    print(f"Voce tem {age} anos.")
    if age >= 18:
        print("Voce e maior de idade.")
```

---

## O Bloco finally — Sempre Executa

O bloco `finally` executa **sempre**, independente de ter ocorrido erro ou nao. E util para acoes de "limpeza" que precisam acontecer de qualquer forma:

```python
try:
    # "number" = numero
    number = int(input("Digite um numero: "))
    # "result" = resultado
    result = 100 / number
    print(f"Resultado: {result}")
except ValueError:
    print("Erro: digite um numero valido!")
except ZeroDivisionError:
    print("Erro: nao divida por zero!")
finally:
    # Este bloco SEMPRE executa, com ou sem erro
    # E como a etapa de "limpar a cozinha" — acontece independente
    # de a receita ter dado certo ou nao
    print("Operacao finalizada.")
```

**Se digitar "5":**
```
Resultado: 20.0
Operacao finalizada.
```

**Se digitar "0":**
```
Erro: nao divida por zero!
Operacao finalizada.
```

**Se digitar "abc":**
```
Erro: digite um numero valido!
Operacao finalizada.
```

---

## Estrutura Completa: try/except/else/finally

```python
try:
    # Codigo que pode gerar erro
    # "value" = valor
    value = int(input("Numero: "))
    result = 100 / value
except ValueError:
    # Executa se ValueError ocorrer
    print("Nao e um numero!")
except ZeroDivisionError:
    # Executa se ZeroDivisionError ocorrer
    print("Nao divida por zero!")
else:
    # Executa APENAS se nenhum erro ocorreu
    print(f"Resultado: {result}")
finally:
    # Executa SEMPRE (com ou sem erro)
    print("Fim da operacao.")
```

### Ordem de execucao

| Situacao | try | except | else | finally |
|----------|-----|--------|------|---------|
| Sem erro | Executa | Pula | Executa | Executa |
| Com erro tratado | Para no erro | Executa | Pula | Executa |
| Com erro nao tratado | Para no erro | Pula | Pula | Executa |

---

## Exemplo Pratico: Entrada Segura de Dados

Um padrao muito util e pedir dados ao usuario repetidamente ate que ele digite algo valido:

```python
# Funcao que pede um numero inteiro de forma segura
# "safe_int_input" = entrada segura de inteiro
# "message" = mensagem a exibir
def safe_int_input(message):
    while True:
        try:
            # Tentamos converter a entrada para int
            # "value" = valor
            value = int(input(message))
            # Se chegou aqui, a conversao deu certo — retornamos o valor
            return value
        except ValueError:
            # Se deu erro, avisamos e o while repete (pede novamente)
            print("Valor invalido! Digite um numero inteiro.")

# Usando a funcao — o programa so continua quando o usuario digitar um numero valido
# "age" = idade
age = safe_int_input("Sua idade: ")
print(f"Idade registrada: {age}")
```

---

## Resumo

| Estrutura | Quando executa |
|-----------|---------------|
| `try:` | Sempre tenta executar |
| `except TipoErro:` | Quando o erro especificado ocorre no try |
| `else:` | Quando nenhum erro ocorre no try |
| `finally:` | Sempre, com ou sem erro |

---

## Para Saber Mais

- [W3Schools — Python Try Except](https://www.w3schools.com/python/python_try_except.asp) — _Tratamento de erros_
- [Documentacao Python — Erros e Excecoes](https://docs.python.org/pt-br/3/tutorial/errors.html) — _Referencia oficial_

---

## Perguntas Frequentes (FAQ)

**P: O que e uma excecao?**
R: E um erro que acontece durante a execucao do programa (nao durante a escrita). Quando uma excecao ocorre e nao e tratada, o programa para. Com try/except, voce pode capturar a excecao e decidir o que fazer.

**P: Qual a diferenca entre erro de sintaxe e excecao?**
R: Erro de sintaxe e detectado antes da execucao — o Python nem consegue rodar o programa. Excecao acontece durante a execucao — o programa comeca a rodar e para quando encontra o problema. So excecoes podem ser tratadas com try/except.

**P: Posso tratar qualquer tipo de erro com try/except?**
R: Quase todos os erros de execucao (excecoes) podem ser tratados. Erros de sintaxe (SyntaxError) nao podem ser tratados com try/except porque o programa nem chega a executar.

**P: O que acontece se eu nao especificar o tipo de erro no except?**
R: `except:` sem tipo captura QUALQUER excecao. Isso funciona, mas nao e recomendado porque pode esconder erros que voce nao esperava. Sempre especifique o tipo de erro quando possivel.

**P: Posso ter varios except?**
R: Sim! Voce pode ter quantos blocos except precisar, cada um tratando um tipo diferente de erro. O Python verifica de cima para baixo e executa o primeiro que corresponder.

**P: O else e obrigatorio?**
R: Nao, e opcional. Use quando tiver codigo que so deve executar se o try foi bem-sucedido. Na pratica, muitos programadores colocam esse codigo dentro do try mesmo.

**P: O finally e obrigatorio?**
R: Nao, e opcional. Use quando precisar garantir que algo aconteca independente de erros — como fechar um arquivo ou uma conexao com banco de dados.

**P: Posso ter try dentro de try?**
R: Sim, mas tente evitar. Try/except aninhados tornam o codigo confuso. Prefira tratar cada erro no nivel adequado.

**P: O que e "capturar" uma excecao?**
R: E o ato de interceptar um erro com except antes que ele pare o programa. Quando voce "captura" uma excecao, voce decide o que fazer com ela em vez de deixar o programa parar.

**P: Posso acessar a mensagem de erro dentro do except?**
R: Sim! Use `except ValueError as e:` — a variavel `e` contera a mensagem de erro. Exemplo: `print(f"Erro: {e}")`.

**P: O que e "raise"?**
R: E uma palavra-chave que permite voce mesmo gerar uma excecao. Exemplo: `raise ValueError("Preco invalido")`. Util para validacao de dados. E um conceito mais avancado.

**P: Devo usar try/except em todo o codigo?**
R: Nao! Use apenas onde erros sao esperados — como entrada de dados do usuario, operacoes com arquivos ou divisoes. Usar try/except em excesso torna o codigo dificil de ler.

**P: O que e "tratar" um erro?**
R: E decidir o que fazer quando o erro acontece, em vez de deixar o programa parar. Pode ser: exibir uma mensagem amigavel, pedir os dados novamente, usar um valor padrao, ou registrar o erro para analise.

**P: Posso tratar ValueError e TypeError no mesmo except?**
R: Sim! Use parenteses: `except (ValueError, TypeError):`. Isso captura ambos os tipos de erro no mesmo bloco.

**P: O que acontece se o erro nao for do tipo especificado no except?**
R: O except nao captura e o erro "sobe" — o programa para com a mensagem de erro normal. Por isso e importante especificar os tipos corretos.

**P: Posso usar try/except com loops?**
R: Sim, e muito comum! O padrao de "pedir dados ate serem validos" usa try/except dentro de while, como no exemplo de entrada segura deste modulo.

**P: O que e "Exception"?**
R: E a classe base de todas as excecoes em Python. `except Exception:` captura quase todos os erros. E mais seguro que `except:` sozinho, mas ainda e generico demais para a maioria dos casos.

**P: Posso criar meus proprios tipos de excecao?**
R: Sim, mas e um conceito avancado que esta fora do escopo deste curso. Por enquanto, use os tipos de excecao que o Python ja oferece.

**P: O que e "propagacao de excecao"?**
R: Quando um erro nao e tratado em uma funcao, ele "sobe" para quem chamou a funcao. Se ninguem tratar, o programa para. E como uma bola quente sendo passada — se ninguem segurar, cai no chao.

**P: E normal ter dificuldade com try/except no inicio?**
R: Sim! Saber quando e onde usar try/except vem com experiencia. Comece tratando os erros mais obvios (como entrada de dados) e va expandindo conforme se sentir confortavel. Com pratica, tratar erros se torna natural.

---

## Exercicios de Fixacao

Os exercicios deste modulo estao em um arquivo separado:

**[Acessar Exercicios do Modulo 18](18-tratamento-erros-exercicios.md)**

---

[<- Anterior: Debugging](17-debugging.md) | [Glossario](00-glossario.md) | [Proximo: Estruturas de Dados ->](19-estruturas-dados.md)
