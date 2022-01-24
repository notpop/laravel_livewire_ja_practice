Laravel + jetstream + livewire を試しに触ってみて日本語化までやったサンプルです

Laravelをインストール
```
curl -s "https://laravel.build/example-app?with=mysql" | bash
```

dockerを起動
```
sail up -d
```

jetstreamをインストール
```
composer require laravel/jetstream
```

livewireをインストール
```
sail php artisan jetstream:install livewire
```

```
npm install
npm run dev
sail php artisan migrate
```

ここまででlocalhostに接続すれば基本的には動く

ここからは日本語化
config/app.phpを書き換える
```
'timezone' => 'Asia/Tokyo',
'locale' => 'ja',
'fallback_locale' => 'ja',
'faker_locale' => 'ja_JP',
```

これだけだとjetstreamは日本語化されないので <br>
・　https://github.com/KSuzuki2016/laravel-jetstream-lang-ja <br>
・　https://github.com/takehirotakiuchi/laravel-8-resources-lang-ja <br>
上記repositoryからja.jsonを落としてきてresources/lang/配下に設置する。 <br>

今回これでもログアウトが日本語化されなかったのでja.jsonに記述を追加して対応した。
