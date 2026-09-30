# PlantãoApp

Site institucional do **PlantãoApp**, um aplicativo para profissionais de saúde organizarem plantões, agenda e ganhos. A página apresenta as funcionalidades, os planos e os links para baixar o app.

## Visão geral

- Landing page responsiva com navegação por seções, menu para dispositivos móveis e animações ao rolar a página.
- Funcionalidades renderizadas dinamicamente a partir de uma lista no JavaScript.
- Apresentação dos planos Free e Premium e imagens das telas do aplicativo.
- Página de redefinição de senha acessada por link com token.

## Pré-requisitos

Não é necessário instalar dependências nem executar um processo de build. O site usa HTML, CSS e JavaScript nativos. A fonte Inter é carregada do Google Fonts.

## Executar localmente

Na pasta do projeto, inicie um servidor HTTP simples:

```powershell
py -m http.server 8000
```

Em macOS ou Linux, você também pode usar:

```bash
python3 -m http.server 8000
```

Abra [http://localhost:8000](http://localhost:8000) no navegador. Para encerrar o servidor, pressione `Ctrl+C` no terminal.

## Estrutura do projeto

| Arquivo ou pasta | Responsabilidade |
| --- | --- |
| `index.html` | Página principal e conteúdo das seções |
| `styles.css` | Estilos, layout responsivo e componentes visuais |
| `script.js` | Configurações do app, funcionalidades e interações da página |
| `reset-password.html` | Formulário e estados da redefinição de senha |
| `reset-password.js` | Validação do formulário e comunicação com a API de redefinição |
| `img/` | Capturas de tela usadas na página |

## Personalização

No início de `script.js`, edite o objeto `CONFIG` para atualizar o nome, a descrição, o e-mail de contato e os endereços das lojas e da assinatura. Os cards de funcionalidades são definidos no array `FEATURES`, no mesmo arquivo.

Os endereços `PLAYSTORE_LINK`, `APPSTORE_LINK` e `PREMIUM_LINK` estão atualmente como `#`; substitua-os pelos links válidos antes de publicar. As imagens referenciadas pela página ficam em `img/`.

## Redefinição de senha

A página `reset-password.html` espera receber um token na query string, por exemplo `reset-password.html?token=TOKEN`. Ao enviar o formulário, `reset-password.js` faz uma requisição `POST` para `/api/auth/reset-password`, enviando `{ "token": "...", "newPassword": "..." }`.

O endereço da API está definido em `API_BASE_URL`, no início de `reset-password.js`. Ajuste-o para o ambiente correto antes de publicar. A página precisa ser servida por HTTP ou HTTPS, e o servidor da API deve permitir as requisições de origem do site (CORS).

## Publicação

Como o projeto não requer build, publique os arquivos estáticos preservando a estrutura de pastas. Antes da publicação, confira os links de download e assinatura, a URL da API de redefinição e a disponibilidade das imagens e da fonte externa.
