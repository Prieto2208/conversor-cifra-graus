# Conversor de cifra para graus

Ferramenta web que converte cifras (acordes) em graus numéricos, mantendo a letra e o alinhamento dos acordes sobre as sílabas.

## Funcionalidades

- Detecta automaticamente o tom a partir de uma linha `Tom: Cm`
- Tom + Modo formam o tom da música e a cifra original acompanha: trocar transpõe acordes, baixos e a linha `Tom:`, mantendo os mesmos graus. Tons relativos (Am e C) mantêm os acordes. Dá para desmarcar "Transpor acordes" para só corrigir o tom
- Tons maiores e menores, com opção de numerar o tom menor pelo relativo maior
- Mostra só o grau do acorde no campo harmônico: em C, `Am` vira `6`, `Dm7` vira `2` e o baixo invertido é mantido (`G/B` vira `5/7`)
- Marca a qualidade só quando o acorde foge do campo (empréstimo modal ou acorde de outra escala): em C, `Fm` vira `4m`, `E7` vira `3M` e `Bb` vira `b7M`
- Mantém os graus na mesma coluna dos acordes originais
- Permite editar os graus à mão (botão Editar); a edição vale para o PDF, o Copiar e as cifras salvas
- Compartilha o resultado em PDF (no celular abre o menu de compartilhar, com WhatsApp; no computador baixa o arquivo), pedindo o nome da música, ou copia para a área de transferência
- Registro de cifras (com login): salvar, buscar, abrir para editar e excluir cifras, guardadas no Supabase
- A conversão roda no navegador; só as cifras que você salva vão para o banco

## Mapa de graus

Aba de estudo com as 12 escalas maiores (escritas pela teoria: F# maior tem E#, Db maior tem Gb), o grau em cima de cada nota, a armadura e o relativo menor de cada tom. Três modos: notas, acordes do campo harmônico (1, 4 e 5 maiores; 2, 3 e 6 menores; 7 diminuto) e fora do campo (empréstimos b3M, 4m, b6M, b7M e dominantes secundários 2M, 3M, 6M). Ordem pelas notas, ciclo das quintas, ciclo das quartas, terças maiores ou terças menores/sextas. Tocar num bloco toca a nota ou o acorde (som gerado no navegador).

## Treino

- Perguntas: grau de uma nota, nota de um grau, acordes do campo e de fora do campo, com placar.
- Ouvido (o site toca o 1 do tom como referência):
  - Grau do acorde / grau da nota: você responde o grau que ouviu.
  - Sobe ou desce: duas notas; você diz se a segunda subiu, desceu ou repetiu, e vê de qual grau para qual foi.
  - Ditado de melodia: 3 notas andando quase sempre de grau em grau; você responde os graus em ordem e vê o desenho (ex.: 3 ↑ 4 ↓ 2).
  - Próximo acorde: toca o começo de uma progressão comum (1-5-6-4, 2-5-1, 6-4-1-5...) e você adivinha o próximo acorde.

## Como usar

Abra a página, cole a cifra na caixa da esquerda e copie ou baixe o resultado da direita.
Ao colar em outro editor, use uma fonte monoespaçada (Consolas ou Courier New) para manter o alinhamento.

## Registro de cifras

- Login com uma conta fixa do grupo; não há cadastro (desligado no Supabase).
- O usuário sem "@" vira e-mail no domínio do site: `meta` = `meta@conversor-cifra-graus.vercel.app`.
- Tabela `cifras` no Supabase com RLS: só usuários logados leem e alteram.
- Para trocar a senha ou criar outra conta: Supabase → Authentication → Users.

## Tecnologias

- HTML, CSS e JavaScript puro
- [jsPDF](https://github.com/parallax/jsPDF) para gerar o PDF no navegador
- [Supabase](https://supabase.com) para login e banco de dados do registro de cifras

## Rodando localmente

Basta abrir o `index.html` no navegador. Não há etapa de build.
