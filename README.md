# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Criação do projeto

- Crie o banco de dados

- Crie o projeto disciplinas
```
    composer create-project laravel/laravel disciplinas
```

- Edite o arquivo .env e coloque os dados da sua conexão com o banco de dados
```
    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=homestead
    DB_USERNAME=homestead
    DB_PASSWORD=secret
```

- Faça a migração do banco de dados
```
    php artisan migrate
```

- Rode o servidor web do Laravel
```
    php artisan serve
```

- Acesse o navegador em http://localhost:8000
