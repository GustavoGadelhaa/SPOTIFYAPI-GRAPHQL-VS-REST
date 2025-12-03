# 🎵 **Spotify API – REST & GraphQL**

![Java](https://img.shields.io/badge/Java-17+-red)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen)
![H2](https://img.shields.io/badge/Database-H2-blue)
![GraphQL](https://img.shields.io/badge/API-GraphQL-orange)
![REST](https://img.shields.io/badge/API-REST-lightgrey)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-purple)

---

## 📌 **Descrição**
Este projeto é uma API inspirada no Spotify, oferecendo endpoints REST e GraphQL para gerenciamento de **usuários**, **músicas** e **playlists**. Inclui um banco em memória H2, interface GraphiQL integrada e exemplos completos de consultas, mutações e uso via cURL.

---

## 🎥 **Demonstração**
*Imagens ilustrativas caso não fornecidas:*

![Demo](https://via.placeholder.com/900x400?text=Demo+da+Spotify+API)
![GraphiQL](https://via.placeholder.com/900x400?text=GraphiQL+Interface)

---

## ⚙️ **Funcionalidades Principais**
- CRUD completo de **Usuários**, **Músicas** e **Playlists**
- API **REST** e **GraphQL** no mesmo projeto
- Adição e remoção de músicas em playlists
- Banco **H2 em memória** com console embutido
- Ambiente pronto para testes com Postman / Insomnia
- Estrutura modular e extensível

---

## 📁 **Estrutura do Projeto**
```bash
src/
 ├─ main/
 │   ├─ java/com/example/spotifyapi/
 │   │   ├─ controller/
 │   │   ├─ service/
 │   │   ├─ repository/
 │   │   ├─ model/
 │   │   └─ graphql/
 │   └─ resources/
 │       ├─ application.properties
 │       └─ schema.graphqls
 └─ test/
     └─ com/example/spotifyapi/
```
## 🔵 **API REST**
---

### 🔗 **Endpoints**

### 👥 **Usuários**
| Método | Endpoint | Descrição |
|-------|----------|-----------|
| GET    | `/api/users`            | Listar todos os usuários |
| GET    | `/api/users/{id}`       | Buscar usuário por ID |
| POST   | `/api/users`            | Criar novo usuário |
| PUT    | `/api/users/{id}`       | Atualizar usuário |
| DELETE | `/api/users/{id}`       | Remover usuário |

---

### 🎵 **Músicas**
| Método | Endpoint | Descrição |
|-------|----------|-----------|
| GET    | `/api/songs`            | Listar todas as músicas |
| GET    | `/api/songs/{id}`       | Buscar música por ID |
| POST   | `/api/songs`            | Criar nova música |
| PUT    | `/api/songs/{id}`       | Atualizar música |
| DELETE | `/api/songs/{id}`       | Remover música |

---

### 📁 **Playlists**
| Método | Endpoint | Descrição |
|-------|----------|-----------|
| GET    | `/api/playlists`                   | Listar todas as playlists |
| GET    | `/api/playlists/{id}`              | Buscar playlist por ID |
| POST   | `/api/playlists`                   | Criar nova playlist |
| PUT    | `/api/playlists/{id}`              | Atualizar playlist |
| DELETE | `/api/playlists/{id}`              | Remover playlist |

#### ➕ Adicionar / Remover músicas de playlists
| Método | Endpoint | Descrição |
|-------|----------|-----------|
| POST   | `/api/playlists/{id}/songs/{songId}`   | Adicionar música à playlist |
| DELETE | `/api/playlists/{id}/songs/{songId}`   | Remover música da playlist |

#### 🔍 Consultas extras
| Endpoint | Descrição |
|----------|-----------|
| `/api/playlists/user/{id}` | Buscar playlists de um usuário específico |
| `/api/playlists/{id}/songs` | Listar músicas de uma playlist |
| `/api/playlists/song/{id}` | Listar playlists que contêm uma música específica |

## 🟣 **GraphQL**
---

### 🔗 **Endpoint**

---

### 📊 **Queries**
```graphql
# Usuários
query {
  users {
    id
    nome
    idade
  }
}

query {
  user(id: 1) {
    id
    nome
  }
}

# Músicas
query {
  songs {
    id
    nome
    artista
  }
}

query {
  song(id: 1) {
    id
    nome
  }
}

# Playlists
query {
  playlists {
    id
    nome
  }
}

query {
  playlist(id: 1) {
    id
    nome
    usuario {
      nome
    }
  }
}
```
### 📊 **MUTATIONS**
```


# Usuários
mutation {
  createUser(nome: "Nome", idade: 25) {
    id
  }
}

mutation {
  updateUser(id: 1, nome: "Novo Nome") {
    id
  }
}

mutation {
  deleteUser(id: 1)
}

# Músicas
mutation {
  createSong(nome: "Música", artista: "Artista") {
    id
  }
}

mutation {
  updateSong(id: 1, nome: "Nova Música") {
    id
  }
}

mutation {
  deleteSong(id: 1)
}

# Playlists
mutation {
  createPlaylist(nome: "Playlist", usuarioId: 1) {
    id
  }
}

mutation {
  updatePlaylist(id: 1, nome: "Nova Playlist") {
    id
  }
}

mutation {
  deletePlaylist(id: 1)
}
```

### 🧪 **Exemplo de Uso (Postman / HTTP)**
```json
{
  "query": "query { users { id nome } }"
}
```
## 🗄️ **Banco de Dados H2 – Como Acessar**

A aplicação utiliza o **H2 Database em memória**, ideal para desenvolvimento e testes rápidos sem necessidade de instalação externa.

---

### 🔌 **Porta e Console do H2**
- **Porta padrão da aplicação:** `8080`
- **Console do H2:** `http://localhost:8080/h2-console`

## 🚀 Comparação de Performance – REST vs GraphQL

Para medir o desempenho real de cada abordagem, foi realizado um teste utilizando o mesmo conjunto de dados:  
um **dump de 300 usuários**, carregado tanto para a API REST quanto para a API GraphQL.

A seguir estão as capturas de tela dos tempos obtidos durante a requisição de **listar todos os usuários**:

---

### 🟣 **GraphQL – Query `users`**
Tempo médio: **~99ms**

![GraphQL Performance](https://github.com/GustavoGadelhaa/SPOTIFYAPI-GRAPHQL-VS-REST/blob/main/Captura%20de%20tela%20de%202025-12-03%2011-10-12.png)

---

### 🔵 **REST – GET `/api/users`**
Tempo médio: **~305ms**

![REST Performance](https://github.com/GustavoGadelhaa/SPOTIFYAPI-GRAPHQL-VS-REST/blob/main/Captura%20de%20tela%20de%202025-12-03%2011-01-04.png)

---

## ⚡ Resultados Observados

- **REST (GET /api/users)**  
  Primeira requisição: **305 ms**

- **GraphQL (query { users { ... } })**  
  Primeira requisição: **99 ms**

Esses valores mostram que o **GraphQL foi aproximadamente 3x mais rápido** na **primeira execução do endpoint**, mesmo acessando exatamente os mesmos dados.

---

## 🔁 Sobre a Segunda Execução dos Endpoints

Após testes repetidos, foi observado que **a partir da segunda requisição**, tanto no REST quanto no GraphQL, o tempo de resposta cai para cerca de **1/3 do tempo inicial**.  
Isso ocorre por causa de:

- Cache interno da JPA / Hibernate  
- Otimizações do próprio Spring Boot  
- Hotspot JVM otimizando o código após a primeira execução

👉 **Mesmo assim, para a comparação oficial, foi contabilizado apenas o tempo da *primeira requisição***, que melhor representa um cenário real de produção sem aquecimento de cache.

---

## 📊 Conclusão

Com base nos testes:

- GraphQL demonstrou **menor latência**, melhor aproveitamento de rede e consulta otimizada.  
- REST continua simples e direto, mas retorna mais dados e faz mais round-trips, impactando o tempo.  
- O *dump* de 300 usuários ajudou a evidenciar ainda mais essas diferenças de desempenho.

GraphQL mostrou-se a alternativa mais performática para consultas maiores e com seleção de campos específicos.
