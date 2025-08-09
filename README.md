# RegEx - Regular Expressions

### O que é?

- Notação que faz verificação em textos, com 3 principais aplicações

1. Efetuar buscas por padrões

2. Efetuar validações em texto

3. Fazer Substituições

**Exemplos de uso:**

`[0]` -> Seleciona todos os números 0

`[02]` ou `[0|2]` -> Seleciona todos os 0 ou 2

`[0-9]` -> Seleciona todos os números entre 0 e 9

- **Quantificadores:** Multiplicam os usos anteriores. Exemplo:

```bash
[0]{2} -> Até duas ocorrencias do caractere 0

[0-9]{6} -> Destaca os 6 digitos números da linha
```

`$` -> Representa o fim da linha. Exemplo:

```bash
[0-9]{2}$ -> Resgata os ultimos dois caracteres
```

`^` -> Representa o inicio da linha. Exemplo:

```bash
^[0-9]{2}$ -> Somente as linhas que possuem 2 caracteres serão resgatadas
```

`+` -> Um número qualquer de ocorrencias de determinado digito

```bash
[0-9]+[-][a-z] -> Aplica o padrão pra QUALQUER ocorrencia, em qualquer posição.

^[0-9]+[-][a-z]$ -> Resgata as letras todas as linhas que tenham qualquer quantidade de números, com qualquer letra no final.

^[0-9]+[-][e]$ -> Resgata as letras todas as linhas que tenham qualquer quantidade de números, porém apenas os que tem a letra E no final.
```

##### Como seria o RegEx pra validar CPF

**Como um CPF é formado:**

- Primeiro Bloco com 3 caracteres, ou [0-9]{3}
- Ponto
- Segundo Bloco com 3 caracteres, ou [0-9]{3}
- Ponto
- Terceiro Bloco com 3 caracteres, ou [0-9]{3}
- Traço
- Quarto Bloco com 2 caracteres, ou [0-9]{2}

**Como ficaria isso junto**:

```bash
[0-9]{3}[.][0-9]{3}[.][0-9]{3}[-][0-9]{2}

```

`()` -> Ele é usado para agrupar valoress, ele vem após a expressão e tudo que estiver dentro dele será o novo valor.

Exemplo:

```bash
    ([0-9]{4})[-]([0-9]{2})[-]([0-9]{2})
     grupo 1       grupo 2      grupo 3
```

- Outro Exemplo:

```bash
    2010-12-20 -> A data original
    ([0-9]{4})[-]([0-9]{2})[-]([0-9]{2}) -> Em forma de RegEx

```

- E para acessar os grupos, usamos "$" e o numero do grupo. Assim:

```bash
    $3/$2/$1 -> Assim a data fica: 20/12/2010
```

`\d` -> Digitos -> Qualquer número, excluindo todos as letras. Uso IGUAL ao "[0-9]", totalmente semelhante.

`\D` -> Eu chamo de Non-Digits -> Exato oposto do "\d", resgata todas as letras, excluindo os números
