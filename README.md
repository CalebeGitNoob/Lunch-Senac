# Sistema de Controle - Lanchonete Ennius Muniz (Senac-DF)

Sistema simples de controle de produtos para lanchonete, feito em **Python** com banco de dados **SQLite**. O programa roda no terminal e permite cadastrar e consultar produtos.

## Funcionalidades

- Cadastrar novos produtos (nome, preço e quantidade em estoque)
- Consultar todos os produtos salvos
- Dados guardados em um banco SQLite (`sistema.db`), que é criado automaticamente

## Requisitos

- Python 3.8 ou superior
- Nenhuma biblioteca externa (`sqlite3` e `os` já vêm com o Python)

## Como executar

1. Clone o repositório ou baixe os arquivos:

   ```bash
   git clone <URL-DO-REPOSITORIO>
   cd <NOME-DA-PASTA>
   ```

2. (Opcional) Insira 10 produtos de exemplo no banco:

   ```bash
   python popular_produtos.py
   ```

3. Rode o sistema:

   ```bash
   python lanchonete.py
   ```

> Os arquivos `lanchonete.py` e `popular_produtos.py` devem ficar na **mesma pasta**, pois o banco `sistema.db` é criado ao lado do arquivo que está sendo executado.

## Como usar

Ao iniciar, o menu principal aparece:

```
## Lanchonete Ennius Muniz - Senac-DF
=== SISTEMA DE CONTROLE (SQLite) ===
1. Cadastrar novos produtos
2. Consultar produtos salvos
3. Sair do sistema
```

| Opção | O que faz |
|---|---|
| 1 | Pede nome, preço e quantidade e salva o produto no banco. O preço aceita vírgula ou ponto (`6,50` ou `6.50`). |
| 2 | Lista todos os produtos cadastrados com nome, preço e estoque. |
| 3 | Encerra o programa e fecha a conexão com o banco. |

Exemplo da consulta:

```
------------------------------------------------------------
Produto: Coxinha              | Preço: R$     6.50 | Estoque: 40
Produto: Pão de queijo        | Preço: R$     4.00 | Estoque: 60
------------------------------------------------------------
```

## Estrutura do projeto

```
.
├── lanchonete.py          # Programa principal (menu, cadastro e consulta)
├── popular_produtos.py    # Script que insere 10 produtos de exemplo
├── sistema.db             # Banco SQLite (gerado automaticamente)
└── README.md
```

## Banco de dados

Tabela `produtos`:

| Coluna | Tipo | Descrição |
|---|---|---|
| nome | TEXT | Nome do produto |
| preco | REAL | Preço em reais |
| quantidade | INTEGER | Quantidade em estoque |

## Como o código funciona

1. Descobre a pasta do arquivo `.py` e conecta ao `sistema.db` nela.
2. Cria a tabela `produtos` caso ainda não exista.
3. `cadastrar_produto()` valida os dados digitados e faz o `INSERT`.
4. `consultar_produtos()` faz um `SELECT` e exibe os itens formatados.
5. `main()` mostra o menu em loop até o usuário escolher sair.

## Autor

Calebe Ribeiro da Cruz Vieira, curso Técnico em Desenvolvimento de Sistemas, Senac-DF.
