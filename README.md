# Simple Public Witnessing

## Introdução
Este projeto é uma aplicação simples para testemunho público. Siga as instruções abaixo para configurar e iniciar o projeto.

## Pré-requisitos
Certifique-se de ter os seguintes softwares instalados em sua máquina:
- [Node.js](https://nodejs.org/)
- [PostgreSQL](https://www.postgresql.org/)
- [Git](https://git-scm.com/)
- [PHP](https://www.php.net/)

## Instalação
### Configurando o Git e a conta no GitHub

1. Configure seu nome de usuário e e-mail no Git:
  ```bash
  git config --global user.name "Seu Nome"
  git config --global user.email "seu-email@example.com"
  ```

  ### Autenticando no Git com HTTPS

  1. Gere um token de acesso pessoal no GitHub:
    - Vá para [Configurações de Tokens](https://github.com/settings/tokens) no GitHub.
    - Clique em "Generate new token" (Gerar novo token).
    - Selecione os escopos necessários e clique em "Generate token" (Gerar token).
    - Copie o token gerado e guarde-o em um local seguro.

  2. Configure o Git para usar o token de acesso pessoal:
    - Ao clonar um repositório ou ao realizar operações que exigem autenticação, use o seguinte formato de URL:
      ```bash
      https://<seu-token>@github.com/alberttocastro/SPW.git
      ```
    - Substitua `<seu-token>` pelo token de acesso pessoal gerado anteriormente.

  3. Salve suas credenciais no cache do Git para evitar digitar o token repetidamente:
    ```bash
    git config --global credential.helper cache
    ```

  4. Opcionalmente, você pode definir um tempo limite para o cache das credenciais (em segundos):
    ```bash
    git config --global credential.helper 'cache --timeout=3600'
    ```

  Se tudo estiver configurado corretamente, você verá uma mensagem de sucesso indicando que a autenticação foi realizada com sucesso.

Se tudo estiver configurado corretamente, você verá uma mensagem de sucesso indicando que a autenticação foi realizada com sucesso.

### 1. Clone o repositório
```bash
git clone https://github.com/seu-usuario/simplepublicwitnessing.git
cd simplepublicwitnessing
```

### 2. Instale as dependências do Node.js
```bash
npm install
```

### Instalando e configurando o PostgreSQL

1. Baixe e instale o PostgreSQL:
  - No [site oficial](https://www.postgresql.org/download/), escolha a versão adequada para o seu sistema operacional e siga as instruções de instalação.

2. Após a instalação, inicie o serviço do PostgreSQL:
  - No Windows, o serviço geralmente é iniciado automaticamente.
  - No Linux, use o comando:
    ```bash
    sudo service postgresql start
    ```

3. Acesse o console do PostgreSQL:
  ```bash
  sudo -u postgres psql
  ```

4. Crie um usuário para o seu projeto:
  ```sql
  CREATE USER seu-usuario WITH PASSWORD 'sua-senha';
  ```

5. Conceda permissões ao usuário criado:
  ```sql
  ALTER USER seu-usuario CREATEDB;
  ```

6. Saia do console do PostgreSQL:
  ```sql
  \q
  ```

### 3. Configure o banco de dados PostgreSQL
- Crie um banco de dados no PostgreSQL:
  ```sql
  CREATE DATABASE simplepublicwitnessing;
  ```
- Configure as credenciais do banco de dados no arquivo `.env`:
  ```
  DB_HOST=localhost
  DB_USER=seu-usuario
  DB_PASSWORD=sua-senha
  DB_NAME=simplepublicwitnessing
  ```
  ### 4. Execute as migrações do banco de dados

  Para executar as migrações do banco de dados utilizando o Laravel, siga os passos abaixo:

  1. Instale as dependências do PHP e do Laravel:
    ```bash
    composer install
    ```

  2. Configure o arquivo `.env` com as credenciais do banco de dados:
    ```
    DB_CONNECTION=pgsql
    DB_HOST=127.0.0.1
    DB_PORT=5432
    DB_DATABASE=simplepublicwitnessing
    DB_USERNAME=seu-usuario
    DB_PASSWORD=sua-senha
    ```

  3. Execute as migrações:
    ```bash
    php artisan migrate
    ```

  Se tudo estiver configurado corretamente, as tabelas do banco de dados serão criadas conforme definido nas migrações do Laravel.

## Executando o projeto

### Iniciando o servidor Node.js
Para iniciar o servidor Node.js, execute o comando:
```bash
npm start
```

### Iniciando o projeto Laravel
Para iniciar o projeto Laravel, execute o comando:
```bash
php artisan serve
```

O servidor Laravel estará disponível em `http://localhost:8000`.

## Contribuição
Sinta-se à vontade para contribuir com este projeto. Envie um pull request com suas alterações.

## Licença
Este projeto está licenciado sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.