# Guia do DER (para desenhar no brModelo)

Tudo o que vai no diagrama, já tirado do texto da Parte A. Você só precisa desenhar.

## 1. Os símbolos do DER

| Símbolo | O que é | No nosso sistema |
|---|---|---|
| Retângulo | **Entidade**: uma "coisa" que guardamos | HABITANTE, CIDADE, ITEM... |
| Losango | **Relacionamento**: liga duas entidades | MORA, TRABALHA, VENDE... |
| Bolinha vazia | **Atributo**: um dado da entidade | nome, idade, peso... |
| Bolinha preenchida | **Identificador** (vira a chave primária) | cod_habitante, cod_item... |
| (min,max) na linha | **Cardinalidade** | (0,n), (1,1), (0,1)... |

**Como ler a cardinalidade (padrão do brModelo):** o número escrito **perto de uma entidade** diz quantas vezes ela aparece para **um** elemento da entidade do outro lado.

Exemplo: `FACCAO (1,1) — CONTROLA — (1,n) CIDADE`
- O `(1,n)` perto de CIDADE: uma facção controla de 1 a muitas cidades.
- O `(1,1)` perto de FACCAO: uma cidade pertence a exatamente 1 facção.

## 2. As 9 entidades e seus atributos

O primeiro atributo de cada uma é o **identificador** (bolinha preenchida).

| Entidade | Atributos |
|---|---|
| FACCAO | **cod_faccao**, nome, cultura, forma_governo, lider |
| CIDADE | **cod_cidade**, nome, nivel, especialidade |
| CLASSE_SOCIAL | **cod_classe**, nome, felicidade_base |
| HABITANTE | **cod_habitante**, nome, sexo, idade, dinheiro |
| TIPO_CONSTRUCAO | **cod_tipo**, nome, tipo_trabalho, salario_hora |
| CONSTRUCAO | **cod_construcao**, nome, nivel |
| ITEM | **cod_item**, nome, categoria, tier, peso, preco_base |
| RECEITA | **cod_receita**, lote, horas, nivel_minimo |
| VENDA | **num_venda**, dia, estacao, ano |

São 9 entidades no diagrama. ESTOQUE, INSUMO e ITEM_VENDA não são retângulos: são relacionamentos N:N com atributo (veja abaixo). Eles só viram tabelas na Parte B.

## 3. Os 14 relacionamentos

| # | Entidade A (card. perto de A) | Relacionamento | Entidade B (card. perto de B) | Atributos do losango |
|---|---|---|---|---|
| 1 | FACCAO **(1,1)** | CONTROLA | CIDADE **(1,n)** | — |
| 2 | CIDADE **(1,1)** | MORA | HABITANTE **(0,n)** | — |
| 3 | CLASSE_SOCIAL **(1,1)** | PERTENCE | HABITANTE **(0,n)** | — |
| 4 | CIDADE **(1,1)** | LOCALIZA | CONSTRUCAO **(0,n)** | — |
| 5 | TIPO_CONSTRUCAO **(1,1)** | CLASSIFICA | CONSTRUCAO **(0,n)** | — |
| 6 | HABITANTE **(0,1)** | POSSUI | CONSTRUCAO **(0,n)** | — |
| 7 | HABITANTE **(0,n)** | TRABALHA | CONSTRUCAO **(0,1)** | — |
| 8 | TIPO_CONSTRUCAO **(1,1)** | REALIZA | RECEITA **(0,n)** | — |
| 9 | ITEM **(1,1)** | PRODUZ | RECEITA **(0,n)** | — |
| 10 | RECEITA **(0,n)** | USA (insumo) | ITEM **(0,n)** | quantidade |
| 11 | CONSTRUCAO **(0,n)** | ARMAZENA (estoque) | ITEM **(0,n)** | quantidade |
| 12 | HABITANTE **(1,1)** | COMPRA | VENDA **(0,n)** | — |
| 13 | CONSTRUCAO **(1,1)** | VENDE | VENDA **(0,n)** | — |
| 14 | VENDA **(0,n)** | CONTEM | ITEM **(1,n)** | quantidade, preco_unitario |

Como ler algumas delas:
- **6 (POSSUI):** uma construção tem **no máximo 1 dono** (0,1: o Mercado e o Templo não têm). Um habitante pode ter **várias** construções (0,n).
- **7 (TRABALHA):** um habitante trabalha em **no máximo 1** construção (0,1). Uma construção tem **vários** trabalhadores (0,n).
- **6 e 7 ligam as mesmas duas entidades** com sentidos diferentes. Isso é normal no DER e mostra que o modelo foi pensado.
- **14 (CONTEM):** uma venda tem **pelo menos 1 item** (1,n). Um item pode estar em **várias** vendas (0,n).

## 4. Passo a passo no brModelo

1. Baixe o brModelo 3 no link do professor (sourceforge.net/projects/brmodelo). Ele precisa do Java, e o Java 21 já está instalado no seu PC.
2. Crie um **Modelo Conceitual** novo.
3. Desenhe as 9 entidades (retângulos). Sugestão de posição para as linhas não se cruzarem:
   - **Em cima:** FACCAO, CIDADE e CLASSE_SOCIAL.
   - **No meio:** HABITANTE à esquerda, CONSTRUCAO no centro e TIPO_CONSTRUCAO à direita.
   - **Embaixo:** VENDA à esquerda, ITEM no centro e RECEITA à direita.
4. Ponha os atributos em cada entidade e marque o primeiro como **identificador**.
5. Crie os 14 losangos e ligue cada um às suas duas entidades.
6. Clique em cada linha e escolha a cardinalidade da tabela acima.
7. Nos losangos 10, 11 e 14, adicione os atributos (quantidade, preco_unitario).
8. Salve o arquivo do brModelo e exporte o diagrama como imagem (se não achar a opção, um print da tela também serve).
9. Cole a imagem no `Trabalho_Final_Parte_A.docx`, no lugar de "[INSERIR AQUI...]", escreva o seu nome e salve como **PDF** (no Word: Arquivo → Salvar como → PDF).

## 5. Banco escolhido para a Parte B

**MySQL**, com o **MySQL Workbench**: é o mais usado em tutoriais em português, e o Workbench desenha sozinho o diagrama do modelo lógico (a Figura 4 da Parte B) a partir das tabelas criadas.
