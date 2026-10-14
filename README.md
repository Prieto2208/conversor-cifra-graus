# Conversor de cifra para graus

Ferramenta web que converte cifras (acordes) em graus numéricos, mantendo a letra e o alinhamento dos acordes sobre as sílabas.

## Funcionalidades

- Detecta automaticamente o tom a partir de uma linha `Tom: Cm`
- Tons maiores e menores, com opção de numerar o tom menor pelo relativo maior
- Dois formatos: parênteses (`1(7)`, `6m(9)`) ou junto (`17`, `6m9`)
- Mantém os graus na mesma coluna dos acordes originais
- Exporta o resultado para Word (.docx) ou copia para a área de transferência
- Tudo roda no navegador: nenhum texto é enviado para servidor

## Como usar

Abra a página, cole a cifra na caixa da esquerda e copie ou baixe o resultado da direita.
Ao colar no Word, use uma fonte monoespaçada (Consolas ou Courier New) para manter o alinhamento.

## Tecnologias

- HTML, CSS e JavaScript puro
- [docx](https://www.npmjs.com/package/docx) para gerar o arquivo Word no navegador

## Rodando localmente

Basta abrir o `index.html` no navegador. Não há etapa de build.
