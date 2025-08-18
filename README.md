# my-react-app

Este é um projeto full-stack que inclui um frontend em React, um backend em Python e um banco de dados PostgreSQL, tudo orquestrado com Docker Compose.

## Visão Geral

O projeto está estruturado para separar as preocupações do frontend e do backend em seus próprios diretórios e contêineres Docker.

-   `frontend/`: Contém a aplicação React criada com Create React App.
-   `backend/`: Contém a aplicação Python.
-   `docker-compose.yml`: Define os serviços, redes e volumes para a aplicação.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte instalado em sua máquina:
-   Docker
-   Docker Compose

## Como Iniciar

1.  **Clone o repositório:**
    ```bash
    git clone <URL_DO_SEU_REPOSITORIO>
    cd my-react-app
    ```

2.  **Inicie os contêineres:**
    Execute o seguinte comando na raiz do projeto para construir e iniciar os contêineres em modo detached (`-d`):
    ```bash
    docker-compose up --build -d
    ```

3.  **Acesse os serviços:**
    -   **Frontend (React App):** http://localhost:3000
    -   **Backend (Python API):** http://localhost:5000
    -   **Database (PostgreSQL):** Acessível na porta `5432` da sua máquina local.

4.  **Para parar os contêineres:**
    ```bash
    docker-compose down
    ```

## Serviços

### Frontend

-   **Tecnologia:** React (Create React App)
-   **Contêiner:** `frontend`
-   **Porta:** `3000:3000`
-   **Notas:** O código-fonte é montado no volume `./frontend:/app`, permitindo o hot-reloading durante o desenvolvimento.

### Backend

-   **Tecnologia:** Python 3.13
-   **Contêiner:** `backend`
-   **Porta:** `5000:5000`
-   **Notas:** O backend está configurado para se conectar ao banco de dados no serviço `db`. É altamente recomendado criar um arquivo `requirements.txt` para gerenciar as dependências Python.

### Banco de Dados

-   **Tecnologia:** PostgreSQL 17.6
-   **Contêiner:** `postgres_db`
-   **Porta:** `5432:5432`
-   **Credenciais:**
    -   **Usuário:** `postgres`
    -   **Senha:** `postgres`
    -   **Banco de Dados:** `my_db`
-   **Persistência:** Os dados do banco de dados são persistidos no volume nomeado `db_data`.

## Desenvolvimento

Para desenvolvimento local fora do Docker, você pode executar os serviços individualmente.

### Frontend

Dentro do diretório `frontend`:
```bash
npm install
npm start
```

### Backend

Dentro do diretório `backend`, é recomendado criar um ambiente virtual:
```bash
python -m venv venv
source venv/bin/activate  # No Windows: venv\Scripts\activate
pip install -r requirements.txt # Crie um requirements.txt com suas dependências
# Inicie seu servidor Python (ex: flask run, uvicorn main:app --reload)
```