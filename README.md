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

## Interface adaptada e Base JSON restrita

A interface agora adapta a navegação ao celular com barra inferior, áreas de toque maiores, respeito à área segura do iPhone e suporte ao zoom do navegador. A tela de perguntas mantém os controles utilizáveis em telas estreitas e respeita a preferência do sistema por movimento reduzido.

O acesso visual à tela **Base JSON** exige autenticação com GitHub e valida a identidade do proprietário pelo ID imutável da conta `omarioarquiteto` (`202185131`). Outros usuários podem jogar normalmente, mas a tela administrativa não é liberada.

### Configuração necessária no Firebase

A proteção usa Firebase Authentication no projeto `resolvei-c95d1`. Para habilitar o primeiro acesso administrativo:

1. No Firebase Console, abra **Authentication → Sign-in method** e habilite o provedor **GitHub**.
2. Registre ou selecione um OAuth App no GitHub. Configure a URL de callback indicada pelo Firebase; para este projeto, ela costuma ser `https://resolvei-c95d1.firebaseapp.com/__/auth/handler`.
3. Informe o Client ID e o Client Secret do OAuth App na configuração do provedor GitHub no Firebase.
4. Em **Authentication → Settings → Authorized domains**, confira se o domínio onde o jogo será executado está autorizado (por exemplo, `resolvei-utilidades.onrender.com` ou o domínio de hospedagem usado pelo jogo).
5. Abra o jogo pela URL HTTPS publicada e use **Proprietário** na navegação. O botão **Base JSON** será exibido somente após a validação da conta `omarioarquiteto`.

A autenticação administrativa é mantida em uma instância Firebase separada para não encerrar a sessão comum do Resolvei. Abrir o HTML por `file://` continua permitindo jogar, mas o login administrativo requer uma origem web autorizada.

**Nota de segurança:** este repositório é público e a interface é estática. O controle protege a navegação normal da tela administrativa, mas não torna o conteúdo de `questions.json` privado nem substitui autorização no servidor para operações sensíveis. Para proteger também o arquivo JSON ou impedir alterações via ferramentas de desenvolvedor, seria necessário hospedar a administração atrás de um endpoint autenticado no servidor ou tornar o repositório privado.

