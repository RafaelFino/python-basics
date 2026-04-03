# Exercicios — Modulo 09: Manipulacao de Strings

[<- Voltar ao Modulo 09](09-manipulacao-strings.md) | [Glossario](00-glossario.md)

> **Como usar estes exercicios:**
> 1. Leia o enunciado com atencao
> 2. Leia as dicas antes de comecar
> 3. Tente resolver sozinho
> 4. Use a Proposta de Teste para verificar se sua solucao funciona
> 5. So depois consulte a Resposta Comentada
>
> **Como testar:** Salve seu codigo na pasta `~/meus-projetos/python-curso/modulo-09/` e execute com `python3 nome_do_arquivo.py`.

---

## Exercicio 1 — Saudacao com f-string — Nivel: Basico

### Enunciado
Peca o nome e a idade do usuario e exiba uma mensagem usando f-string.

### Dicas
- Use `input()` para ler os dados
- Use f-string: `f"texto {variavel} texto"`

### Proposta de Teste
- **Caso basico:** Nome: `Ana`, Idade: `25` — Saida: `Ola, Ana! Voce tem 25 anos.`
- **Caso de borda:** Nome: `Jo`, Idade: `8` — Deve funcionar com nomes curtos

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos o nome e a idade do usuario
# "name" = nome, "age" = idade
name = input("Seu nome: ")
age = input("Sua idade: ")

# Usamos f-string para formatar a mensagem
# As chaves {} sao substituidas pelos valores das variaveis
# "message" = mensagem
message = f"Ola, {name}! Voce tem {age} anos."

# Exibimos a mensagem formatada
print(message)
```

---

## Exercicio 2 — Texto em Maiusculas e Minusculas — Nivel: Basico

### Enunciado
Peca uma frase ao usuario e exiba a frase em maiusculas, em minusculas e a original.

### Dicas
- Use `.upper()` para maiusculas
- Use `.lower()` para minusculas
- Lembre-se: os metodos nao alteram o original

### Proposta de Teste
- **Caso basico:** Frase: `Bom Dia` — Maiusculas: `BOM DIA`, Minusculas: `bom dia`, Original: `Bom Dia`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos uma frase ao usuario
# "sentence" = frase
sentence = input("Digite uma frase: ")

# upper() converte para maiusculas — retorna um NOVO texto
print("Maiusculas:", sentence.upper())

# lower() converte para minusculas — retorna um NOVO texto
print("Minusculas:", sentence.lower())

# O texto original nao foi alterado pelos metodos
print("Original:", sentence)
```

---

## Exercicio 3 — Contando Caracteres — Nivel: Basico

### Enunciado
Peca um texto ao usuario e exiba quantos caracteres ele tem (incluindo espacos) e quantos caracteres tem sem os espacos das bordas.

### Dicas
- Use `len()` para contar caracteres
- Use `.strip()` para remover espacos das bordas

### Proposta de Teste
- **Caso basico:** Texto: `  Python  ` — Com espacos: 10, Sem espacos das bordas: 6
- **Caso de borda:** Texto: `abc` (sem espacos) — Ambos devem ser 3

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos um texto ao usuario
# "text" = texto
text = input("Digite um texto: ")

# len() conta todos os caracteres, incluindo espacos
# "total_length" = comprimento total
total_length = len(text)

# strip() remove espacos do inicio e fim, depois contamos
# "stripped_length" = comprimento sem espacos das bordas
stripped_length = len(text.strip())

# Exibimos os resultados
print(f"Texto: '{text}'")
print(f"Caracteres (com espacos): {total_length}")
print(f"Caracteres (sem espacos das bordas): {stripped_length}")
```

---

## Exercicio 4 — Primeira e Ultima Letra — Nivel: Basico

### Enunciado
Peca uma palavra ao usuario e exiba a primeira letra e a ultima letra.

### Dicas
- Primeira letra: `palavra[0]`
- Ultima letra: `palavra[-1]`

### Proposta de Teste
- **Caso basico:** Palavra: `Python` — Primeira: `P`, Ultima: `n`
- **Caso de borda:** Palavra: `a` — Primeira e ultima sao `a`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos uma palavra ao usuario
# "word" = palavra
word = input("Digite uma palavra: ")

# Acessamos a primeira letra (posicao 0) e a ultima (posicao -1)
# "first_letter" = primeira letra, "last_letter" = ultima letra
first_letter = word[0]
last_letter = word[-1]

# Exibimos os resultados
print(f"Palavra: {word}")
print(f"Primeira letra: {first_letter}")
print(f"Ultima letra: {last_letter}")
```

---

## Exercicio 5 — Substituindo Palavras — Nivel: Intermediario

### Enunciado
Peca uma frase ao usuario e duas palavras: a palavra a ser substituida e a nova palavra. Exiba a frase com a substituicao feita.

### Dicas
- Use `.replace(antigo, novo)`
- Lembre-se: replace() retorna um novo texto

### Proposta de Teste
- **Caso basico:** Frase: `Eu gosto de cafe`, Trocar: `cafe`, Por: `cha` — Saida: `Eu gosto de cha`
- **Caso de borda:** Palavra nao encontrada — a frase permanece igual

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos a frase original
# "sentence" = frase
sentence = input("Digite uma frase: ")

# Pedimos a palavra a ser substituida
# "old_word" = palavra antiga (a ser trocada)
old_word = input("Palavra a substituir: ")

# Pedimos a nova palavra
# "new_word" = palavra nova (substituta)
new_word = input("Substituir por: ")

# replace() troca todas as ocorrencias da palavra antiga pela nova
# "new_sentence" = nova frase (com a substituicao)
new_sentence = sentence.replace(old_word, new_word)

# Exibimos o resultado
print(f"Original: {sentence}")
print(f"Modificada: {new_sentence}")
```

---

## Exercicio 6 — Extraindo Partes de um Texto — Nivel: Intermediario

### Enunciado
Peca ao usuario um texto com pelo menos 10 caracteres. Exiba os 5 primeiros caracteres, os 5 ultimos e os caracteres do meio (da posicao 3 ate a posicao 7).

### Dicas
- Primeiros 5: `texto[:5]`
- Ultimos 5: `texto[-5:]`
- Meio: `texto[3:8]`

### Proposta de Teste
- **Caso basico:** Texto: `Programacao` — Primeiros 5: `Progr`, Ultimos 5: `macao`, Meio: `grama`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos um texto ao usuario
# "text" = texto
text = input("Digite um texto com pelo menos 10 caracteres: ")

# Fatiamos o texto em diferentes partes
# text[:5] pega do inicio ate a posicao 4 (5 caracteres)
# "first_five" = primeiros cinco
first_five = text[:5]

# text[-5:] pega os ultimos 5 caracteres
# "last_five" = ultimos cinco
last_five = text[-5:]

# text[3:8] pega da posicao 3 ate a 7 (5 caracteres do meio)
# "middle" = meio
middle = text[3:8]

# Exibimos os resultados
print(f"Texto completo: {text}")
print(f"Primeiros 5: {first_five}")
print(f"Ultimos 5: {last_five}")
print(f"Meio (posicoes 3 a 7): {middle}")
```

---

## Exercicio 7 — Contando Ocorrencias — Nivel: Intermediario

### Enunciado
Peca uma frase e uma letra ao usuario. Conte quantas vezes a letra aparece na frase (considerando maiusculas e minusculas como iguais).

### Dicas
- Converta tudo para minusculas com `.lower()` antes de contar
- Use `.count()` para contar

### Proposta de Teste
- **Caso basico:** Frase: `Banana`, Letra: `a` — Deve contar 3 (incluindo o A maiusculo convertido)
- **Caso de borda:** Letra nao encontrada — Deve mostrar 0

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos a frase e a letra
# "sentence" = frase, "letter" = letra
sentence = input("Digite uma frase: ")
letter = input("Qual letra deseja contar? ")

# Convertemos tudo para minusculas para ignorar maiusculas/minusculas
# lower() garante que "A" e "a" sejam tratados como iguais
# "count" = contagem (quantas vezes a letra aparece)
count = sentence.lower().count(letter.lower())

# Exibimos o resultado usando f-string
print(f"A letra '{letter}' aparece {count} vez(es) na frase.")
```

---

## Exercicio 8 — Verificando Extensao de Arquivo — Nivel: Intermediario

### Enunciado
Peca o nome de um arquivo ao usuario e verifique se ele termina com `.py` (arquivo Python), `.txt` (arquivo de texto) ou outro tipo.

### Dicas
- Use `.endswith()` para verificar o final do texto
- Neste exercicio, use apenas `if` simples (sem elif) — verifique cada extensao separadamente

### Proposta de Teste
- **Caso basico:** Arquivo: `programa.py` — Saida: `Arquivo Python`
- **Caso de borda:** Arquivo: `foto.jpg` — Saida: `Outro tipo de arquivo`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos o nome do arquivo
# "filename" = nome do arquivo
filename = input("Nome do arquivo: ")

# Verificamos a extensao usando endswith()
# endswith() retorna True se o texto termina com o valor especificado
# Nota: estamos usando if/elif/else que sera aprofundado no modulo 12
# Por enquanto, entenda que "if" significa "se" e "elif" significa "senao se"
if filename.endswith(".py"):
    # Se termina com .py, e um arquivo Python
    print("Arquivo Python")
elif filename.endswith(".txt"):
    # Se termina com .txt, e um arquivo de texto
    print("Arquivo de texto")
else:
    # Se nao termina com nenhum dos anteriores
    print("Outro tipo de arquivo")
```

> **Nota:** Este exercicio usa `if/elif/else`, que sera estudado em detalhes no modulo 12. Por enquanto, entenda que o programa verifica cada condicao e executa o bloco correspondente.

---

## Exercicio 9 — Formatando Nome Completo — Nivel: Intermediario

### Enunciado
Peca o primeiro nome e o sobrenome do usuario. Exiba o nome completo formatado de tres formas: normal, tudo maiusculo e com a primeira letra de cada palavra em maiuscula.

### Dicas
- Junte os nomes com f-string ou concatenacao
- Use `.upper()` para maiusculas
- Use `.title()` para primeira letra maiuscula em cada palavra

### Proposta de Teste
- **Caso basico:** Nome: `maria`, Sobrenome: `silva` — Normal: `maria silva`, Maiusculo: `MARIA SILVA`, Titulo: `Maria Silva`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos o primeiro nome e o sobrenome
# "first_name" = primeiro nome, "last_name" = sobrenome
first_name = input("Primeiro nome: ")
last_name = input("Sobrenome: ")

# Juntamos em nome completo usando f-string
# "full_name" = nome completo
full_name = f"{first_name} {last_name}"

# Exibimos em tres formatos diferentes
# upper() = tudo maiusculo
# title() = primeira letra de cada palavra em maiuscula
print(f"Normal: {full_name}")
print(f"Maiusculo: {full_name.upper()}")
print(f"Titulo: {full_name.title()}")
```

---

## Exercicio 10 — Invertendo uma Palavra — Nivel: Avancado

### Enunciado
Peca uma palavra ao usuario e exiba a palavra invertida (de tras para frente).

### Dicas
- Use fatiamento com passo negativo: `texto[::-1]`
- `[::-1]` significa "do fim ao inicio, de 1 em 1"

### Proposta de Teste
- **Caso basico:** Palavra: `Python` — Invertida: `nohtyP`
- **Caso de borda:** Palavra: `aba` — Invertida: `aba` (palindromo)

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos uma palavra ao usuario
# "word" = palavra
word = input("Digite uma palavra: ")

# Invertemos usando fatiamento com passo negativo
# [::-1] percorre a string de tras para frente
# "reversed_word" = palavra invertida
reversed_word = word[::-1]

# Exibimos o resultado
print(f"Original: {word}")
print(f"Invertida: {reversed_word}")
```

---

## Exercicio 11 — Separando e Juntando — Nivel: Avancado

### Enunciado
Peca ao usuario uma frase com varias palavras. Separe as palavras, exiba cada uma em uma linha, e depois junte-as novamente usando hifen (-) como separador.

### Dicas
- Use `.split()` para separar
- Use `"-".join(lista)` para juntar com hifen
- Use um loop `for` para exibir cada palavra (sera aprofundado no modulo 14)

### Proposta de Teste
- **Caso basico:** Frase: `eu gosto de python` — Palavras separadas, depois: `eu-gosto-de-python`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos uma frase ao usuario
# "sentence" = frase
sentence = input("Digite uma frase: ")

# Separamos a frase em palavras usando split()
# split() divide nos espacos e retorna uma lista
# "words" = palavras
words = sentence.split()

# Exibimos cada palavra separadamente
# "for" percorre cada item da lista (sera aprofundado no modulo 14)
print("Palavras separadas:")
for word in words:
    # "word" = cada palavra individual da lista
    print(f"  - {word}")

# Juntamos as palavras com hifen usando join()
# join() e o oposto de split() — junta uma lista em um texto
# "joined" = texto juntado
joined = "-".join(words)

print(f"\nJuntadas com hifen: {joined}")
```

---

## Exercicio 12 — Gerador de Email — Nivel: Avancado

### Enunciado
Peca o primeiro nome e o sobrenome do usuario. Gere um email no formato `nome.sobrenome@empresa.com`, tudo em minusculas e sem espacos extras.

### Dicas
- Use `.lower()` para converter para minusculas
- Use `.strip()` para remover espacos extras
- Use f-string para montar o email

### Proposta de Teste
- **Caso basico:** Nome: `  Maria  `, Sobrenome: `  Silva  ` — Email: `maria.silva@empresa.com`
- **Caso de borda:** Nome: `JOAO`, Sobrenome: `SANTOS` — Email: `joao.santos@empresa.com`

### Resposta Comentada

> **Importante:** Tente resolver sozinho primeiro!

```python
# Pedimos o primeiro nome e o sobrenome
# "first_name" = primeiro nome, "last_name" = sobrenome
first_name = input("Primeiro nome: ")
last_name = input("Sobrenome: ")

# Limpamos e padronizamos os nomes:
# strip() remove espacos extras do inicio e fim
# lower() converte para minusculas
# "clean_first" = primeiro nome limpo
clean_first = first_name.strip().lower()

# "clean_last" = sobrenome limpo
clean_last = last_name.strip().lower()

# Montamos o email usando f-string
# "email" = endereco de email
email = f"{clean_first}.{clean_last}@empresa.com"

# Exibimos o resultado
print(f"Email gerado: {email}")
```

---

[<- Voltar ao Modulo 09](09-manipulacao-strings.md) | [Glossario](00-glossario.md)
