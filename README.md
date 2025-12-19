# Sistema de Gestão de Eventos — API REST com Django
> Este repositório é um fork de um projeto desenvolvido em grupo, mantido aqui para continuidade do desenvolvimento e documentação individual.

![Python](https://img.shields.io/badge/Python-3.12+-blue?logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-5.0+-darkgreen?logo=django&logoColor=white)
![Django REST Framework](https://img.shields.io/badge/Django%20REST%20Framework-API%20REST-red)
![SQLite](https://img.shields.io/badge/SQLite-Database-blue?logo=sqlite&logoColor=white)
![Git](https://img.shields.io/badge/Git-Version%20Control-orange?logo=git&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

## Instituições de Fomento e Parceria
[![Instituto Federal de Brasília](https://img.shields.io/badge/Instituto%20Federal%20de%20Brasília-IFB-%23508C3C?labelColor=%23C8102E)](https://www.ifb.edu.br/)
[![Instituto Hardware Brasil](https://img.shields.io/badge/Instituto%20Hardware%20Brasil-IHWB-%23DAA520?labelColor=%232E2E2E)](https://hardware.org.br/)

## Orientador
[![Currículo Lattes](https://img.shields.io/badge/Currículo%20Lattes-Henrique%20Pereira-green?logo=cnpq&logoColor=white)](http://lattes.cnpq.br/5409128005289847)

**Henrique Pereira de Freitas Filho**  
Professor Orientador — Instituto Federal de Brasília  
📧 henrique.filho@ifb.edu.br 

## Sumário

- [Visão Geral](#visão-geral)
- [Pacotes Utilizados](#pacotes-utilizados)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Diagramas de Banco de Dados](#diagrama-de-banco-de-dados)
- [Documentação da API](#documentação-da-api)
- [Configuração do Ambiente](#configuração-do-ambiente)
- [Deploy](#deploy)

## Visão Geral

Esta API REST tem como objetivo fornecer uma solução backend para a gestão de eventos, permitindo o cadastro de eventos, a associação de atividades e a inscrição de participantes. O sistema também possibilita a definição de um responsável por atividade, estruturando os relacionamentos entre as entidades de forma consistente e alinhada aos princípios REST.

## Pacotes Utilizados

Liste todos os pacotes Python necessários, com versões recomendadas. Utilize um formato de tabela para maior clareza.

| Pacote                  | Versão       | Descrição                                      |
|-------------------------|--------------|------------------------------------------------|
| Django                  | >=5.0        | Framework web principal                        |
| djangorestframework     | latest       | Toolkit para construção de APIs REST           |
| django-filter           | latest       | Suporte a filtros nos endpoints da API         |
| drf-spectacular         | latest       | Geração automática de documentação OpenAPI     |
| ...                     | ...          | ...                                            |

> **Nota:** Consulte o arquivo `requirements.txt` para a lista completa e versões exatas.

## Estrutura do Projeto

```
gestor_eventos/
├── docs/
│   ├── modelo-conceitual.jpg
│   └── modelo-logico.jpg
├── eventos/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── serializers.py
│   ├── test.py
│   └── views.py
├── gestor_eventos/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
└── requirements.txt
```

## Descrição da Estrutura do Projeto

- **gestor_eventos/** (raiz)  
  Diretório principal do projeto, contendo a aplicação Django, arquivos de configuração e dependências.

- **eventos/**  
  Aplicação responsável pelo domínio do sistema, concentrando as regras de negócio relacionadas a eventos, atividades e participantes.
  - **admin.py**: Registro dos modelos no painel administrativo do Django.
  - **apps.py**: Configuração da aplicação `eventos`.
  - **models.py**: Definição das entidades do sistema e seus relacionamentos.
  - **serializers.py**: Serialização e validação dos dados para a API REST.
  - **views.py**: Implementação dos endpoints da API e lógica das requisições.
  - **test.py**: Arquivos destinados a testes automatizados da aplicação.

- **gestor_eventos/** (configuração)  
  Diretório de configuração global do projeto Django.
  - **settings.py**: Configurações gerais do projeto (apps, banco de dados, middleware, etc.).
  - **urls.py**: Definição das rotas principais da aplicação.
  - **asgi.py / wsgi.py**: Pontos de entrada para servidores ASGI e WSGI.

- **manage.py**  
  Script de gerenciamento do Django, utilizado para executar comandos administrativos, como migrações e inicialização do servidor.

- **requirements.txt**  
  Lista de dependências Python necessárias para a execução do projeto.

## Diagramas de Banco de Dados

### Modelo Conceitual
![Modelo Conceitual do Banco de Dados](./docs/modelo-conceitual.jpg)

### Modelo Lógico
![Modelo Lógico do Banco de Dados](./docs/modelo-logico.jpg)

## Documentação da API

A documentação interativa está disponível em `/api/docs/` (Swagger UI) ou `/api/redoc/` (ReDoc) no ambiente de desenvolvimento.

### Endpoints Principais

| Método | Endpoint                   | Descrição                           | Autenticação |
|--------|----------------------------|-------------------------------------|--------------|
| GET    | `/api/eventos/`            | Lista todos os eventos              | Opcional     |
| POST   | `/api/eventos/`            | Cria um novo evento                 | Requerida    |
| GET    | `/api/eventos/{id}/`       | Recupera um evento específico       | Opcional     |
| PUT    | `/api/eventos/{id}/`       | Atualiza um evento                  | Requerida    |
| DELETE | `/api/eventos/{id}/`       | Remove um evento                    | Requerida    |
| GET    | `/api/participantes/`      | Lista todos os participantes        | Opcional     |
| POST   | `/api/participantes/`      | Cria um novo participante           | Requerida    |
| GET    | `/api/participantes/{id}/` | Recupera um participante específico | Opcional     |
| PUT    | `/api/participantes/{id}/` | Atualiza um evento                  | Requerida    |
| DELETE | `/api/participantes/{id}/` | Remove um evento                    | Requerida    |
| GET    | `/api/atividades/`         | Lista todos as atividades           | Opcional     |
| POST   | `/api/atividades/`         | Cria uma nova atividade             | Requerida    |
| GET    | `/api/atividades/{id}/`    | Recupera uma atividade específica   | Opcional     |
| PUT    | `/api/atividades/{id}/`    | Atualiza uma atividade              | Requerida    |
| DELETE | `/api/atividades/{id}/`    | Remove uma atividade                | Requerida    |
| ...    | ...                        | ...                                 | ...          |

### Endpoints de Relacionamento

#### Participantes de um evento (N:N):
| Método | Endpoint                           | Descrição                                            | Autenticação |
|--------|------------------------------------|------------------------------------------------------|--------------|
| GET    | `/api/eventos/{id}/participantes`  | Lista participantes inscritos em um evento           | Opcional     |
| POST   | `/api/eventos/{id}/participantes`  | Inscreve um participante em um evento existente      | Requerida    |

#### Atividades de um Evento (1:N):
| Método | Endpoint                           | Descrição                                            | Autenticação |
|--------|------------------------------------|------------------------------------------------------|--------------|
| GET    | `/api/eventos/{id}/atividades/`    | Lista as atividades vinculadas a um evento           | Opcional     |
| POST   | `/api/eventos/{id}/atividades/`    | Cadastra nova atividade associada a um evento        | Requerida    |

#### Responsável por uma Atividade (1:N):
| Método | Endpoint                           | Descrição                                            | Autenticação |
|--------|------------------------------------|------------------------------------------------------|--------------|
| GET    | `/api/atividades/{id}/responsavel/`| Retorna o participante responsável por uma atividade | Opcional     |
| PUT   | `/api/atividades/{id}/responsavel/` | Altera o responsável por uma atividade               | Requerida    |

> **Detalhes:** Consulte a interface Swagger para schemas de request/response, parâmetros e exemplos.

## Configuração do Ambiente

Siga os passos abaixo para configurar o ambiente local.

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/antoniogms/gestor_eventos.git
   cd gestor_eventos
   ```

2. **Crie um ambiente virtual:**
   ```bash
   python -m venv venv
   ```
   Ative o ambiente virtual conforme o sistema operacional:
   ```
   source venv/bin/activate  # Linux/Mac
   venv\Scripts\activate     # Windows
   ```

3. **Instale as dependências:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure as variáveis de ambiente:**
   ```bash
   cp .env.example .env
   # Edite .env com suas credenciais
   ```

5. **Aplique as migrações e inicie o servidor:**
   ```bash
   python manage.py migrate
   python manage.py runserver
   ```

## Deploy

https://gestor-eventos.duckdns.org/api/

Detalhes sobre o deploy em breve...