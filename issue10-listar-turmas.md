# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 10 - Listar as turmas cadastradas nas páginas das disciplinas

- Mostrar as turmas na págian show da disciplina (resources/views/disciplinas/show.blade.php)
```php
    @foreach ($disciplina->turmas as $turma)
        {{ $turma->ministrante }}
        {{ $turma->inicio }}
    @endforeach
```

- Teste no navegador
