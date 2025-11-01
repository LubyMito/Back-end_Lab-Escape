# 🧪 Lab Escape - Backend

Backend do **Lab Escape**, um jogo *top-down* desenvolvido na **Godot Engine**, utilizando **Nakama** para o multiplayer e lógica de backend, e **CockroachDB** como banco de dados.  

Este backend gerencia:
- Autenticação de jogadores  
- Persistência de dados e pontuações  
- Matchmaking e salas de multiplayer  
- Leaderboards globais  

---

## ⚙️ Tecnologias

| Tecnologia     | Função |
|----------------|--------|
| **Godot Engine** | Cliente do jogo |
| **Nakama** | Servidor de backend para jogos em tempo real |
| **CockroachDB** | Banco de dados escalável e distribuído |
| **Lua / Go / TypeScript** | Scripts de servidor para o Nakama |

---

## 🚀 Instalação e Configuração

### 🧩 Nakama

Baixe e rode o Nakama via Docker:

```bash
docker run --name lab-escape-nakama -p 7350:7350 -p 7351:7351 \
  -e "DATABASE_URL=postgresql://root@localhost:26257/lab_escape?sslmode=disable" \
  heroiclabs/nakama
````

---

### 🗄️ CockroachDB

Instale e rode o CockroachDB:

```bash
cockroach start-single-node --insecure --listen-addr=localhost:26257
cockroach sql --insecure
```

Crie o banco de dados:

```sql
CREATE DATABASE lab_escape;
```

---

### 📜 Scripts do Nakama

Adicione os scripts **Lua**, **Go** ou **TypeScript** do Nakama na pasta `modules/` e configure no arquivo `nakama.yml`.

Esses scripts controlam:

* Autenticação customizada
* Persistência de dados
* Leaderboards
* Eventos de multiplayer

---

## 🔌 Endpoints e Rotas

Com o Nakama, você interage principalmente via **RPCs** e **WebSocket**.

### 🧠 RPCs (exemplos)

| Endpoint              | Descrição                         |
| --------------------- | --------------------------------- |
| `rpc.register_user`   | Registrar novo jogador            |
| `rpc.submit_score`    | Enviar pontuação para leaderboard |
| `rpc.get_leaderboard` | Obter ranking global              |

### 🌐 WebSocket / Real-time

* Conecte-se via **Godot Nakama SDK**
* Eventos de sala: `join`, `leave`, `state_update`

---

## 📁 Estrutura do Projeto

```
lab-escape-backend/
├── modules/               # Scripts do Nakama (Lua/Go/TS)
├── docker/                # Dockerfiles / configs
├── nakama.yml             # Configuração do servidor Nakama
├── cockroachdb/           # Scripts e migrações do banco
└── README.md
```

---

## 🤝 Contribuição

1. Faça um **fork** do projeto
2. Crie uma **branch**:

   ```bash
   git checkout -b feature/nome-da-feature
   ```
3. Faça o **commit** das suas alterações:

   ```bash
   git commit -m "Descrição da feature"
   ```
4. Faça o **push** para a branch:

   ```bash
   git push origin feature/nome-da-feature
   ```
5. Abra um **Pull Request**

---

📜 **Licença:** Este projeto é distribuído sob a licença MIT.

```

```
