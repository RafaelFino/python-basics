# 12 — Condicionais: if, elif e else

[<- Anterior: Operadores](11-operadores.md) | [Glossario](00-glossario.md) | [Proximo: Seletores match/case ->](13-seletores-match-case.md)

---

## Introducao

Ate agora, todos os nossos programas executavam as instrucoes de cima para baixo, uma apos a outra, sem desvios. Mas na vida real, tomamos decisoes o tempo todo: "se estiver chovendo, levo guarda-chuva; senao, levo oculos de sol". Programas tambem precisam tomar decisoes.

Neste modulo, voce vai aprender a fazer seus programas **escolherem caminhos diferentes** dependendo de condicoes. Isso e feito com as estruturas `if` (se), `elif` (senao se) e `else` (senao).

Pense nas condicionais como uma encruzilhada: o programa chega a um ponto onde precisa decidir qual caminho seguir, e a decisao depende de uma condicao ser verdadeira ou falsa.

> **Dica:** Este modulo depende dos modulos 10 (indentacao) e 11 (operadores). Se nao se sentir seguro nesses temas, revise-os antes de continuar.

---

## Como Executar os Exemplos Deste Modulo

1. Copie o codigo e cole em um novo arquivo no VSCode
2. Salve na pasta `~/meus-projetos/python-curso/modulo-12/`
3. No terminal: `cd ~/meus-projetos/python-curso/modulo-12`
4. Execute: `python3 nome_do_arquivo.py`

---

## if — "Se" (Uma Condicao Simples)

A estrutura `if` executa um bloco de codigo **apenas quando a condicao e verdadeira**. Se a condicao for falsa, o bloco e ignorado e o programa continua.

Pense assim: "Se estiver chovendo, leve o guarda-chuva." Se nao estiver chovendo, voce simplesmente ignora essa instrucao e segue em frente.

```python
# Exemplo basico de if
# "temperature" = temperatura
temperature = 35

# if verifica se a condicao e verdadeira
# Se temperature > 30 for True, o bloco indentado executa
# Se for False, o bloco e ignorado
if temperature > 30:
    # Este bloco so executa se a temperatura for maior que 30
    print("Esta muito quente hoje!")
    print("Beba bastante agua.")

# Esta linha esta fora do if — executa sempre
print("Tenha um bom dia!")
```

**Saida esperada (com temperature = 35):**
```
Esta muito quente hoje!
Beba bastante agua.
Tenha um bom dia!
```

**Se mudarmos para temperature = 20:**
```
Tenha um bom dia!
```

> **Nota:** Lembre-se do modulo 10: o bloco do `if` e definido pela indentacao. Todas as linhas indentadas apos o `if:` pertencem ao bloco. Quando a indentacao volta ao nivel anterior, o bloco terminou.

### Anatomia do if

```
if condicao:          <-- a condicao e uma expressao que resulta em True ou False
    instrucao_1       <-- bloco indentado: executa apenas se a condicao for True
    instrucao_2       <-- ainda dentro do bloco
codigo_fora           <-- fora do bloco: executa sempre
```

A condicao pode ser qualquer expressao que resulte em `True` ou `False`:
- Comparacoes: `age >= 18`, `name == "Maria"`, `price < 100`
- Variaveis booleanas: `is_active`, `has_discount`
- Combinacoes com operadores logicos: `age >= 18 and has_id`

---

## if/else — "Se... Senao" (Dois Caminhos)

Quando voce precisa de dois caminhos — um para quando a condicao e verdadeira e outro para quando e falsa — use `if/else`:

Pense assim: "Se estiver chovendo, leve guarda-chuva; **senao**, leve oculos de sol."

```python
# if/else: dois caminhos possiveis
# "age" = idade
age = int(input("Digite sua idade: "))

# Se a idade for >= 18, executa o primeiro bloco
# Senao (else), executa o segundo bloco
if age >= 18:
    # Bloco do if — executa quando a condicao e verdadeira
    print("Voce e maior de idade.")
    print("Pode tirar carteira de motorista.")
else:
    # Bloco do else — executa quando a condicao e falsa
    print("Voce e menor de idade.")
    print("Ainda nao pode tirar carteira.")

# Fora dos blocos — executa sempre
print("Obrigado por usar o sistema!")
```

**Saida esperada (se digitar 20):**
```
Voce e maior de idade.
Pode tirar carteira de motorista.
Obrigado por usar o sistema!
```

**Saida esperada (se digitar 15):**
```
Voce e menor de idade.
Ainda nao pode tirar carteira.
Obrigado por usar o sistema!
```

> **Nota:** O `else` nao tem condicao — ele e o "caso contrario". Tudo que nao entrou no `if` cai no `else`.

---

## if/elif/else — "Se... Senao Se... Senao" (Multiplos Caminhos)

Quando voce tem mais de duas opcoes, use `elif` (abreviacao de "else if", que significa "senao se") para criar caminhos adicionais:

Pense assim: "Se a nota for >= 9, conceito A; senao se for >= 7, conceito B; senao se for >= 5, conceito C; senao, conceito D."

```python
# if/elif/else: multiplos caminhos
# "grade" = nota
grade = float(input("Digite sua nota (0 a 10): "))

# O Python verifica cada condicao de cima para baixo
# Quando encontra a primeira verdadeira, executa o bloco e pula o resto
if grade >= 9:
    # Executa se nota >= 9
    # "concept" = conceito
    concept = "A"
    print("Excelente!")
elif grade >= 7:
    # Executa se nota >= 7 (e < 9, porque a condicao anterior ja foi verificada)
    concept = "B"
    print("Bom trabalho!")
elif grade >= 5:
    # Executa se nota >= 5 (e < 7)
    concept = "C"
    print("Pode melhorar.")
else:
    # Executa se nenhuma condicao anterior for verdadeira (nota < 5)
    concept = "D"
    print("Precisa estudar mais.")

# Fora dos blocos — executa sempre
print(f"Sua nota: {grade} — Conceito: {concept}")
```

**Saida esperada (se digitar 8.5):**
```
Bom trabalho!
Sua nota: 8.5 — Conceito: B
```

### Como o Python avalia as condicoes

O Python verifica as condicoes **de cima para baixo**. Quando encontra a primeira condicao verdadeira, executa o bloco correspondente e **pula todas as outras**. Se nenhuma condicao for verdadeira, executa o `else` (se existir).

E como um funil: o valor "cai" pela primeira abertura que encontra.

---

## Condicionais Aninhadas — if Dentro de if

Voce pode colocar um `if` dentro de outro `if`. Isso se chama "aninhamento" e e util quando voce precisa verificar uma condicao dentro de outra:

```python
# Condicionais aninhadas: if dentro de if
# "has_ticket" = tem ingresso, "age" = idade
has_ticket = input("Tem ingresso? (sim/nao): ")
age = int(input("Sua idade: "))

# Primeiro verificamos se tem ingresso
if has_ticket == "sim":
    # Dentro do primeiro if: verificamos a idade
    print("Ingresso verificado.")

    if age >= 18:
        # Dentro do segundo if (8 espacos de indentacao)
        print("Entrada permitida. Boa diversao!")
    else:
        # Dentro do else do segundo if
        print("Entrada permitida com acompanhante adulto.")
else:
    # Bloco do else do primeiro if
    print("Voce precisa de um ingresso para entrar.")

print("Fim da verificacao.")
```

> **Atencao:** Condicionais aninhadas podem ficar confusas se tiverem muitos niveis. Tente limitar a dois niveis de aninhamento. Se precisar de mais, considere reorganizar a logica.

---

## Condicoes Compostas — Combinando com and, or, not

Em vez de aninhar varios `if`, voce pode combinar condicoes usando os operadores logicos que aprendeu no modulo 11:

```python
# Condicoes compostas com and e or
# "age" = idade, "has_id" = tem documento
age = int(input("Idade: "))
has_id_input = input("Tem documento? (sim/nao): ")
has_id = has_id_input == "sim"

# Usando and: ambas as condicoes precisam ser verdadeiras
if age >= 18 and has_id:
    print("Acesso liberado.")
else:
    print("Acesso negado.")

    # Explicamos o motivo usando not
    if not (age >= 18):
        # not inverte: se NAO tem 18+, e menor de idade
        print("Motivo: menor de idade.")
    if not has_id:
        # not inverte: se NAO tem documento
        print("Motivo: sem documento.")
```

```python
# Usando or: pelo menos uma condicao precisa ser verdadeira
# "payment_method" = forma de pagamento
payment_method = input("Forma de pagamento (dinheiro/cartao/pix): ")

if payment_method == "dinheiro" or payment_method == "cartao" or payment_method == "pix":
    print("Pagamento aceito!")
else:
    print("Forma de pagamento nao aceita.")
```

---

## Exemplos Praticos

### Exemplo 1: Classificacao de idade

```python
# Classificando uma pessoa pela faixa etaria
# "age" = idade
age = int(input("Digite a idade: "))

if age < 0:
    # Idade negativa nao faz sentido
    print("Idade invalida!")
elif age <= 12:
    # 0 a 12 anos
    # "category" = categoria
    category = "Crianca"
elif age <= 17:
    # 13 a 17 anos
    category = "Adolescente"
elif age <= 59:
    # 18 a 59 anos
    category = "Adulto"
else:
    # 60 anos ou mais
    category = "Idoso"

if age >= 0:
    print(f"Idade: {age} — Categoria: {category}")
```

### Exemplo 2: Calculadora com operacao escolhida

```python
# Calculadora que pede a operacao ao usuario
# "number_a" = primeiro numero, "number_b" = segundo numero
number_a = float(input("Primeiro numero: "))
number_b = float(input("Segundo numero: "))

# "operation" = operacao
operation = input("Operacao (+, -, *, /): ")

if operation == "+":
    # "result" = resultado
    result = number_a + number_b
    print(f"{number_a} + {number_b} = {result}")
elif operation == "-":
    result = number_a - number_b
    print(f"{number_a} - {number_b} = {result}")
elif operation == "*":
    result = number_a * number_b
    print(f"{number_a} * {number_b} = {result}")
elif operation == "/":
    # Verificamos se o divisor nao e zero antes de dividir
    if number_b != 0:
        result = number_a / number_b
        print(f"{number_a} / {number_b} = {result}")
    else:
        print("Erro: nao e possivel dividir por zero!")
else:
    print("Operacao invalida! Use +, -, * ou /")
```

---

## Resumo

| Estrutura | Quando usar | Exemplo |
|-----------|-------------|---------|
| `if` | Uma condicao, um caminho | `if age >= 18:` |
| `if/else` | Dois caminhos (sim ou nao) | `if age >= 18: ... else: ...` |
| `if/elif/else` | Multiplos caminhos | `if grade >= 9: ... elif grade >= 7: ...` |
| Aninhado | Condicao dentro de condicao | `if has_ticket: if age >= 18:` |
| Composto | Combinar condicoes | `if age >= 18 and has_id:` |

---

## Para Saber Mais

- [W3Schools — Python If...Else](https://www.w3schools.com/python/python_conditions.asp) — _Condicionais em Python_
- [W3Schools — Python Operators](https://www.w3schools.com/python/python_operators.asp) — _Operadores de comparacao e logicos_
- [Documentacao Python — Controle de Fluxo](https://docs.python.org/pt-br/3/tutorial/controlflow.html) — _Referencia oficial_

---

## Perguntas Frequentes (FAQ)

**P: Qual a diferenca entre if e elif?**
R: `if` inicia uma nova verificacao de condicao. `elif` (else if = senao se) e uma condicao alternativa que so e verificada se o `if` anterior foi falso. Pense no `elif` como "se a primeira opcao nao serviu, tente esta".

**P: Posso ter if sem else?**
R: Sim! O `else` e opcional. Se voce so precisa fazer algo quando a condicao e verdadeira e nada quando e falsa, use apenas `if` sem `else`.

**P: Posso ter varios elif?**
R: Sim, quantos precisar! Voce pode ter `if`, seguido de quantos `elif` quiser, e opcionalmente um `else` no final. O Python verifica cada condicao de cima para baixo.

**P: O else e obrigatorio?**
R: Nao. O `else` e opcional. Use-o quando precisar de um "caso contrario" — algo que acontece quando nenhuma condicao anterior foi verdadeira.

**P: O que acontece se duas condicoes forem verdadeiras ao mesmo tempo?**
R: O Python executa apenas o bloco da **primeira** condicao verdadeira que encontrar (de cima para baixo) e pula todas as outras. Por isso a ordem das condicoes importa.

**P: Posso usar if sem elif, direto com else?**
R: Sim! `if/else` (sem elif) e a forma mais simples: dois caminhos, um para verdadeiro e outro para falso.

**P: O que sao "condicionais aninhadas"?**
R: E quando voce coloca um `if` dentro de outro `if`. O if interno so e verificado se o if externo for verdadeiro. Use com moderacao — muitos niveis de aninhamento tornam o codigo dificil de ler.

**P: Quando devo usar aninhamento vs condicoes compostas (and/or)?**
R: Se as condicoes sao independentes (verificar A e depois verificar B dentro de A), use aninhamento. Se as condicoes precisam ser verdadeiras ao mesmo tempo, use `and`. Na duvida, prefira `and/or` — e mais legivel.

**P: Posso comparar strings com if?**
R: Sim! `if name == "Maria":` verifica se o nome e exatamente "Maria". Cuidado: a comparacao diferencia maiusculas de minusculas. "Maria" e "maria" sao diferentes.

**P: Como ignoro maiusculas/minusculas na comparacao?**
R: Converta para minusculas antes de comparar: `if name.lower() == "maria":`. Assim, "Maria", "MARIA" e "maria" sao todos aceitos.

**P: O que e o operador ternario?**
R: E uma forma de escrever um if/else em uma unica linha: `resultado = "par" if numero % 2 == 0 else "impar"`. E util para expressoes simples, mas para iniciantes, o if/else normal e mais claro.

**P: Posso colocar if dentro de elif?**
R: Sim, voce pode aninhar condicionais em qualquer nivel. Mas tente manter no maximo 2-3 niveis para nao perder a legibilidade.

**P: O que acontece se eu esquecer os dois pontos (:) depois do if?**
R: O Python mostra um `SyntaxError`. Os dois pontos sao obrigatorios — eles indicam que um bloco indentado vem a seguir.

**P: Posso ter um bloco vazio no if?**
R: Sim, usando `pass`. Se voce ainda nao sabe o que colocar no bloco, use `if condicao: pass` como placeholder. Isso evita o `IndentationError`.

**P: O que e "curto-circuito" em condicoes?**
R: Quando o Python usa `and`, se a primeira condicao for `False`, ele nem verifica a segunda (porque o resultado ja sera `False`). Com `or`, se a primeira for `True`, ele nem verifica a segunda. Isso e chamado de avaliacao em curto-circuito.

**P: Posso usar numeros como condicao no if?**
R: Sim! O Python converte automaticamente para booleano. `if 0:` nunca executa (0 e False). `if 1:` ou `if 42:` sempre executa (qualquer numero diferente de zero e True). Mas para clareza, prefira condicoes explicitas.

**P: Posso usar strings como condicao?**
R: Sim! String vazia `""` e `False`, qualquer string com conteudo e `True`. `if nome:` verifica se o nome nao esta vazio. Mas `if nome != "":` e mais explicito para iniciantes.

**P: Qual a diferenca entre `=` e `==` dentro do if?**
R: `=` e atribuicao (guarda valor) e NAO pode ser usado dentro do if. `==` e comparacao (verifica igualdade) e e o que voce usa no if. Escrever `if age = 18:` gera erro — o correto e `if age == 18:`.

**P: Posso ter codigo antes e depois do if na mesma linha?**
R: Nao antes, mas o bloco pode estar na mesma linha: `if True: print("ola")`. Porem, para legibilidade, prefira colocar o bloco na linha seguinte com indentacao.

**P: E normal errar a logica das condicoes no inicio?**
R: Muito normal! Condicoes sao um dos pontos onde mais se erra no inicio. Teste seu programa com diferentes valores para garantir que todos os caminhos funcionam. Use a proposta de teste de cada exercicio para verificar.

---

## Exercicios de Fixacao

Os exercicios deste modulo estao em um arquivo separado para facilitar a consulta. Este e um modulo complexo — os exercicios sao mais numerosos e progressivos.

**[Acessar Exercicios do Modulo 12](12-condicionais-exercicios.md)**

---

[<- Anterior: Operadores](11-operadores.md) | [Glossario](00-glossario.md) | [Proximo: Seletores match/case ->](13-seletores-match-case.md)
