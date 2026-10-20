# Quiz OmniVerse — Desafio dos 12 Temas

Jogo de perguntas e respostas responsivo para desktop e dispositivos móveis.

## Arquivos

- `index.html`: interface e lógica do jogo.
- `questions.json`: banco de dados oficial em JSON puro.
- `questions.js`: espelho do mesmo banco, carregado pela página para permitir abertura local por duplo clique (`file://`).

## Banco de perguntas

A base inicial contém **1.200 perguntas**, distribuídas em 12 temas com 100 perguntas por tema: Ciência, História, Tecnologia, Geografia, Português, Biologia, Física, Química, Matemática, Astronomia, Cinema e Mundo Geek.

Cada pergunta tem `id`, `theme`, `themeName`, `difficulty`, `question`, quatro `options`, `answer` (índice de 0 a 3) e `explanation`.

## Executar

Abra `index.html` diretamente no navegador ou publique os três arquivos em uma hospedagem estática. O Tailwind CSS e a fonte Inter são carregados de CDNs, portanto a estilização externa requer conexão com a internet.

## Atualizar a base

Use a aba **Base JSON** do jogo para importar um `questions.json` ou baixar a base ativa. A edição pela interface é armazenada localmente no navegador e o botão de exportação baixa um novo arquivo; para publicar as alterações para todos, atualize os arquivos do repositório.

Para editar manualmente, preserve o formato JSON e os campos das perguntas. Ao publicar em servidor HTTP/HTTPS, o jogo tenta carregar `./questions.json`; ao abrir via `file://`, utiliza `questions.js` como fallback.
