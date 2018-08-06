# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 3 - Implementando o método show das Disciplinas

- Edite o método show, no app/Http/Controllers/DisciplinaController
```php
    public function show(Disciplina $disciplina)
    {
        return view('disciplinas.show',compact('disciplina'));
    }
```

- Crie o arquivo (view) resources/views/disciplinas/show.blade.php
```php
    <h1>{{ $disciplina->titulo }}</h1>
    <p>{{ $disciplina->ementa }}</p>
```

- Adicione um link para o show na view index (resources/views/disciplinas/index.blade.php)
```php
    <ul>
    @foreach ($disciplinas as $disciplina)
        <li>
            <a href="/disciplinas/{{ $disciplina->id }}">
                {{ $disciplina->titulo }} 
            </a>
        </li>
    @endforeach
    </ul>
```

- Teste no navegador em http://localhost:8000
