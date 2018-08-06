# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 1 - Criando Resource para Disciplinas

- Gere o model para Disciplina
```
    php artisan make:model Disciplina -crm
```

- Edite o arquivo de migrations (***create_disciplinas_table.php)
```php
    /* Adicione os campos ao corpo do método up */
    $table->string('titulo');
    $table->text('ementa');
```

- Faça a migração do banco de dados
```
    php artisan migrate
```

- Use o Tinker para inserir algumas disciplinas no banco de dados
```php
    php artisan tinker

    >>> $d = new Disciplina
    >>> $d->titulo = "Filosofia I"
    >>> $d->ementa = "Aulas de Filosofia, etc."
    >>> $d->save()

    >>> $d2 = new Disciplina
    >>> $d2->titulo = "História da Arte"
    >>> $d2->ementa = "Ementa da disciplina História da Arte."
    >>> $d2->save()
```

- Para ver as disciplinas cadastradas, usando o tinker:
```php
    >>> Disciplina::all()
```
