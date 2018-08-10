# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 12 - Implementando a busca de disciplinas

- Crie o método search no DisciplinaController
```php
    public function search(Request $request)
	{
		$text = $request->text;
		$disciplinas = Disciplina::where('titulo', 'LIKE', "%{$text}%")->get();
		return view('disciplinas.index',compact('disciplinas'));
	}
```

- Adicione o método search ao except do auth, no construtor do DisciplinaController
```php
	$this->middleware('auth')->except(['index','show', 'search']);
```

- Crie a rota para o método search - em routes/web.php
```php
	Route::post('/disciplinas/search','DisciplinaController@search');
```

- Adicione o campo de busca ao layout master - resources/views/layouts/master.blade.php
```php
	<form method="POST" action="/disciplinas/search">
		{{ csrf_field() }}
		<input name="text" type="text">
		<button type="submit"> Buscar </button>
	</form>
```

- Teste no navegador em http://localhost:8000
