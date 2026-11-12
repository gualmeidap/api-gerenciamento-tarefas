[![English](https://img.shields.io/badge/English-0A66C2?style=for-the-badge)](README.md) [![Português](https://img.shields.io/badge/Portugu%C3%AAs-lightgrey?style=for-the-badge)](README.pt-BR.md)

# 📌 Task Management API (Flask + JWT)

A REST API built with Flask for task management, with user authentication using JWT (JSON Web Token).
Each user can sign up, log in and manage their own tasks (CRUD).

# 🚀 Stack

Python

Flask

Flask-SQLAlchemy

Flask-JWT-Extended

SQLite (local database)

# 📁 Project layout
<pre>
api-gerenciamento-tarefas/
└── instance/
    └── tarefas.db        # SQLite database (created automatically)
├── routes/
│   ├── auth_routes.py    # Authentication routes
│   └── task_routes.py    # Task routes
├── .gitattributes        # Git file attribute settings
├── .gitignore            # Files and directories ignored by Git
├── app.py                # Main Flask file
├── database.py           # Models and database connection
├── extensions.py         # Flask extension setup
├── README.md             # This file (English)
├── README.pt-BR.md       # Portuguese version
└── requirements.txt      # Project dependencies
</pre>
# ⚙️ Running the project
## 1. Clone the repository:
```bash
git clone https://github.com/gualmeidap/api-gerenciamento-tarefas.git

cd api-gerenciamento-tarefas
```

## 2. Create a virtual environment (optional but recommended):

```bash
python -m venv venv
```

### Activate it:

#### Linux/macOS:
```bash
source venv/bin/activate
```
#### Windows:
```bash
venv\Scripts\activate
```
## 3. Install the dependencies:
```bash
pip install -r requirements.txt
```
## 4. Run the application:
```bash
python app.py
```

# 🧪 Testing the API and expected responses with [Postman](https://www.postman.com/downloads/)

> The API's response messages (`msg`) are in Portuguese, exactly as the API returns them.

## 1. Register User

Method: POST

Endpoint: http://127.0.0.1:5000/register

#### Body (JSON):
```bash
{
  "username": "usuario1",
  "email": "usuario1@email.com",
  "password": "123456"
}
```

#### Expected response (201):
```bash 
{
  "msg": "Usuário registrado com sucesso"
}
```
## 2. Login User

Method: POST

Endpoint: http://127.0.0.1:5000/login

#### Body (JSON):
```bash
{
  "email": "usuario1@email.com",
  "password": "123456"
}
```
#### Expected response (200):
```bash
{
  "access_token": "<jwt_token_here>",
  "user": {
    "id": 1,
    "username": "usuario1",
    "email": "usuario1@email.com"
  }
}
```
📌 Note: take the token from `/login` and use it in the header of Create, List, Update and Delete.

## 3. Create Task

Method: POST

Endpoint: http://127.0.0.1:5000/tasks

#### Body (JSON):
```bash
{
  "title": "Estudar Flask",
  "description": "Finalizar projeto com autenticação"
}
```

#### Expected response (201 Created)
```bash
{
  "msg": "Tarefa criada com sucesso",
  "id": 1
}
```
📌 Note: keep the returned id, you will use it in the update/delete tests.

## 4. List Tasks

Method: GET

Endpoint: http://127.0.0.1:5000/tasks

Headers:

Authorization: Bearer <your_token>

#### Response (200):
```bash
[
  {
    "id": 1,
    "title": "Estudar Flask",
    "description": "Finalizar projeto com autenticação",
    "completed": false
  }
]
```
## 5. Update Task

Method: PUT

Endpoint: http://127.0.0.1:5000/tasks/<task_id>

#### Body (JSON):
```bash
{
  "title": "Estudar Flask atualizado",
  "description": "Atualizei a descrição",
  "completed": true
}
```
#### Expected response (200 OK)
```bash
{
  "msg": "Tarefa atualizada com sucesso"
}
```
## 6. Delete Task

Method: DELETE

Endpoint: http://127.0.0.1:5000/tasks/<task_id>

#### Expected response (200 OK)
```bash
{
  "msg": "Tarefa deletada com sucesso"
}
```
# Quick verification sequence (full flow)
```bash
POST /tasks → creates, returns id = N.

GET /tasks → check that the task appears in the list.

PUT /tasks/N → update fields.

GET /tasks → check that the changes show up.

DELETE /tasks/N → delete.

GET /tasks → check that the task is gone from the list.
```

# ✅ Contributing

Feel free to clone, modify and test the project. Suggestions are always welcome! 🚀

# 📄 License

This project is licensed under the MIT license.
