# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 2 - Implementando o método index 

- Edite o método index, no app/Http/Controllers/DisciplinaController
```php
    public function index()
    {
        return Disciplina::all();
    }
```

- Edite o arquivo de rotas routes/web.php - substitua todo o seu conteúdo
```php
    Route::get('/','DisciplinaController@index');
    Route::resource('disciplinas','DisciplinaController');
```

- Teste no navegador - http://localhost:8000

- Edite o método index para usar uma view
```php
    public function index()
    {
        $disciplinas = Disciplina::all();
        return view('disciplinas.index', compact('disciplina'));
    }
```

- Crie o arquivo de view na pasta resources/views (crie a pasta disciplinas, e dentro dela o arquivo index.blade.php)
```php
    /* Arquivo resources/views/disciplinas/index.blade.php */

    <ul>
    @foreach ($disciplinas as $disciplina)
        <li>{{ $disciplina->titulo }} </li>
    @endforeach
    </ul>
```

- Teste no navegador em http://localhost:8000
