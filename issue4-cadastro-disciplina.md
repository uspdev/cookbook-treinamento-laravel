# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 4 - Criando o formulário de cadastro de disciplina

- Crie o arquivo resources/views/disciplinas/create.blade.php
```php
    <form method="POST" action="/disciplinas">
        {{ csrf_field() }}
        Nome: <input name="titulo">
        Ementa: <textarea name="ementa"> </textarea>
        <button type="submit"> Salvar </button>
    </form>
```

- Edite o método create em app/Http/Controllers/DisciplinaController
```php
    public function create()
    {
        return view('disciplinas.create');
    }
```

- Edite o método store em app/Http/Controllers/DisciplinaController
```php
    public function store(Request $request)
    {
        $disciplina = new Disciplina;
        $disciplina->titulo = $request->titulo;
        $disciplina->ementa = $request->ementa;
        $disciplina->save();

        return redirect('/');
    }
```

- Adicione o link para cadastrar nova disciplina em resources/views/disciplinas/index.blade.php
```php
<a href="/disciplinas/create">Cadastrar nova disciplina</a>
```

- Teste no navegador em http://localhost:8000
