# Template Full-Stack: React, Python, PostgreSQL e Docker

Este é um projeto modelo (boilerplate) projetado para acelerar o desenvolvimento de aplicações web full-stack. Ele fornece uma estrutura pré-configurada com um frontend em **React**, um backend em **Python**, um banco de dados **PostgreSQL**, todos orquestrados com **Docker e Docker Compose**.

## ✨ Recursos

-   **🚀 Início Rápido:** Clone o repositório e inicie todo o ambiente de desenvolvimento com um único comando.
-   **🐳 Containerizado:** Frontend, backend e banco de dados rodam em contêineres Docker isolados.
-   **💻 Hot-Reloading:** As alterações no código do frontend são refletidas instantaneamente sem a necessidade de reiniciar os contêineres.
-   **🔗 Pré-configurado:** Conexão entre frontend, backend e banco de dados já estabelecida.
-   **🌱 Escalável:** Estrutura base sólida para construir projetos complexos.

## 📂 Estrutura do Projeto

O projeto é organizado de forma monorepo, separando claramente as responsabilidades:

```
.
├── backend/
│   ├── Dockerfile
│   └── requirements.txt
├── frontend/
│   ├── public/
│   ├── src/
│   ├── package.json
│   └── Dockerfile
├── .gitignore
├── docker-compose.yml
└── README.md
```

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte instalado em sua máquina:
-   Docker
-   Docker Compose

## 🚀 Como Usar este Template

1.  **Clone o repositório para sua máquina local:**
    ```bash
    git clone <URL_DESTE_REPOSITORIO> nome-do-seu-projeto
    cd nome-do-seu-projeto
    ```

2.  **Construa e inicie os contêineres:**
    Execute o comando a seguir na raiz do projeto. O Docker Compose irá construir as imagens e iniciar os serviços em background (`-d`).
    ```bash
    docker compose up --build -d
    ```

3.  **Pronto! Acesse os serviços:**
    -   **Frontend (React App):** http://localhost:3000
    -   **Backend (Python API):** http://localhost:5000
    -   **Database (PostgreSQL):** Acessível na porta `5432` da sua máquina local.

4.  **Para parar todos os serviços:**
    ```bash
    docker compose down
    ```

## 🛠️ Serviços Docker

### Frontend (`frontend`)

-   **Tecnologia:** React (Node.js)
-   **Porta:** `3000:3000`
-   **Notas:** O código-fonte em `./frontend` é montado diretamente no contêiner, permitindo hot-reloading.

### Backend (`backend`)

-   **Tecnologia:** Python 3.13
-   **Porta:** `5000:5000`
-   **Notas:** O código-fonte em `./backend` também é montado para desenvolvimento ágil. A variável de ambiente `DATABASE_URL` já está configurada para se conectar ao serviço `db`.

### Banco de Dados (`db`)

-   **Tecnologia:** PostgreSQL 17.6
-   **Porta:** `5432:5432`
-   **Credenciais Padrão:**
    -   **Usuário:** `postgres`
    -   **Senha:** `postgres`
    -   **Banco de Dados:** `my_db`
-   **Persistência:** Os dados são salvos no volume `db_data` para sobreviver a reinicializações dos contêineres.

## 🔧 Desenvolvimento e Customização

### Backend (Python)

1.  **Adicione dependências** ao arquivo `backend/requirements.txt`.
2.  **Escreva seu código** Python no diretório `backend/`.
3.  **Defina o comando de inicialização** no `backend/Dockerfile` para rodar sua API (ex: com Flask ou Uvicorn).
4.  Reinicie o serviço para aplicar as mudanças: `docker-compose up -d --build backend`.

### Frontend (React)

Você pode adicionar novas dependências normalmente. Execute os comandos **no seu terminal local**, dentro do diretório `frontend/`:

```bash
# Estando dentro do diretório my-react-app/frontend
npm install axios
```

O `package.json` será atualizado. Na próxima vez que você executar `docker-compose up --build`, as novas dependências serão instaladas na imagem Docker.
