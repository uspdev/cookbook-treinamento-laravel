# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 6 - Implementar opção de delete das disciplinas

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
            <br>
            <form method="POST" action="/disciplinas/{{ $disciplina->id }}">
                {{ csrf_field() }}
                {{ method_field('delete') }}
                <button type="submit">Apagar</button>
            </form>
        </li>
    @endforeach
    </ul>
```

- Editar o método destroy em app/Http/Controllers/DisciplinaController
```php
    public function destroy(Disciplina $disciplina)
    {
        $disciplina->delete();
        return redirect('/');
    }
```

- Teste no navegador em http://localhost:8000
