# Exercícios de Fixação — Função, Vetor, Matriz, PARA e ENQUANTO

> **Lembrete rápido sobre função:**
> Uma **função** é parecida com um procedimento, mas com uma diferença importante: ela **devolve um valor** pro programa principal. Esse valor é entregue com o comando `retorne`.
>
> Sintaxe no VisuAlg:
> ```
> funcao dobro(n: inteiro): inteiro
> inicio
>     retorne n * 2
> fimfuncao
> ```
>
> No programa principal a gente "guarda" o resultado em uma variável:
> ```
> x <- dobro(5)   // x recebe 10
> ```
>
> **Sobre os laços:**
> - **PARA** → quando você já sabe quantas voltas vai dar (percorrer um vetor, uma matriz fixa)
> - **ENQUANTO** → quando depende de uma condição (até achar algo, até o usuário digitar -1)

---

## Questão 1 — Fatorial: Apresentação de Dança ⭐⭐⭐

A professora de Educação Física vai organizar uma apresentação de dança com a turma e ficou na dúvida: **de quantas formas diferentes ela consegue organizar os alunos em uma fila?**

Por exemplo, com **3 alunos** (Ana, Bia e Caio), existem **6 ordens possíveis**:

```
Ana-Bia-Caio    Bia-Ana-Caio    Caio-Ana-Bia
Ana-Caio-Bia    Bia-Caio-Ana    Caio-Bia-Ana
```

Essa quantidade é exatamente o **fatorial** do número de alunos:
- 3 alunos → `3! = 3 × 2 × 1 = 6`
- 5 alunos → `5! = 5 × 4 × 3 × 2 × 1 = 120`
- 7 alunos → `7! = 5040`

**O que fazer:**
Crie uma **função** chamada `fatorial` que recebe a quantidade de alunos (`n`) e **retorna** quantas filas diferentes são possíveis. No programa principal, pergunte quantos alunos a professora tem e mostre o total de filas.

**Exemplo de execução:**
```
Quantos alunos? 5
Total de filas diferentes: 120
```

#### Diagrama

```
              INÍCIO
                 |
            Leia num
                 |
        resultado = fatorial(num)
                 |
        Escreva resultado
                 |
                FIM


       [função fatorial(n)]
                 |
              fat = 1
                 |
        PARA i de 1 até n:
          fat = fat * i
                 |
           RETORNE fat
```

---

## Questão 2 — Cofrinho do Lucas: Juntando pro Brinquedo ⭐⭐⭐

O Lucas tem 8 anos e ganhou um **cofrinho** de presente do avô. Ele recebe uma **mesada semanal** dos pais e quer começar a juntar pra comprar um brinquedo que viu na loja.

Antes de começar a guardar, ele quer saber: **em quantas semanas vai conseguir comprar o brinquedo?**

O programa precisa **simular** esse processo semana por semana: cada semana o Lucas guarda a mesada no cofrinho, e o programa verifica se já tem dinheiro suficiente. Quando o cofrinho atingir (ou passar de) o preço do brinquedo, o programa mostra **quantas semanas demorou**.

> 💡 **Por que usar ENQUANTO?** Você não sabe de antemão quantas semanas vai precisar — depende da relação entre a mesada e o preço. Por isso usa **ENQUANTO** (repete até atingir uma condição), em vez de **PARA** (que precisa de um número fixo de voltas).

**O que fazer:**
Crie uma **função** chamada `semanasParaComprar` que recebe dois valores reais — a **mesada semanal** e o **preço do brinquedo** — e **retorna** quantas semanas o Lucas vai demorar pra juntar o dinheiro.

No programa principal, leia os dois valores e mostre o resultado.

**Exemplo de execução:**
```
Mesada semanal: R$ 10
Preço do brinquedo: R$ 75
O Lucas vai conseguir comprar em 8 semanas
```
> Em 7 semanas ele teria R$ 70 — ainda não dá. Na 8ª semana ele chega a R$ 80 e consegue comprar.

```
Mesada semanal: R$ 15
Preço do brinquedo: R$ 60
O Lucas vai conseguir comprar em 4 semanas
```

#### Diagrama

```
              INÍCIO
                 |
        Leia mesada, preco
                 |
   sem = semanasParaComprar(mesada, preco)
                 |
          Escreva sem
                 |
                FIM


  [função semanasParaComprar(m, p)]
                 |
            total = 0
           semanas = 0
                 |
         ENQUANTO total < p:
           total = total + m
           semanas = semanas + 1
                 |
          RETORNE semanas
```

---

## Questão 3 — MDC: Montando Kits Escolares ⭐⭐⭐⭐

A papelaria da esquina recebeu uma doação: **48 canetas** e **18 cadernos**. O dono quer montar **kits escolares idênticos** pra distribuir nas escolas do bairro, **sem sobrar nada** e fazendo o **maior número possível de kits**.

A pergunta é: **quantos kits ele consegue montar?**

A resposta é o **MDC** (Máximo Divisor Comum) entre 48 e 18 — o maior número que divide os dois ao mesmo tempo. Pra calcular, usamos o **Algoritmo de Euclides**:

> Enquanto `b` for diferente de 0:
> - `resto = a MOD b`
> - `a` recebe `b`
> - `b` recebe `resto`
>
> Quando `b` virar 0, o MDC está em `a`.

Teste de mesa com `a=48` e `b=18`:

| Passo | a  | b  | resto |
|-------|----|----|-------|
| 1     | 48 | 18 | 12    |
| 2     | 18 | 12 | 6     |
| 3     | 12 | 6  | 0     |
| 4     | 6  | 0  | (para)|

MDC = **6**. Logo, dá pra fazer **6 kits**, cada um com 8 canetas e 3 cadernos. 🎒

**O que fazer:**
Crie uma **função** `mdc` que recebe dois inteiros e retorna o MDC. No programa principal, leia a quantidade de canetas e de cadernos e mostre quantos kits podem ser montados.

**Exemplo de execução:**
```
Quantidade de canetas: 48
Quantidade de cadernos: 18
Total de kits possíveis: 6
```

#### Diagrama

```
              INÍCIO
                 |
            Leia a, b
                 |
        resultado = mdc(a, b)
                 |
        Escreva resultado
                 |
                FIM


        [função mdc(a, b)]
                 |
         ENQUANTO b <> 0:
           resto = a MOD b
           a = b
           b = resto
                 |
           RETORNE a
```

---

## Questão 4 — Vetor com Sentinela: Fechamento de Caixa ⭐⭐⭐

Você foi chamado pra fazer o sistema de **fechamento de caixa** de uma cantina. Durante o dia, a funcionária vai digitando o **valor de cada venda** que acontece. Quando o caixa fecha à noite, ela digita **-1** pra avisar o sistema que terminou.

O programa não pode contar com saber quantas vendas vão acontecer no dia (podem ser 5, podem ser 47). Por isso, ele usa o **-1 como sentinela**: enquanto não vier -1, segue lendo.

No fim do expediente, o programa deve mostrar:
- **Quantas vendas** aconteceram no dia
- **A lista** com todos os valores vendidos

⚠️ O `-1` **não** entra no vetor e **não** é contado como venda — ele é só o sinal de "acabou".

Considere o vetor com tamanho máximo de **50 posições** (a cantina nunca passa de 50 vendas/dia).

**O que fazer:**
Use **ENQUANTO** pra ler os valores enquanto não for -1. Depois, use **PARA** pra exibir o que foi armazenado.

**Exemplo de execução:**
```
Valor da venda: 10
Valor da venda: 25
Valor da venda: 8
Valor da venda: 15
Valor da venda: -1

Total de vendas do dia: 4
Vendas: 10, 25, 8, 15
```

#### Diagrama

```
              INÍCIO
                 |
              n = 0
            Leia val
                 |
        ENQUANTO val <> -1:
          n = n + 1
          vet[n] = val
          Leia val
                 |
        Escreva "Total:", n
                 |
        PARA i de 1 até n:
          Escreva vet[i]
                 |
                FIM
```

---

## Questão 5 — Contar Múltiplos: Promoção do Supermercado ⭐⭐⭐

O gerente do supermercado quer fazer uma **promoção temática**: ele vai juntar em uma prateleira só os produtos cujo preço é **múltiplo de um certo valor** (R$ 5, R$ 10, depende do dia). Antes de mandar o repositor fazer a separação, ele quer saber **quantos produtos** vão pra prateleira.

O sistema tem cadastrado o **preço de 10 produtos**. O gerente vai digitar qual divisor ele quer usar e o programa deve responder quantos produtos têm preço múltiplo daquele valor.

> 💡 **Lembrete:** um número é múltiplo de outro quando o resto da divisão é zero. Ex: 25 é múltiplo de 5 porque `25 MOD 5 = 0`.

**O que fazer:**
1. Leia os 10 preços em um vetor.
2. Leia o divisor escolhido pelo gerente.
3. Crie uma **função** `contarMultiplos` que recebe o vetor e o divisor e **retorna** quantos preços são múltiplos.
4. Mostre a quantidade encontrada.

**Exemplo de execução:**
```
Preços cadastrados:
10, 7, 25, 13, 50, 8, 100, 15, 4, 35

Qual o divisor da promoção? 5
Produtos que entram na promoção: 6
```
(porque 10, 25, 50, 100, 15 e 35 são múltiplos de 5)

#### Diagrama

```
              INÍCIO
                 |
        PARA i de 1 até 10:
          Leia vet[i]
                 |
            Leia divisor
                 |
        qtd = contarMultiplos(vet, divisor)
                 |
           Escreva qtd
                 |
                FIM


    [função contarMultiplos(v, d)]
                 |
              cont = 0
                 |
        PARA i de 1 até 10:
          v[i] MOD d = 0?
           /          \
         SIM          NÃO
          |         (próx i)
       cont = cont + 1
                 |
           RETORNE cont
```

---

## Questão 6 — Busca em Vetor: Lista de Convidados ⭐⭐⭐⭐

Você foi contratado pra fazer o sistema de **entrada de uma festa fechada**. A organização cadastrou previamente os **números de identificação** (RG ou CPF) de **8 pessoas convidadas**. Na hora da festa, quando alguém chega na porta, a pessoa digita o número dela e o sistema responde:

- Se **estiver** na lista: `"Acesso liberado — convidado da posição X"`
- Se **não estiver**: `"Acesso negado — não está na lista"`

Como tem fila na porta, o sistema **não pode ficar lento**: assim que achar a pessoa na lista, deve **parar de procurar** na mesma hora.

**O que fazer:**
Crie uma **função** `buscarPosicao` que recebe o vetor de convidados e o número da pessoa que chegou, e **retorna**:
- A **posição** (1 a 8) se encontrar
- `-1` se não encontrar

A função deve usar **ENQUANTO** com duas condições: continuar enquanto `i <= 8` **E** ainda não achou ninguém. Assim que achar, o laço para sozinho.

**Exemplo de execução:**
```
Convidados cadastrados:
1234, 5678, 9012, 3456, 7890, 2345, 6789, 1357

Digite seu número de identificação: 7890
Acesso liberado - convidado da posição 5

Digite seu número de identificação: 9999
Acesso negado - não está na lista
```

#### Diagrama

```
              INÍCIO
                 |
        PARA i de 1 até 8:
          Leia vet[i]
                 |
            Leia alvo
                 |
        pos = buscarPosicao(vet, alvo)
                 |
             pos = -1?
            /         \
          SIM         NÃO
           |           |
   "Não encontrado" "Encontrado na
                     posição", pos
           |           |
          FIM         FIM


   [função buscarPosicao(v, x)]
                 |
              i = 1
            achou = -1
                 |
   ENQUANTO i <= 8 E achou = -1:
     v[i] = x?
      /        \
    SIM        NÃO
     |          |
  achou = i  i = i + 1
                 |
         RETORNE achou
```

---

## Questão 7 — Vetor Ordenado: Conferência da Fila do Posto ⭐⭐⭐⭐

No posto de saúde, as pessoas pegam **senha por ordem de chegada** e ficam esperando ser chamadas. A recepcionista digitou no sistema as **6 senhas** que estão na fila agora, mas ficou desconfiada — parece que alguém **furou a fila**, ou seja, a sequência das senhas pode não estar mais em ordem crescente.

O programa precisa olhar a sequência de senhas e responder se a fila está **organizada corretamente** (em ordem crescente) ou se **alguém furou** (tem senha menor depois de uma maior).

> 💡 **Como detectar:** uma fila está em ordem se, para cada par de senhas consecutivas, a primeira é **menor ou igual** à segunda. Basta achar **um único** par fora de ordem pra concluir que tem alguém furando.

**O que fazer:**
1. Leia as 6 senhas no vetor.
2. Crie uma **função** `vetorOrdenado` (do tipo `logico`) que recebe o vetor e retorna `VERDADEIRO` se está em ordem ou `FALSO` se não está.
3. Mostre `"Fila correta"` ou `"Fila fora de ordem - alguém furou!"`.

**Exemplo de execução:**
```
Caso 1:
Senhas digitadas: 12, 15, 18, 23, 29, 31
Fila correta

Caso 2:
Senhas digitadas: 12, 15, 20, 17, 29, 31
Fila fora de ordem - alguém furou!
```
(no Caso 2, depois da senha 20 veio a 17, que é menor)

#### Diagrama

```
              INÍCIO
                 |
        PARA i de 1 até 6:
          Leia vet[i]
                 |
        ord = vetorOrdenado(vet)
                 |
        ord = VERDADEIRO?
        /             \
      SIM             NÃO
       |               |
 "Fila correta"  "Alguém furou!"
       |               |
      FIM             FIM


      [função vetorOrdenado(v)]
                 |
       ordenado = VERDADEIRO
                 |
        PARA i de 1 até 5:
          v[i] > v[i+1]?
           /         \
         SIM         NÃO
          |        (próx i)
    ordenado = FALSO
                 |
        RETORNE ordenado
```

---

## Questão 8 — Soma da Matriz: Faturamento da Rede de Lojas ⭐⭐⭐

Uma rede de lojas tem **3 filiais** que vendem **3 produtos diferentes**. No fim do mês, o financeiro montou uma planilha com o **faturamento de cada produto em cada filial**:

```
                 Produto A    Produto B    Produto C
Filial 1            500          800          300
Filial 2            450          900          250
Filial 3            600          750          400
```

O dono quer saber **o faturamento total** da rede inteira nesse mês — basta somar todos os 9 valores da planilha.

**O que fazer:**
1. Leia uma **matriz 3x3** com os valores de faturamento.
2. Crie uma **função** `somaTotal` que recebe a matriz e **retorna** a soma de todos os elementos.
3. Mostre o faturamento total da rede.

**Exemplo de execução:**
```
[lê os 9 valores]
500 800 300
450 900 250
600 750 400

Faturamento total da rede: R$ 4950
```

#### Diagrama

```
              INÍCIO
                 |
        PARA i de 1 até 3:
          PARA j de 1 até 3:
            Leia mat[i, j]
                 |
        total = somaTotal(mat)
                 |
          Escreva total
                 |
                FIM


       [função somaTotal(m)]
                 |
              soma = 0
                 |
        PARA i de 1 até 3:
          PARA j de 1 até 3:
            soma = soma + m[i, j]
                 |
          RETORNE soma
```

---

## Questão 9 — Menor por Linha: Pior Semana de Cada Vendedor ⭐⭐⭐⭐

Uma loja tem **4 vendedores** e o gerente acompanha o desempenho deles ao longo das **4 semanas** do mês. Ele montou uma planilha onde cada **linha** representa um vendedor e cada **coluna** uma semana:

```
                Sem 1   Sem 2   Sem 3   Sem 4
Vendedor 1      1500    800     2000    1200
Vendedor 2      1200    1800    1500    2100
Vendedor 3      900     500     1100    800
Vendedor 4      2000    1700    1500    1800
```

Pra dar um feedback construtivo na reunião do mês, o gerente quer descobrir **qual foi a pior semana de cada vendedor** (o menor valor vendido por ele). Assim, ele pode entender o que aconteceu e ajudar a melhorar.

**O que fazer:**
1. Leia uma **matriz 4x4** com as vendas.
2. Pra **cada linha** (vendedor), encontre o **menor** valor.
3. Mostre o resultado linha por linha.

> 💡 **Dica:** pra cada linha, comece assumindo que o menor é o primeiro valor (`mat[i, 1]`) e vá comparando com os outros 3 da mesma linha.

**Exemplo de execução:**
```
[lê os 16 valores]

Vendedor 1: pior semana = R$ 800
Vendedor 2: pior semana = R$ 1200
Vendedor 3: pior semana = R$ 500
Vendedor 4: pior semana = R$ 1500
```

#### Diagrama

```
              INÍCIO
                 |
        PARA i de 1 até 4:
          PARA j de 1 até 4:
            Leia mat[i, j]
                 |
        PARA i de 1 até 4:
          menor = mat[i, 1]
                 |
          PARA j de 2 até 4:
            mat[i, j] < menor?
             /          \
           SIM          NÃO
            |         (próx j)
        menor = mat[i, j]
                 |
       Escreva "Vendedor", i,
       "pior semana =", menor
                 |
         (próxima linha)
                 |
                FIM
```

---

## Questão 10 — Matriz Simétrica: Tabela de Distâncias ⭐⭐⭐⭐

O setor de logística de uma transportadora montou uma **tabela de distâncias** entre 3 cidades pra calcular rotas. Como a distância de A até B é sempre **igual** à distância de B até A (vai e volta dá o mesmo), a tabela precisa ser **simétrica** — o que está acima da diagonal deve ser igual ao que está abaixo, espelhado.

Exemplo de tabela **correta** (simétrica):

```
            Cidade1   Cidade2   Cidade3
Cidade1       0        150       200
Cidade2      150        0         80
Cidade3      200        80         0
```

Veja que `mat[1,2] = mat[2,1] = 150`, `mat[1,3] = mat[3,1] = 200`, etc.

Se algum estagiário digitar errado, a tabela fica **inconsistente** (não simétrica) e os cálculos de rota dão errado. O programa precisa **verificar se a tabela digitada está consistente**.

**O que fazer:**
1. Leia uma **matriz 3x3** com a tabela de distâncias.
2. Crie uma **função** `matrizSimetrica` (do tipo `logico`) que recebe a matriz e retorna `VERDADEIRO` se for simétrica ou `FALSO` se não for.
3. Mostre `"Tabela consistente"` ou `"Erro: tabela inconsistente"`.

> 💡 **Definição formal:** uma matriz é simétrica quando `mat[i, j] = mat[j, i]` pra todos os pares `i, j`. Basta encontrar **um** par diferente pra a função retornar `FALSO`.

**Exemplo de execução:**
```
Caso 1 (simétrica):
0   150  200
150   0   80
200  80    0
Tabela consistente

Caso 2 (estagiário errou a distância C2-C1):
0   150  200
130   0   80
200  80    0
Erro: tabela inconsistente
```

#### Diagrama

```
              INÍCIO
                 |
        PARA i de 1 até 3:
          PARA j de 1 até 3:
            Leia mat[i, j]
                 |
        sim = matrizSimetrica(mat)
                 |
        sim = VERDADEIRO?
        /             \
      SIM             NÃO
       |               |
"Tabela consistente" "Tabela inconsistente"
       |               |
      FIM             FIM


    [função matrizSimetrica(m)]
                 |
       simetrica = VERDADEIRO
                 |
        PARA i de 1 até 3:
          PARA j de 1 até 3:
            m[i, j] <> m[j, i]?
             /           \
           SIM           NÃO
            |          (próx j)
    simetrica = FALSO
                 |
       RETORNE simetrica
```

---

## Resumo dos conceitos por questão

| Questão | Cenário | Função | Vetor | Matriz | PARA | ENQUANTO |
|---------|---------|:------:|:-----:|:------:|:----:|:--------:|
| 1 — Apresentação de dança | Fatorial          | ✓ |   |   | ✓ |   |
| 2 — Cofrinho do Lucas     | Simulação semanal | ✓ |   |   |   | ✓ |
| 3 — Kits escolares        | MDC (Euclides)    | ✓ |   |   |   | ✓ |
| 4 — Fechamento de caixa   | Vetor sentinela   |   | ✓ |   | ✓ | ✓ |
| 5 — Promoção do mercado   | Múltiplos         | ✓ | ✓ |   | ✓ |   |
| 6 — Lista de convidados   | Busca em vetor    | ✓ | ✓ |   |   | ✓ |
| 7 — Fila do posto         | Verificar ordem   | ✓ | ✓ |   | ✓ |   |
| 8 — Faturamento de rede   | Soma de matriz    | ✓ |   | ✓ | ✓ |   |
| 9 — Pior semana           | Menor por linha   |   |   | ✓ | ✓ |   |
| 10 — Tabela de distâncias | Matriz simétrica  | ✓ |   | ✓ | ✓ |   |

---

## Legenda do diagrama

| Símbolo | Significado |
|---------|-------------|
| `INÍCIO` / `FIM` | Início e fim do algoritmo ou função |
| `Leia / Escreva` | Entrada e saída de dados |
| `?` | Decisão (SE) |
| `SIM / NÃO` | Caminhos das ramificações |
| `PARA i de X até Y` | Laço com número definido de repetições |
| `ENQUANTO cond` | Laço baseado em condição |
| `[função nome(...)]` | Sub-rotina que **retorna** valor com `RETORNE` |
