Lab Escape - Backend

Backend do Lab Escape, um jogo top-down desenvolvido na Godot, usando Nakama para multiplayer e lógica de backend, e CockroachDB como banco de dados. Este backend gerencia autenticação de jogadores, persistência de dados e pontuações, matchmaking, salas de multiplayer e leaderboards globais.

Tecnologias

Godot Engine → Cliente do jogo.

Nakama → Servidor de backend de jogos em tempo real.

CockroachDB → Banco de dados escalável e distribuído.

Lua / Go / TypeScript → Scripts de servidor para Nakama.

Instalação e Configuração
Nakama

Baixe e rode o Nakama via Docker:

docker run --name lab-escape-nakama -p 7350:7350 -p 7351:7351 \
  -e "DATABASE_URL=postgresql://root@localhost:26257/lab_escape?sslmode=disable" \
  heroiclabs/nakama

CockroachDB

Instale e rode o CockroachDB:

cockroach start-single-node --insecure --listen-addr=localhost:26257
cockroach sql --insecure


Crie o banco de dados:

CREATE DATABASE lab_escape;

Scripts do Nakama

Adicione os scripts Lua/Go/TS do Nakama na pasta modules/ e configure no nakama.yml. Esses scripts controlam autenticação customizada, persistência de dados, leaderboards e eventos de multiplayer.

Endpoints e Rotas

Com Nakama, você interage principalmente via RPCs e WebSocket:

RPCs (exemplo)

rpc.register_user → Registrar novo jogador.

rpc.submit_score → Enviar pontuação para leaderboard.

rpc.get_leaderboard → Obter ranking global.

WebSocket / Real-time

Conectar via Godot Nakama SDK.

Eventos de sala: join, leave, state_update.

Estrutura do Projeto
lab-escape-backend/
│
├── modules/               # Scripts do Nakama (Lua/Go/TS)
├── docker/                # Dockerfiles / configs
├── nakama.yml             # Configuração do servidor Nakama
├── cockroachdb/           # Scripts e migrações do banco
└── README.md

Contribuição

Faça um fork do projeto

Crie uma branch (git checkout -b feature/nome)

Commit suas alterações (git commit -m "Descrição da feature")

Push para a branch (git push origin feature/nome)

Abra um Pull Request

Licença

MIT License – veja LICENSE
.
