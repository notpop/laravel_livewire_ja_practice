Laravel8 + jetstream + livewire を試しに触ってみて日本語化までやったサンプルです

Laravelをインストール
```
curl -s "https://laravel.build/example-app?with=mysql" | bash
```

dockerを起動
```
cd example-app
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
langの追加
```
php -r "copy('https://readouble.com/laravel/8.x/ja/install-ja-lang-files.php', 'install-ja-lang.php');"
php -f install-ja-lang.php
php -r "unlink('install-ja-lang.php');"
```

これだけだとjetstreamは日本語化されないので <br>
・　https://github.com/KSuzuki2016/laravel-jetstream-lang-ja <br>
・　https://github.com/takehirotakiuchi/laravel-8-resources-lang-ja <br>
上記repositoryからja.jsonを落としてきてresources/lang/配下に設置する。 <br>
※当然だがこのrepositoryのものを丸々使っても良い <br>

今回これでもログアウトが日本語化されなかったのでja.jsonに記述を追加して対応した。


さらに参考までにロゴを下記からコピーして置き換えるとロゴを変更できる <br>
https://tablericons.com/
