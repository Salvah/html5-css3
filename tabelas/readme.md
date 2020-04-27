# Tabelas

## Referências

[W3C](https://dev.w3.org/html5/spec-LC/tabular-data.html)

[MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table)

[w3schools](https://www.w3schools.com/html/html_tables.asp)

## Introdução

Tabelas são utilizadas para representar dados tabulares no formato de linhas e colunas.
Antigamente, antes do surgimento do CSS, muitos utilizavam as tabelas para organizar a estrutura do site.
Elas não devem ser utilizadas para esse propósito. Esta prática não é recomendada.

### Estrutura básica

A tabela é formada por um conjunto de linhas e colunas.

![](tabela.png?w=100)

A tag **\<table\>** é utilizada para definir uma tabela. A tag **\<tr\>** é utilizada para representar uma linha, a tag **\<th\>** representa uma célula de cabeçalho e a tag **\<td\>** uma célula de dados.
A seguir é apresentado um exemplo.

```
<table>
    <tr>
        <th>Estado</th>
        <th>Sigla</th>
    </tr>
    <tr>
        <td>Rio Grande do Sul</td>
        <td>RS</td>
    </tr>
</table>
```

### Linhas

A tag **\<tr\>** define uma linha na tabela. Pode conter uma combinação de **\<th\>** e **\<td\>**.

- Pode ser filha do elemento **\<table\>** caso não tenha o elemento **\<tbody\>** especificado;
- Pode ser filha dos seguintes elementos: **\<thead\>**, **\<tbody\>** e **\<tfoot\>**;
- Deve vir depois dos elementos **\<caption\>**, **\<colgroup\>** e **\<thead\>** (quando especificados).

```
<table>
    ...
    <tr>
    ...
    </tr>
    ...
</table>
```

### Células

A tag **\<th\>** define uma célula cabeçalho da tabela (_table header_), enquanto a tag **\<td\>** define uma célula de dados (_table data_).

- Ela deve ser filha do elemento **\<tr\>**;
- Ela não precisa ser fechada caso seja imediatamente seguida por outra **\<th\>** ou **\<td\>**;

Os parâmetros aceitos são:

1. **_colspan_**: Mescla células de colunas adjacentes na mesma linha; Recebe um valor entre 1 e 1000. Quando o valor for incorreto será atribuído o valor padrão 1.
2. **_rowspan_**: Mescla células de linhas diferentes na mesma coluna; Recebe um valor entre 0 e 65534. Quando atribuído o valor 0, ela irá mesclar todas as células daquela coluna.
3. **_headers_**: (não possui efeito visual). Recebe uma lista de ids das células relacionadas.

4. **_scope_**: (não possui efeito visual). Pode ser col, row, rowgroup e colgroup. Serve para indicar a relação da célula. (específico para **th**)

```
<table>
    ...
    <tr>
        <!-- A TH irá ocupar o espaço de duas células da mesma linha  !-->
        <th colspan="2">...</th>
        ...
    </tr>
    <tr>
        <!-- A TD irá ocupar o espaço de três células da mesma coluna  !-->
        <td rowpan="3">...</td>
        ...
    </tr>
    ...
</table>
```

## Legenda

A tag **\<caption\>** define um título para a tabela.

- Ela deve ser o primeiro elemento filho de **\<table\>**;
- Quando **\<table\>** for filho de **\<figure\>**, você deve utilizar **\<figcaption\>**;
- As tags de abertura e fechamento são obrigatórias.
- Por padrão elas são posicionadas em cima da tabela.

```
<table>
    <caption>Estados do Brasil</caption>
    ...
</table>
```

## SEGMENTOS DE LINHAS

É possível separar a tabela em 3 segmentos **\<thead\>**, **\<tbody\>** e **\<tfoot\>**. Os segmentos são úteis para ajudar o navegador a renderizar a tabela, eles dão uma semântica para a tabela.

### THEAD

Define um conjunto de linhas utilizadas para representar o cabeçalho da tabela. É possível indicar para o navegador repetir o cabeçalho da tabela a cada nova página impressa que contenha a tabela.

- Permite zero ou mais elementos **\<tr\>**;
- A tag de abertura é obrigatória. Já a tag de fechamento pode ser omitida caso seja imediatamente seguida pelo **\<tbody\>** ou **\<tfoot\>**.

```
<table>
    <caption>Estados do Brasil</caption>
    <thead>
        <tr>
            <th>Estado</th>
            <th>Sigla</th>
        </tr>
    </thead>
    ...
</table>
```

### TBODY

Define um conjunto de linhas utilizadas para representar o segmento de dados da tabela. É possível indicar para o navegador aplicar barra de rolagem somente nesse segmento caso a tabela tenha muitas linhas e você queria evitar quebrar o layout do site.

- Permite zero ou mais elementos **\<tr\>**;
- Não é um elemento obrigatório porém, caso a **\<table\>** tenha filhos **\<tr\>**, ele não pode estar presente.
- Quando especificado, deve vir após os elementos **\<caption\>**, **\<colgroup\>** e **\<thead\>**.

```
<table>
    <caption>Estados do Brasil</caption>
    <thead>
        <tr>
            <th>Estado</th>
            <th>Sigla</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Rio Grande do Sul</td>
            <td>RS</td>
        </tr>
        ...
    </tbody>
</table>
```

### TFOOT

Define um conjunto de linhas utilizadas para representar o segmento de rodapé da tabela.

- Não é obrigatório;
- Quando especificado, deve vir depois dos elementos **\<caption\>**, **\<colgroup\>**, **\<thead\>** e **\<tbody\>**.

```
<table>
    ...
    <tfoot>
        <tr>
            <td colspan="2">Relação de estados</td>
        </tr>
    </tfoot>
</table>
```

## SEGMENTOS DE COLUNAS

### COLGROUP E COL

Podemos definir um grupo de colunas utilizando a tag **\<colgroup\>**. Isso é útil para especificar regras de estilos para um grupo de colunas sem a necessidade de repetir o estilo para cada célula presente nessas colunas.

- Se o atributo **_span_** for especificado a tag não pode conter filhos, caso contrário o elemento pode conter zero ou mais elementos **\<col\>**;
- Deve vir depois do elemento **\<caption\>** e antes de qualquer **\<thead\>**, **\<tbody\>**, **\<tfoot\>** ou **\<tr\>**.

O parâmetro aceito é:

1. **_span_**: Define a quantidade de colunas.

```
<table>
    ...
    <colgroup span="3"/>
    ...
</table>
```

Já a tag **\<col\>** serve para especificar uma ou mais colunas dentro de um **\<colgroup\>**.

O parâmetro aceito é:

1. **_span_**: Define a quantidade de colunas.

```
<table>
    ...
    <colgroup>
        <col span="2"/>
        <col>
    </colgroup>
    ...
</table>
```

#### Propriedades CSS permitidas:

1. **_border_**: Define a borda para a coluna (somente se a propriedade **border-collapse** da tabela estiver definida como **collapse**).
2. **_background_**: Define o background para a coluna (apenas se a **linha** e a **célula** tiverem fundos transparentes).
3. **_width_**: Define uma largura mínima para a coluna.
4. **_visibility_**: Se estiver definida como **collapse**, a coluna não será renderizada. (não suportada no chrome)
