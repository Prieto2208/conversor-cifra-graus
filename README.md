# Conversor de cifra para graus

Ferramenta web que converte cifras (acordes) em graus numéricos, mantendo a letra e o alinhamento dos acordes sobre as sílabas.

## Funcionalidades

- Detecta automaticamente o tom a partir de uma linha `Tom: Cm`
- Tons maiores e menores, com opção de numerar o tom menor pelo relativo maior
- Mostra só o grau do acorde no campo harmônico: em C, `Am` vira `6`, `Dm7` vira `2` e o baixo invertido é mantido (`G/B` vira `5/7`)
- Marca a qualidade só quando o acorde foge do campo (empréstimo modal ou acorde de outra escala): em C, `Fm` vira `4m`, `E7` vira `3M` e `Bb` vira `b7M`
- Mantém os graus na mesma coluna dos acordes originais
- Permite editar os graus à mão (botão Editar); a edição vale para o Word, o Copiar e as cifras salvas
- Exporta o resultado para Word (.docx), pedindo o nome da música para nomear o arquivo, ou copia para a área de transferência
- Registro de cifras (com login): salvar, buscar, abrir para editar e excluir cifras, guardadas no Supabase
- A conversão roda no navegador; só as cifras que você salva vão para o banco

## Como usar

Abra a página, cole a cifra na caixa da esquerda e copie ou baixe o resultado da direita.
Ao colar no Word, use uma fonte monoespaçada (Consolas ou Courier New) para manter o alinhamento.

## Registro de cifras

- Login com uma conta fixa do grupo; não há cadastro (desligado no Supabase).
- O usuário sem "@" vira e-mail no domínio do site: `meta` = `meta@conversor-cifra-graus.vercel.app`.
- Tabela `cifras` no Supabase com RLS: só usuários logados leem e alteram.
- Para trocar a senha ou criar outra conta: Supabase → Authentication → Users.

## Tecnologias

- HTML, CSS e JavaScript puro
- [docx](https://www.npmjs.com/package/docx) para gerar o arquivo Word no navegador
- [Supabase](https://supabase.com) para login e banco de dados do registro de cifras

## Rodando localmente

Basta abrir o `index.html` no navegador. Não há etapa de build.
