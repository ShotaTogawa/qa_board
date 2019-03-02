## [メモ]]
・対話型シェル: `php artisan tinker`  
・`str_slug(x)`: slugフォーマットに変換する。`ex)str_slug('hello world') -> hello-world`

#### seedの生成  
・seedの生成コマンド: `php artisan migrate:fresh --seed`  
・ [factory](https://qiita.com/fagai/items/7f63d651cbed3664b758)  
・ [Eloquesntのリレーション](https://qiita.com/fagai/items/7f63d651cbed3664b758)
・ usersテーブルのidを外部キーとして参照する。 `$table->foreign('user_id')->references('id')->on('users')->onDelete('cascade');`  
・CASCADE: 親テーブルに対して更新を行うと子テーブルで同じ値を持つカラムの値も合わせて更新される


```php
// make()がnew Model()に該当し、create()がModel::create()に該当する（呼び出し時にINSERTされるかされないかの違い、後者がされる）。
factory(App\User::class, 3)->create()->each(function($u) {
            $u->questions()
              ->saveMany(
                  factory(App\Question::class, rand(1,5))->make()
              );
        });
```

####controllerからview
[controllerからviewへの変数の受け渡し](https://qiita.com/ryo2132/items/63ced19601b3fa30e6de)


 ## Answers Table Schema
 ・id  
 ・user_id  
 ・question_id  
 ・body  
 ・votes_control  
 ・created_at, updated_at