# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 7 - Criar model e migrations para Turma

- Crie o model com o Artisan
```php
    php artisan make:model Turma -m
```

- Editar a migration create_turmas_table.php (pasta database/migrations)
```php
    /* Adicione os campos ao corpo do método up */
    $table->string('ministrante');
    $table->date('inicio');
    $table->date('fim');
    $table->text('bibliografia')->nullable();
    $table->integer('disciplina_id')->unsigned();
    $table->foreign('disciplina_id')->references('id')->on('disciplinas');
```

- Roda as migrations com o Artisan
```
    php artisan migrate
```
