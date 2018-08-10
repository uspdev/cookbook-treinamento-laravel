# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 11 - Autenticando o usuário e restringindo acesso ao cadastro de disciplinas e turmas

- Gere a autenticação pelo artisan
```php
    php artisan make:auth
```

- Crie o método construtor no DisciplinaController
```php
    public function __construct()
    {
        $this->middleware('auth')->except(['index','show']);

    }
```

- Crie um template master - resources/views/layouts/master.blade.php
```php
	@auth
		<form id="logout-form" action="/logout" method="POST"> 
			{{ csrf_field() }}
			<button type="submit">Sair </button>
		</form>
	@else
		<a href="/login">Login</a>
		<a href="/register">Register</a>
	@endauth
```

- Em todas as views da pasta resources/views/disciplinas/* (inclusive na pasta turmas) - coloque o código para herdar o template master
```php
/* Coloque na primeira linha de cada view */
@extends('layouts.master')
```
