> 🇺🇸 [English version](README.md)

# 📌 API de Gerenciamento de Tarefas (Flask + JWT)

Esta é uma API REST desenvolvida com Flask para gerenciamento de tarefas, com autenticação de usuários usando JWT (JSON Web Token).
O projeto permite que cada usuário possa se cadastrar, fazer login e gerenciar suas próprias tarefas (CRUD).

# 🚀 Tecnologias utilizadas

Python

Flask

Flask-SQLAlchemy

Flask-JWT-Extended

SQLite (banco de dados local)

# 📁 Estrutura do Projeto
<pre>
api-gerenciamento-tarefas/
└── instance/
    └── tarefas.db        # Banco SQLite (criado automaticamente)
├── routes/
│   ├── auth_routes.py    # Rotas de autenticação
│   └── task_routes.py    # Rotas das tarefas
├── .gitattributes        # Configurações de atributos de arquivos para o Git
├── .gitignore            # Lista de arquivos e diretórios a serem ignorados pelo Git
├── app.py                # Arquivo principal do Flask
├── database.py           # Modelos e conexão com banco de dados
├── extensions.py         # Inicialização e configuração de extensões Flask
├── README.md             # Versão em inglês
├── README.pt-BR.md       # Este arquivo
└── requirements.txt      # Dependências do projeto
</pre>
# ⚙️ Como executar o projeto
## 1. Clone o repositório:
```bash
git clone https://github.com/gualmeidap/api-gerenciamento-tarefas.git

cd api-gerenciamento-tarefas
```

## 2. Crie um ambiente virtual (opcional, mas recomendado):

```bash
python -m venv venv
```

### Ative o ambiente:

#### Linux/macOS:
```bash
source venv/bin/activate
```
#### Windows:
```bash
venv\Scripts\activate
```
## 3. Instale as dependências:
```bash
pip install -r requirements.txt
```
## 4. Execute a aplicação:
```bash
python app.py
```

# 🧪 Testando a API e Respostas Esperadas usando [Postman](https://www.postman.com/downloads/)
## 1. Register User

Método: POST

Endpoint: http://127.0.0.1:5000/register

#### Body (JSON):
```bash
{
  "username": "usuario1",
  "email": "usuario1@email.com",
  "password": "123456"
}
```

#### Resposta esperada (201):
```bash 
{
  "msg": "Usuário registrado com sucesso"
}
```
## 2. Login User

Método: POST

Endpoint: http://127.0.0.1:5000/login

#### Body (JSON):
```bash
{
  "email": "usuario1@email.com",
  "password": "123456"
}
```
#### Resposta esperada (200):
```bash
{
  "access_token": "<jwt_token_aqui>",
  "user": {
    "id": 1,
    "username": "usuario1",
    "email": "usuario1@email.com"
  }
}
```
📌 Observação: pegue o token do /login e use no header de Create, List, Update e Delete.

## 3. Create Task

Método: POST

Endpoint: http://127.0.0.1:5000/tasks

#### Body (JSON):
```bash
{
  "title": "Estudar Flask",
  "description": "Finalizar projeto com autenticação"
}
```

#### Resposta esperada (201 Created)
```bash
{
  "msg": "Tarefa criada com sucesso",
  "id": 1
}
```
📌 Observação: anote o id retornado — você usará ele nos testes de update/delete.

## 4. List Task

Método: GET

Endpoint: http://127.0.0.1:5000/tasks

Headers:

Authorization: Bearer <seu_token>

#### Resposta (200):
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

Método: PUT

Endpoint: http://127.0.0.1:5000/tasks/<task_id>

#### Body (JSON):
```bash
{
  "title": "Estudar Flask atualizado",
  "description": "Atualizei a descrição",
  "completed": true
}
```
#### Resposta esperada (200 OK)
```bash
{
  "msg": "Tarefa atualizada com sucesso"
}
```
## 6. Delete Task

Método: DELETE

Endpoint: http://127.0.0.1:5000/tasks/<task_id>

#### Resposta esperada (200 OK)
```bash
{
  "msg": "Tarefa deletada com sucesso"
}
```
# Sequência de verificação rápida (fluxo completo)
```bash
POST /tasks → cria, retorna id = N.

GET /tasks → verifique que a tarefa aparece na lista.

PUT /tasks/N → atualizar campos.

GET /tasks → verifique que as alterações apareceram.

DELETE /tasks/N → deletar.

GET /tasks → verifique que a tarefa sumiu da lista.
```

# ✅ Contribuição

Sinta-se à vontade para clonar, modificar e testar o projeto. Sugestões são sempre bem-vindas! 🚀

# 📄 Licença

Este projeto está sob a licença MIT.