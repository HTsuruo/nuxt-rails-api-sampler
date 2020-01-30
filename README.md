# nuxt-rails-api-sampler
* Nuxt.js + Rails(APIモード) Sampler
* Railsアーキテクトに `MVC + Service + Repository` を採用してみた


## Initial Setup.
* `rails new` すると、いつものrailsツリーが作られる
	* マウントしているので、ホストにも同様のツリーが作られる
	* Gemfileの上書き、依存関係排除、パッケージのスキップ、APIモード指定する

```
$ docker-compose run app rails new . --force --no-deps --database=mysql --skip-bundle --api
```

* DB使う場合はcreateも必要

```
$ docker-compose run app rails db:create
```

* `create-nuxt-app` すると、いつものnuxtツリーが作られる

```
$ docker-compose run frontend npx create-nuxt-app --no-deps
```
