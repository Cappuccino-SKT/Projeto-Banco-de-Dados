# Sistema de Gerenciamento de Cidades, Produção e Comércio de um Mundo de Jogo

**Aluno:** [SEU NOME COMPLETO]
**Disciplina:** Banco de Dados — Prof. Wendel Góes — UTFPR Câmpus Apucarana
**Trabalho Final — Parte A**

## DESCRIÇÃO DO SISTEMA

O sistema proposto armazena e controla os dados do mundo de um jogo 2D de gestão e RPG que está sendo desenvolvido pelo autor. Nesse mundo existem diversas cidades, cada uma com seus habitantes, suas oficinas e seus mercados, e a economia funciona de verdade: os habitantes trabalham, as construções produzem itens a partir de receitas, os itens ficam guardados em estoque e depois são vendidos. O banco de dados precisa guardar quem vive em cada cidade, onde cada um trabalha, o que cada construção produz e tem em estoque, e todas as vendas realizadas.

O mundo é dividido entre seis facções: Guerreira, Arcana, Autoritária, Religiosa, Tecnocrata e Escravista. Cada facção recebe um código próprio, e para cada uma é necessário saber o nome, a cultura, a forma de governo e o nome do seu líder. Cada facção controla no mínimo uma cidade, e cada cidade pertence a uma única facção.

Cada cidade recebe um código e possui um nome, um nível (de 1 a 5, que aumenta conforme a população cresce) e uma especialidade, como "cidade mineira", "celeiro" ou "cidade das oficinas".

O mundo possui aproximadamente 2.000 habitantes. Cada habitante recebe um código, e é necessário saber seu nome, seu sexo, sua idade (em anos do jogo) e quanto dinheiro ele possui guardado, em moedas. Cada habitante mora em uma única cidade, e uma cidade pode ter muitos habitantes. Todo habitante pertence a uma única classe social. As classes sociais são Escravo, Civil, Rico, Nobre e Realeza; para cada classe é guardado um código, o nome e a felicidade base dos seus membros. Em certos momentos, uma classe pode não ter nenhum habitante.

As construções do mundo são de vários tipos, como Fazenda, Posto de Coleta, Cozinheiro, Carpinteiro, Pedreira, Mercado e Templo. Para cada tipo de construção é necessário saber o código, o nome, o tipo de trabalho realizado nela (Braçal, Manufaturado ou Especialista) e o salário pago por hora de trabalho. Cada construção existente recebe um código e possui um nome e um nível; ela fica em uma única cidade e é de um único tipo. Uma construção pode ter um dono, que é um habitante; construções públicas, como o Mercado e o Templo, não têm dono. Um habitante pode ser dono de várias construções. Além disso, cada habitante trabalha em no máximo uma construção (crianças e desempregados não trabalham em nenhuma), e uma construção pode ter vários trabalhadores.

Os produtos do jogo são chamados de itens. Cada item recebe um código, e é necessário saber seu nome, sua categoria (matéria-prima ou bem de consumo), seu tier (de 0 a 3, que indica o quanto ele é avançado), seu peso e seu preço base. Os itens são produzidos por meio de receitas. Cada receita recebe um código e possui o tamanho do lote (quantas unidades ela produz de cada vez), as horas de trabalho necessárias e o nível mínimo da construção. Cada receita produz um único item e só pode ser feita em um tipo de construção. Uma receita pode usar vários itens como insumo, e para cada insumo é preciso saber a quantidade usada. Por exemplo, a receita do Pão é feita no Cozinheiro e usa 2 Grãos e 1 Água para produzir 4 Pães em 4 horas. As receitas de coleta, como a do Grão e a da Tora, não usam nenhum insumo. Um mesmo item pode ser insumo de várias receitas.

Cada construção possui um estoque, onde guarda vários itens; para cada item guardado é necessário saber a quantidade. Um mesmo item pode estar guardado em várias construções.

Por fim, é preciso controlar as vendas. Cada venda recebe um número e possui a data em que aconteceu, no calendário do jogo: o dia, a estação e o ano (o ano do jogo tem 4 estações de 16 dias cada). Cada venda é feita por uma única construção, a vendedora, para um único habitante, o comprador. Uma venda pode conter vários itens, e para cada item vendido é necessário saber a quantidade e o preço unitário cobrado, que pode ser diferente do preço base, pois os preços mudam conforme a oferta e a procura. Com isso, deseja-se saber, por exemplo, quais oficinas vendem mais, quais habitantes estão sem trabalho e quais itens estão faltando no estoque de cada cidade.

## DIAGRAMA ENTIDADE-RELACIONAMENTO (DER)

[INSERIR AQUI A IMAGEM DO DER FEITO NO BRMODELO]
