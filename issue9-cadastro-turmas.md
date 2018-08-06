# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 9 - Criação de formulário para cadastro de turma no contexto da disciplina

- No DisciplinaController, crie o método para inserção de turmas
```php
    public function createTurma($disciplina_id)
    {
        return view('disciplinas.turmas.create',compact('disciplina_id'));
    }
```

- Adicione a rota para o método createTurma (routes/web.php)
```php
    Route::get('/disciplinas/{disciplina_id}/turmas/create','DisciplinaController@createTurma');
```

- Adicione um link para a inserção de turma na view show, da disciplina (resources/views/disciplinas/show.blade.php)
```php
    <a href="/disciplinas/{{ $disciplina->id }}/turmas/create">Inserir Turma</a>
```

- Crie a view com o formulário para o cadastro da turma (resources/view/disciplinas/turmas/create.blade.php)
```php
    <form method="POST" action="/disciplinas/{{ $disciplina_id }}/turmas">
        {{ csrf_field() }}

        Ministrante: <input name="ministrante">

        Data início: <input name="inicio">

        Data fim: <input name="fim">

        Bibliografia: <textarea name="bibliografia"></textarea>

        <button type="submit" class="btn btn-success"> Salvar </button>
    </form>
```

- Crie a rota para o método store das turmas (routes/web.php)
```php
    Route::post('/disciplinas/{disciplina_id}/turmas','DisciplinaController@storeTurma');
```

- Crie o método storeTurma em app/Http/Controllers/DisciplinaController.php
```php
    public function storeTurma(Request $request, $disciplina_id)
    {
        $turma = new \App\Turma;
        $turma->ministrante = $request->ministrante;
        $turma->inicio = $request->inicio;
        $turma->fim = $request->fim;
        $turma->bibliografia = $request->bibliografia;
        $turma->disciplina_id = $request->disciplina_id;
        Disciplina::find($disciplina_id)->turmas()->save($turma);
        return redirect("/disciplinas/$disciplina_id");
    }
```

- Teste acessando a página show de alguma disciplina e tente cadastrar turmas
