# Bot de Tickets para Discord

Bot de tickets em português, usando Discord.js v14 e Node.js 18.17+.

## Recursos
- `/painel-ticket` envia o painel (exige permissão Gerenciar Servidor).
- Botão Abrir Ticket cria canal privado.
- Cada usuário só pode ter um ticket aberto.
- O canal é acessível ao usuário, cargo de suporte e bot.
- Fechar Ticket pede confirmação e apaga o canal após 5 segundos.

## Configurar o bot
1. Crie uma aplicação em https://discord.com/developers/applications e adicione um bot.
2. Copie o token na seção Bot. Não compartilhe esse token.
3. Em OAuth2 > URL Generator, selecione `bot` e `applications.commands`; convide o bot ao servidor.
4. Dê ao bot as permissões Ver canais, Enviar mensagens, Ler histórico, Inserir links e Gerenciar canais.
5. Crie uma categoria de tickets e um cargo de suporte.
6. Ative Modo Desenvolvedor no Discord e copie os IDs da aplicação, servidor, cargo e categoria.

## Variáveis de ambiente
Copie `.env.example` para `.env` e preencha:
- `DISCORD_TOKEN`: token do bot
- `CLIENT_ID`: ID da aplicação
- `GUILD_ID`: ID do servidor
- `STAFF_ROLE_ID`: ID do cargo de suporte
- `TICKET_CATEGORY_ID`: ID da categoria de tickets

Nunca envie `.env` ao GitHub. Envie somente `.env.example`, que não contém segredos.

## Rodar localmente
Com Node.js 18.17+:
```bash
npm install
npm run deploy
npm start
```
`npm run deploy` registra `/painel-ticket` no servidor definido por `GUILD_ID`.

## Hospedar no Render
1. Envie todos os arquivos ao GitHub mantendo `package.json` na raiz e a pasta `src`.
2. No Render, crie um **Background Worker** conectado ao repositório.
3. Build Command: `npm install`
4. Start Command: `npm start`
5. Em Environment Variables, adicione as cinco variáveis acima.
6. Para registrar o comando slash, execute `npm run deploy` em um ambiente com as mesmas variáveis. Depois mantenha o serviço principal com `npm start`.

A disponibilidade contínua depende do plano e das condições atuais do serviço de hospedagem.

## Problemas comuns
- Bot offline: confira o token e os logs.
- Comando não aparece: confira `CLIENT_ID` e `GUILD_ID` e rode `npm run deploy`.
- Não cria canal: confira os IDs da categoria/cargo e a permissão Gerenciar Canais.
