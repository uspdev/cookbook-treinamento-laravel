# Treinamento - Laravel Básico

Cookbook do treinamento de Laravel básico, para a resolução das issues propostas.

## Issue 7 - Criar model e migrations para Turma

- Adicione o método disciplina ao model Turma (app/Turma.php)
```php
    public function disciplina()
    {
        return $this->belongsTo('App\Disciplina');
    }
```

- Adicione o método turmas ao model Disciplina (app/Disciplina.php)
```php
    public function turmas()
    {
        return $this->hasMany('App\Turma');
    }
```

- Faça testes no Tinker
```php
    php artisan tinker

    >>> $d = new Disciplina;
    >>> $d->ementa = 'Filosofia Grega e Romana'
    >>> $d->titulo = "Filosofia I"
    >>> $d->save()
    >>> 
    >>> $t = new Turma;
    >>> $t->ministrante = 'Pedro'
    >>> $t->inicio = '2015-10-10'
    >>> $t->fim = '2016-10-10'
    >>> $t->disciplina_id = $d->id
    >>> $t->save()
    >>> 
    >>> $d->turmas
    >>> $d->turmas[0]->ministrante
    >>> $t->disciplina
    >>> $t->disciplina->ementa
```
