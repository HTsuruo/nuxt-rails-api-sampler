# nuxt-rails-api-sampler
* Nuxt.js + Rails Sampler
* NuxtはSSR予定だけど動かない..（2020/02/04）
* Railsアーキテクトに `MVC + Service + Repository` を採用してみたい


## Env.

```
## backend
rails: '~> 6.0.2'
ruby: '2.7.0'

## frontend
node.js: 11.14.0-alpine
nuxt.js: ^2.0.0

```

## Run.
```
$ docker-compose up

※初回実行時は下記コマンドにてDB作成
$ docker-compose run --rm backend rails db:create
```


## Memo.
#### Backend

* `rails new` すると、いつものrailsツリーが作られる
	* マウントしているので、ホストにも同様のツリーが作られる
	* Gemfileの上書き、依存関係排除、パッケージのスキップ、APIモード指定する

```
$ docker-compose run backend rails new . --force --no-deps --database=mysql --skip-bundle --api
```

#### Frontend

* `create-nuxt-app` すると、いつものnuxtツリーが作られる
	* コンテナ側で `npm install -g create-nuxt-app` を忘れずに
```
$ docker-compose run --rm frontend npx create-nuxt-app
```
