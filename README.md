# 📝 TodoList API - Sistema de Gerenciamento de Tarefas

Uma **API RESTful** completa para gerenciamento de tarefas, desenvolvida em **Java com Spring Boot**.  
Este projeto permite **criar, visualizar, atualizar e excluir tarefas**, além de oferecer funcionalidades avançadas como **filtros, paginação e ordenação**.

---

## 🚀 Tecnologias Utilizadas

- **Java 21** → Linguagem de programação  
- **Spring Boot 3.2.4** → Framework principal  
- **Spring Data JPA** → Persistência de dados  
- **H2 Database** → Banco de dados em memória (desenvolvimento)  
- **Maven** → Gerenciamento de dependências  
- **Lombok** → Redução de código boilerplate  
- **SpringDoc OpenAPI** → Documentação da API  

---

## 📦 Estrutura do Projeto

```text
src/
├── main/
│   ├── java/com/todolist/
│   │   ├── controller/         # Controladores REST
│   │   ├── model/              # Entidades JPA
│   │   ├── repository/         # Interfaces de repositório
│   │   ├── service/            # Lógica de negócio
│   │   └── TodoListApplication.java  # Classe principal
│   └── resources/
│       ├── application.properties    # Configurações
│       └── import.sql         # Dados iniciais (opcional)
└── test/                      # Testes unitários
```

---

## ⚙️ Funcionalidades

- ✅ Criar, visualizar, atualizar e excluir tarefas  
- ✅ Marcar tarefas como concluídas  
- ✅ Filtrar tarefas por status (concluídas/pendentes)  
- ✅ Paginação e ordenação de resultados  
- ✅ Busca por descrição  
- ✅ API documentada com OpenAPI/Swagger  
- ✅ Banco H2 para desenvolvimento com interface web  

---

## 🛠️ Como Executar o Projeto

### Pré-requisitos

- **Java JDK 17** ou superior  
- **Maven 3.6+** (opcional, o projeto usa wrapper)  
- **Git**  

### Passo a passo

**Clone o repositório**
```bash
git clone https://github.com/luizgabb/todolist-java-spring.git
cd todolist-java-spring
```

**Execute com Maven Wrapper**
```bash
# Linux/Mac
./mvnw spring-boot:run

# Windows
mvnw.cmd spring-boot:run
```

**Acesse a aplicação**
- API: [http://localhost:8080](http://localhost:8080)  
- Swagger UI: [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)  
- H2 Console: [http://localhost:8080/h2-console](http://localhost:8080/h2-console)  

**Credenciais do H2**
- JDBC URL: `jdbc:h2:mem:testdb`  
- Usuário: `sa`  
- Senha: *(vazio)*  

---

## 📚 Endpoints da API

### Tarefas

| Método | Endpoint                 | Descrição                       |
|--------|--------------------------|---------------------------------|
| **GET**    | `/api/todos`              | Lista todas as tarefas (com filtros) |
| **GET**    | `/api/todos/{id}`         | Busca uma tarefa por ID         |
| **POST**   | `/api/todos`              | Cria uma nova tarefa            |
| **PUT**    | `/api/todos/{id}`         | Atualiza uma tarefa existente   |
| **DELETE** | `/api/todos/{id}`         | Exclui uma tarefa               |
| **PATCH**  | `/api/todos/{id}/complete` | Marca tarefa como concluída     |
| **PATCH**  | `/api/todos/{id}/pending`  | Marca tarefa como pendente      |

**Parâmetros de Consulta para GET `/api/todos`**
- `page` → Número da página (padrão: 0)  
- `size` → Tamanho da página (padrão: 10)  
- `sort` → Campo para ordenação (ex: description,asc)  
- `completed` → Filtrar por status (true/false)  
- `description` → Filtrar por descrição (contém)  

---

## 🔧 Exemplos de Uso

**Criar uma tarefa**
```bash
curl -X POST "http://localhost:8080/api/todos"   -H "Content-Type: application/json"   -d '{
    "description": "Estudar Spring Boot",
    "completed": false
  }'
```

**Listar tarefas pendentes**
```bash
curl "http://localhost:8080/api/todos?completed=false&page=0&size=5"
```

**Marcar tarefa como concluída**
```bash
curl -X PATCH "http://localhost:8080/api/todos/1/complete"
```

---

## 🧪 Testes

Execute os testes unitários com:
```bash
./mvnw test
```

---

## 📊 Banco de Dados

O projeto utiliza o **H2 Database** em memória para desenvolvimento.  
Os dados são persistidos durante a execução da aplicação, mas são perdidos ao reiniciar.

**Acessando o console do H2**
1. Execute a aplicação  
2. Acesse [http://localhost:8080/h2-console](http://localhost:8080/h2-console)  
3. Use as credenciais:  
   - JDBC URL: `jdbc:h2:mem:testdb`  
   - User Name: `sa`  
   - Password: *(deixe em branco)*  

---

## 🚧 Próximas Melhorias

- Adicionar autenticação e autorização  
- Implementar testes de integração  
- Adicionar suporte a outros bancos de dados (PostgreSQL, MySQL)  
- Implementar front-end web  
- Adicionar categorias/tags para tarefas  
- Implementar datas de vencimento e lembretes  
- Adicionar deploy configuration (Docker, cloud)  

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Siga os passos:

1. Faça um fork do projeto  
2. Crie uma branch para sua feature  
   ```bash
   git checkout -b feature/AmazingFeature
   ```  
3. Commit suas mudanças  
   ```bash
   git commit -m 'Add some AmazingFeature'
   ```  
4. Push para a branch  
   ```bash
   git push origin feature/AmazingFeature
   ```  
5. Abra um Pull Request  

---

## 📄 Licença

Este projeto está sob a licença **MIT**.  
Veja o arquivo LICENSE para mais detalhes.

---

## 👨‍💻 Autor

**Luiz Gabriel** - [GitHub](https://github.com/luizgabb)

---

## 🔗 Links Úteis

- [Spring Boot Documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/)  
- [Spring Data JPA Documentation](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/)  
- [H2 Database Documentation](https://www.h2database.com/html/main.html)  
