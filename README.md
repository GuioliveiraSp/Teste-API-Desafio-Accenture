# Testes de API com Postman

Coleção Postman para testes de uma API de gerenciamento de livros e usuários.

## 📌 Pré-requisitos

- [Postman](https://www.postman.com/downloads/) instalado
- (Opcional) [Newman](https://learning.postman.com/docs/running-collections/using-newman-cli/command-line-integration-with-newman/) para execução via linha de comando

## 🚀 Como Executar os Testes

Siga estes passos para importar e executar a coleção no Postman:

1. **Baixe a coleção**
   - Faça o download do arquivo `Testes_Postman.json` deste repositório

2. **Importe para o Postman**
   - Abra o Postman
   - Clique em "Import" > "File"
   - Selecione o arquivo `Testes_Postman.json`
   - Clique em "Import"

3. **Execute os endpoints em ordem**:
   ```mermaid
   graph TD
     A[1. Criar Usuário] --> B[2. Gerar Token]
     B --> C[3. Verificar Autorização]
     C --> D[4. Listar Livros]
     D --> E[5. Selecionar Livros]
     E --> F[6. Ver Livros Reservados]
📋 Endpoints Disponíveis
1. POST /Account/v1/User
Cria um usuário randômico para testes.

Corpo da Requisição (Exemplo):

json
{
  "userName": "usuario_teste",
  "password": "Senha@123"
}
2. POST /GenerateToken
Gera um token de acesso para o usuário criado.

Corpo da Requisição:

json
{
  "userName": "usuario_teste",
  "password": "Senha@123"
}
3. POST /Autorized
Verifica se o usuário tem permissão de acesso.

Corpo da Requisição:

json
{
  "userName": "usuario_teste",
  "password": "Senha@123"
}
4. GET /ListBooks
Lista todos os livros disponíveis para locação (requer token no header).

Headers:

Authorization: Bearer <token>
5. POST /SelectBooks
Reserva 2 livros manualmente (requer token).

Corpo da Requisição:

json
{
  "userId": "ID_DO_USUARIO",
  "collectionOfIsbns": [
    {"isbn": "ISBN_LIVRO1"},
    {"isbn": "ISBN_LIVRO2"}
  ]
}
6. GET /ChosenBooks
Lista os livros reservados pelo usuário (requer token).

Headers:

Authorization: Bearer <token>
🔧 Execução Automatizada
Para executar via linha de comando com Newman:

bash
npm install -g newman
newman run Testes_Postman.json
⁉️ Suporte
Em caso de problemas:

Verifique se todas as etapas estão sendo executadas em sequência

Confira se o token está sendo incluído nos headers das requisições

Abra uma issue neste repositório

