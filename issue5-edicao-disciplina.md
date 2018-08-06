# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 5 - Criando o formulário para edição da disciplina

- Crie o arquivo resources/views/disciplinas/edit.blade.php
```php
    <form method="POST" action="/disciplinas/{{ $disciplina->id  }}">
        {{ csrf_field() }}
        {{ method_field('patch') }}
        Nome: <input name="titulo" value="{{ $disciplina->titulo }}">
        Ementa: <textarea name="ementa"> {{ $disciplina->ementa }} </textarea>
        <button type="submit"> Salvar </button>
    </form>
```

- Edite o método edit em app/Http/Controllers/DisciplinaController
```php
    public function edit(Disciplina $disciplina)
    {
        return view('disciplinas.edit',compact('disciplina'));
    }
```

- Edite o método update em app/Http/Controllers/DisciplinaController
```php
    public function update(Request $request, Disciplina $disciplina)
    {
        $disciplina->titulo = $request->titulo;
        $disciplina->ementa = $request->ementa;
        $disciplina->save();

        return redirect("/disciplinas/$disciplina->id");
    }
```

- Adicione o link para editar a disciplina em resources/views/disciplinas/index.blade.php
```php
    <ul>
    @foreach ($disciplinas as $disciplina)
        <li>
            <a href="/disciplinas/{{ $disciplina->id }}">
                {{ $disciplina->titulo }} 
            </a>
            <br>
            <a href="/disciplinas/{{ $disciplina->id }}/edit"> Editar </a>
        </li>
    @endforeach
    </ul>
```
- Teste no navegador em http://localhost:8000
