# 10 — Indentacao e Escopo de Blocos de Codigo

[<- Anterior: Manipulacao de Strings](09-manipulacao-strings.md) | [Glossario](00-glossario.md) | [Proximo: Operadores ->](11-operadores.md)

---

## Introducao

Este modulo trata de um assunto que pode parecer simples, mas e absolutamente fundamental em Python: a **indentacao**. Em muitas linguagens de programacao, a indentacao e apenas uma questao estetica — o codigo funciona com ou sem ela. Em Python, a indentacao **faz parte da linguagem**. Se voce indentar errado, o programa nao funciona.

Pense na indentacao como a organizacao de itens dentro de caixas. Quando voce coloca itens dentro de uma caixa, eles ficam "recuados" em relacao a caixa. Em Python, linhas de codigo que pertencem a um bloco (como o corpo de um `if`, `for` ou funcao) precisam estar recuadas para dentro, mostrando que fazem parte daquele bloco.

Este modulo prepara voce para os proximos modulos (condicionais, loops e funcoes), que dependem diretamente da indentacao para funcionar.

> **Dica:** Consulte o [Glossario](00-glossario.md) sempre que encontrar um termo desconhecido.

---

## Como Executar os Exemplos Deste Modulo

1. Copie o codigo e cole em um novo arquivo no VSCode
2. Salve com extensao `.py` na pasta `~/meus-projetos/python-curso/modulo-10/`
3. No terminal: `cd ~/meus-projetos/python-curso/modulo-10`
4. Execute: `python3 nome_do_arquivo.py`

---

## O que e Indentacao?

[Indentacao](00-glossario-e-i.md#indentacao) e o espacamento a esquerda de uma linha de codigo. Em Python, esse espacamento nao e apenas visual — ele define a **estrutura** do programa.

### Python vs outras linguagens

Em linguagens como Java, C ou JavaScript, os blocos de codigo sao delimitados por chaves `{}`:

```
// Exemplo em Java (NAO e Python!)
if (age >= 18) {
    System.out.println("Maior de idade");
    System.out.println("Pode votar");
}
```

Em Python, nao existem chaves. Os blocos sao definidos pela **indentacao**:

```python
# Exemplo em Python
# As linhas indentadas (recuadas) pertencem ao bloco do if
# "age" = idade
age = 20

if age >= 18:
    # Estas duas linhas estao indentadas — pertencem ao bloco do if
    # Elas so executam se a condicao (age >= 18) for verdadeira
    print("Maior de idade")
    print("Pode votar")

# Esta linha NAO esta indentada — nao pertence ao bloco do if
# Ela executa sempre, independente da condicao
print("Fim do programa")
```

**Saida esperada:**
```
Maior de idade
Pode votar
Fim do programa
```

> **Nota:** Nao se preocupe em entender o `if` completamente agora — vamos aprofundar no modulo 12. O foco aqui e entender como a indentacao define o que esta "dentro" e o que esta "fora" do bloco.

---

## Como Indentar Corretamente

### A regra de ouro: 4 espacos

O padrao do Python (definido pelo PEP 8) e usar **4 espacos** para cada nivel de indentacao. No VSCode, quando voce pressiona a tecla `Tab`, ele automaticamente insere 4 espacos.

```python
# Nivel 0 — sem indentacao (linha principal)
print("Nivel 0")

# Nivel 1 — 4 espacos de indentacao (dentro de um bloco)
if True:
    print("Nivel 1 — dentro do if")

    # Nivel 2 — 8 espacos (bloco dentro de bloco)
    if True:
        print("Nivel 2 — dentro do if interno")
```

**Saida esperada:**
```
Nivel 0
Nivel 1 — dentro do if
Nivel 2 — dentro do if interno
```

### Visualizando a indentacao

Imagine a indentacao como caixas dentro de caixas:

```
Programa (nivel 0)
|
|-- if condicao:
|   |
|   |-- codigo dentro do if (nivel 1)
|   |-- mais codigo dentro do if (nivel 1)
|   |
|   |-- if outra_condicao:
|   |   |
|   |   |-- codigo dentro do if interno (nivel 2)
|   |
|-- codigo fora do if (nivel 0)
```

Tudo que esta "dentro" de um bloco precisa estar recuado um nivel a mais. Quando o recuo volta ao nivel anterior, o bloco terminou.

---

## Tabs vs Espacos

Existem duas formas de criar indentacao: usando a tecla **Tab** ou usando **espacos**. O Python aceita ambas, mas **nunca misture as duas no mesmo arquivo**. Misturar tabs e espacos causa erros.

A recomendacao oficial (PEP 8) e usar **espacos** — especificamente, 4 espacos por nivel. O VSCode, por padrao, converte a tecla Tab em 4 espacos automaticamente, entao voce pode usar a tecla Tab sem preocupacao.

Para verificar se o VSCode esta configurado corretamente, olhe no canto inferior direito da tela. Deve aparecer "Spaces: 4". Se aparecer "Tab Size: 4", clique e mude para "Indent Using Spaces".

---

## Erros Comuns de Indentacao

### IndentationError: unexpected indent

Esse erro aparece quando uma linha esta indentada sem motivo:

```python
# ERRADO — a segunda linha esta indentada sem necessidade
print("Ola")
    print("Mundo")  # IndentationError!
```

**Mensagem de erro:**
```
IndentationError: unexpected indent
```

Traduzindo: "Erro de Indentacao: indentacao inesperada". A segunda linha esta recuada, mas nao ha nenhum bloco (if, for, funcao) que justifique essa indentacao.

**Correcao:**
```python
# CORRETO — ambas as linhas no mesmo nivel
print("Ola")
print("Mundo")
```

### IndentationError: expected an indented block

Esse erro aparece quando voce cria um bloco (if, for, funcao) mas nao coloca nada indentado dentro dele:

```python
# ERRADO — o if espera um bloco indentado, mas nao tem
age = 20
if age >= 18:
print("Maior de idade")  # IndentationError!
```

**Mensagem de erro:**
```
IndentationError: expected an indented block
```

Traduzindo: "Erro de Indentacao: esperava um bloco indentado". Depois do `if age >= 18:`, o Python espera pelo menos uma linha indentada.

**Correcao:**
```python
# CORRETO — a linha dentro do if esta indentada com 4 espacos
age = 20
if age >= 18:
    print("Maior de idade")
```

### TabError: inconsistent use of tabs and spaces

Esse erro aparece quando voce mistura tabs e espacos no mesmo arquivo:

```python
# ERRADO — mistura de tabs e espacos (invisivel a olho nu!)
if True:
	print("Com tab")      # esta linha usa tab
    print("Com espacos")  # esta linha usa espacos — TabError!
```

**Mensagem de erro:**
```
TabError: inconsistent use of tabs and spaces in indentation
```

Traduzindo: "Erro de Tab: uso inconsistente de tabs e espacos na indentacao".

**Correcao:** Use apenas espacos (4 espacos por nivel). No VSCode, selecione todo o codigo (`Ctrl + A`) e use o comando "Convert Indentation to Spaces" na paleta de comandos (`Ctrl + Shift + P`).

---

## Conexao com os Proximos Modulos

A indentacao e essencial para tudo que vem a seguir no curso:

- **Condicionais (modulo 12):** O codigo dentro de `if`, `elif` e `else` precisa estar indentado
- **Loops (modulo 14):** O codigo dentro de `for` e `while` precisa estar indentado
- **Funcoes (modulo 15):** O corpo de uma funcao precisa estar indentado
- **Classes (modulo 22):** Metodos e atributos dentro de uma classe precisam estar indentados

Dominar a indentacao agora vai evitar muita dor de cabeca nos proximos modulos. Se voce entendeu que "linhas recuadas pertencem ao bloco acima", voce ja tem o conceito principal.

---

## Resumo

| Conceito | Descricao |
|----------|-----------|
| Indentacao | Espacamento a esquerda que define blocos de codigo |
| Padrao PEP 8 | 4 espacos por nivel de indentacao |
| Bloco de codigo | Conjunto de linhas indentadas que pertencem a uma estrutura (if, for, def) |
| IndentationError | Erro causado por indentacao incorreta |
| TabError | Erro causado por mistura de tabs e espacos |

---

## Para Saber Mais

- [W3Schools — Python Indentation](https://www.w3schools.com/python/python_syntax.asp) — _Indentacao e sintaxe do Python_
- [W3Schools — Python If...Else](https://www.w3schools.com/python/python_conditions.asp) — _Condicionais (usa indentacao)_
- [PEP 8 — Indentation](https://peps.python.org/pep-0008/#indentation) — _Guia oficial de indentacao_
- [Documentacao Python — Estruturas de Controle](https://docs.python.org/pt-br/3/tutorial/controlflow.html) — _Referencia oficial_

---

## Perguntas Frequentes (FAQ)

**P: Por que Python usa indentacao em vez de chaves como outras linguagens?**
R: O criador do Python, Guido van Rossum, acreditava que a indentacao torna o codigo mais legivel. Em vez de depender de chaves que podem ser esquecidas, o Python forca voce a organizar o codigo visualmente. Com o tempo, a maioria dos programadores concorda que isso torna o codigo mais limpo.

**P: Quantos espacos devo usar?**
R: O padrao e 4 espacos por nivel de indentacao, conforme o PEP 8. Tecnicamente, qualquer numero funciona (2, 3, 4, 8), desde que seja consistente. Mas use 4 — e o que todo mundo usa e o que o VSCode configura por padrao.

**P: Posso usar Tab em vez de espacos?**
R: O Python aceita Tab, mas a recomendacao oficial e usar espacos. O VSCode converte Tab em 4 espacos automaticamente, entao voce pode pressionar Tab sem preocupacao. O importante e nunca misturar tabs e espacos no mesmo arquivo.

**P: Como sei se estou usando tabs ou espacos?**
R: No VSCode, olhe no canto inferior direito da tela. Deve aparecer "Spaces: 4". Voce tambem pode ativar a opcao "Render Whitespace" nas configuracoes para ver os espacos como pontinhos.

**P: O que e um "bloco de codigo"?**
R: E um conjunto de linhas que pertencem a uma mesma estrutura. Por exemplo, todas as linhas indentadas depois de um `if:` formam o bloco do if. Quando a indentacao volta ao nivel anterior, o bloco terminou.

**P: O que significa os dois pontos (:) no final de uma linha?**
R: Os dois pontos indicam que um novo bloco de codigo vai comecar na proxima linha. Voce vai ver isso em `if:`, `for:`, `while:`, `def:` e `class:`. Depois dos dois pontos, a proxima linha precisa estar indentada.

**P: Posso ter blocos dentro de blocos?**
R: Sim! Isso se chama "aninhamento". Cada nivel de bloco adiciona mais 4 espacos de indentacao. Um if dentro de outro if tera 8 espacos de indentacao (4 + 4).

**P: O que acontece se eu indentar uma linha sem motivo?**
R: O Python mostra `IndentationError: unexpected indent`. Toda indentacao precisa ter um motivo — uma estrutura (if, for, def) que justifique o bloco.

**P: O que e `pass`?**
R: E uma palavra-chave que nao faz nada. E usada como placeholder quando voce precisa de um bloco indentado mas ainda nao escreveu o codigo. Exemplo: `if True: pass` — cria um bloco vazio sem erro.

**P: A indentacao afeta a velocidade do programa?**
R: Nao. A indentacao e processada apenas quando o Python le o codigo. Depois disso, nao tem nenhum impacto na velocidade de execucao.

**P: E possivel ter indentacao errada que nao gera erro mas muda o comportamento?**
R: Sim! Se voce indentar uma linha no nivel errado, ela pode pertencer a um bloco diferente do que voce pretendia. O programa roda sem erro, mas faz algo diferente do esperado. Por isso, preste muita atencao na indentacao.

**P: O que e "escopo"?**
R: Escopo e a regiao do codigo onde uma variavel existe e pode ser acessada. Variaveis criadas dentro de um bloco (como dentro de uma funcao) podem nao ser acessiveis fora dele. Vamos aprofundar isso no modulo 15 (Funcoes).

**P: Como o VSCode me ajuda com indentacao?**
R: O VSCode indenta automaticamente quando voce pressiona Enter depois de uma linha com `:`. Ele tambem mostra linhas verticais que conectam os niveis de indentacao, facilitando a visualizacao dos blocos.

**P: O que fazer se meu codigo tem erros de indentacao e eu nao consigo encontrar?**
R: No VSCode, ative "Render Whitespace" para ver espacos e tabs. Selecione todo o codigo (Ctrl+A) e use "Convert Indentation to Spaces" na paleta de comandos (Ctrl+Shift+P). Isso padroniza toda a indentacao.

**P: Linhas em branco precisam de indentacao?**
R: Nao. Linhas em branco podem estar completamente vazias. Elas sao ignoradas pelo Python e servem apenas para separar visualmente partes do codigo.

**P: Comentarios precisam de indentacao?**
R: Sim, se estiverem dentro de um bloco. Um comentario dentro de um if deve estar indentado no mesmo nivel que o codigo do bloco. Isso mantem a organizacao visual.

**P: O que e PEP 8?**
R: E o guia de estilo oficial do Python que define convencoes de formatacao, incluindo indentacao (4 espacos), comprimento de linhas (maximo 79 caracteres) e nomenclatura. Vamos estudar o PEP 8 em detalhes no modulo 27.

**P: Posso ter um bloco com apenas uma linha?**
R: Sim! Um bloco pode ter quantas linhas voce precisar — inclusive apenas uma. `if True: print("ola")` tambem funciona em uma unica linha, mas para legibilidade, prefira colocar o bloco na linha seguinte com indentacao.

**P: Indentacao e a mesma coisa que "recuo" de texto?**
R: Exatamente! Indentar e recuar o texto para a direita. Em editores de texto comuns, voce recua paragrafos. Em Python, voce recua linhas de codigo para indicar que pertencem a um bloco.

**P: Vou errar muito com indentacao no inicio?**
R: Provavelmente sim, e isso e completamente normal. Erros de indentacao sao os mais comuns entre iniciantes. A boa noticia e que o Python sempre avisa quando algo esta errado, e com pratica voce vai indentar corretamente sem nem pensar. Tenha paciencia consigo mesmo.

---

## Exercicios de Fixacao

Os exercicios deste modulo estao em um arquivo separado para facilitar a consulta:

**[Acessar Exercicios do Modulo 10](10-indentacao-escopo-exercicios.md)**

---

[<- Anterior: Manipulacao de Strings](09-manipulacao-strings.md) | [Glossario](00-glossario.md) | [Proximo: Operadores ->](11-operadores.md)
