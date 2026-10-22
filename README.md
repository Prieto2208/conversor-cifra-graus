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

Aba de estudo com as 12 escalas maiores (escritas pela teoria: F# maior tem E#, Db maior tem Gb), o grau em cima de cada nota, a armadura e o relativo menor de cada tom. Campo maior ou menor (escala menor natural, com o relativo maior ao lado), mostrando as notas ou os acordes do campo harmônico (maior: 1, 4 e 5 maiores; 2, 3 e 6 menores; 7 diminuto. Menor: 1, 4 e 5 menores; 3, 6 e 7 maiores; 2 diminuto). Ordem pelas notas, ciclo das quintas, ciclo das quartas, terças maiores ou terças menores/sextas. Tocar num bloco toca a nota ou o acorde (som gerado no navegador).

## Mudar de tom

Para passar de uma música para a próxima, em outro tom, sem parar a banda. Você escolhe o tom e o acorde em que a música atual termina, e o tom e o acorde em que a próxima começa (ex.: música em C que termina no G; a próxima, em F, começa no Bb). O site liga esses dois acordes: pelo 2-5 do primeiro acorde (G → Cm7 → F7 → Bb), pelo dominante dele (G → F7 → Bb), pelo ciclo das quartas (G → C7 → F7 → Bb) ou passando pela tônica nova (G → C7 → F → Bb). Mostra também truques de ligação (o G vira Gm e você já está no campo de F), a nota de ligação e permite ouvir cada caminho.

**Tocar no tempo:** em cada caminho, toca a transição como numa música de verdade: metrônomo em 4/4 (65 bpm por padrão, de 40 a 160), 1 compasso de contagem, 2 compassos do acorde final da música atual, a passagem (1 ou 2 compassos por acorde) e 2 compassos do primeiro acorde da próxima. O pad do tom fica de fundo no tom da música atual (tônica, quinta e oitava) e passa para o tom novo num fade longo (cerca de 1 compasso) em volta do começo da próxima música; o piano toca os acordes no 1º tempo. Dá para ligar e desligar metrônomo, pad e piano. A tela mostra o tempo do compasso e acende o acorde que está soando.

## Treino

- Perguntas: grau de uma nota, nota de um grau e acordes do campo harmônico, com placar.
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
