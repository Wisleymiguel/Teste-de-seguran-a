# 🔐 EBAC Injection Testing

Projeto de testes de segurança focado em vulnerabilidades de injeção (SQL Injection, NoSQL Injection e Command Injection), desenvolvido como parte do curso de Quality Assurance da EBAC.

## 📋 Sobre o Projeto

Este repositório contém uma suíte de testes automatizados para identificar e validar vulnerabilidades de injeção em uma API de demonstração. O objetivo é praticar técnicas de teste de segurança seguindo metodologias como OWASP.

### Tipos de Testes Cobertos

- **SQL Injection** - Testes contra banco de dados PostgreSQL
- **NoSQL Injection** - Testes contra banco de dados MongoDB
- **Command Injection** - Testes de injeção de comandos no sistema operacional

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Versão | Descrição |
|------------|--------|-----------|
| Node.js | 16+ | Runtime JavaScript |
| Jest | 27.5.1 | Framework de testes |
| Supertest | 6.2.2 | Biblioteca para testes de API HTTP |
| Docker | - | Containerização dos serviços |
| PostgreSQL | 11.2 | Banco de dados relacional |
| MongoDB | latest | Banco de dados NoSQL |

## 📁 Estrutura do Projeto

```
ebac-injection-testing/
├── test/
│   └── sql.spec.js          # Testes de SQL Injection
├── resources/               # Arquivos de recursos para testes
├── .env                     # Variáveis de ambiente
├── docker-compose.yml       # Configuração dos containers
├── jest.config.json         # Configuração do Jest
├── package.json             # Dependências do projeto
└── README.md
```

## 🚀 Como Executar

### Pré-requisitos

- Node.js (v16 ou superior)
- Docker e Docker Compose
- npm ou yarn

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/ebac-injection-testing.git
cd ebac-injection-testing
```

### 2. Instale as dependências

```bash
npm install
```

### 3. Suba os containers da aplicação

```bash
docker-compose up -d
```

Isso irá iniciar:
- **API** na porta `3000`
- **PostgreSQL** na porta `5432`
- **MongoDB** na porta `27017`

### 4. Verifique se os serviços estão rodando

```bash
docker-compose ps
```

### 5. Execute os testes

```bash
npm test
```

## ⚙️ Configuração

### Variáveis de Ambiente

O arquivo `.env` contém as configurações necessárias:

```env
API_URL=http://localhost:3000
```

### Docker Compose

Os serviços são configurados no `docker-compose.yml`:

| Serviço | Porta | Credenciais |
|---------|-------|-------------|
| API | 3000 | - |
| PostgreSQL | 5432 | postgres/postgres |
| MongoDB | 27017 | mongodb/mongodb |

## 🧪 Exemplos de Payloads de Teste

### SQL Injection

```javascript
// Bypass de autenticação
const payload = "' OR '1'='1' --";

// Union-based injection
const payload = "' UNION SELECT * FROM users --";
```

### NoSQL Injection

```javascript
// Bypass com operador $ne
const payload = { "$ne": null };

// Bypass com operador $gt
const payload = { "$gt": "" };
```

### Command Injection

```javascript
// Injeção de comando
const payload = "& echo 'comando' &";

// Encadeamento de comandos
const payload = "; ls -la";
```

## 📚 Referências

- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [OWASP Top 10 - Injection](https://owasp.org/Top10/A03_2021-Injection/)
- [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)

## 👨‍💻 Autor

**Wisley Borges**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/wisleyborges)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/wisleyborges)

---

## 📄 Licença

Este projeto está sob a licença ISC.

---

⚠️ **Aviso Legal**: Este projeto é exclusivamente para fins educacionais. Os testes de segurança devem ser realizados apenas em ambientes controlados e com autorização prévia. O uso indevido dessas técnicas é ilegal e antiético.
