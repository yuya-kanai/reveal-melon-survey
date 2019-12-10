# Melon Survey
背後にある技術

--

## Technologies
Tech | Description
---- | ---
Graphql | クエリ言語
Docker | 実行環境
Golang | サーバー側の言語
Gorm | サーバー側のORM
gqlgen | サーバー側のGraphqlフレームワーク

--

Tech | Description
---- | ---
Typescript | 型付きのJS (クライアント側)
Nuxt | クライアント側のフレームワーク(Vue)
Apollo |  クライアント側のGraphqlフレームワーク(Vue)


---

# Docker / K8S

--

[Docker](https://www.youtube.com/watch?v=u8dW8DrcSmo
) vs Vagrant + Ansible

--

## DockerScript
- ansibleのような冪等性がない
- Vagrantをdestroyするのと似ている
- キャッシングで高速化

--

## Benefits of Containerization
- 構成をすばやく変更
  - 中間層のキャッシュ

- ダウンロード速度
  - 最小のダウンロード時間(長くても1分程)

- 運用コスト
  - オーケストレーションで自動的にスケールアップ

--

```
FROM node:10

WORKDIR /usr/src/app

COPY package.json ./

RUN npm install

# 中間層のキャッシュ

COPY . .

EXPOSE 8080
CMD [ "node", "server.js" ]
```
-- 


# Orchestration
### 複数のコンテナを運用する

Docker-Compose, Kompose, Docker-swarm, K8s

--

## Cloud Services

多くのクラウドサービスは、自動スケーリングを利用できるコンテナ運用に対応しています


- ECS Fargate 
- ECS EC2
- EKS
- GKE
- Google Cloud Run

---

# Golang

--

## What is golang?

Googleによって開発され、C++を置き換える目的であった

--

## Strength of golang
- 並行性
- パフォーマンス
- C++よりもクリーン
- 小さなバイナリ=> 100x java
- 高速コンパイル
- DXをサポートするすばらしいツール
  - Formatter
  - Test
  - Lint
  - Benchmark
  - Document
  - Profiler

--

## Weakness

GOPATHで管理される依存関係

↓
 
Docker + Go mod

--

## Resources 
https://tour.golang.org/list

---

#### Before graphql
### SPA VS HTML Template

--

HTMLテンプレートとは？

PHP

--

SPAとは？

Vue, React

--

## LAMP 

Linux Apache Mysql PHP/Perl/Python

# ↓ 

## MERN

MongoDB Express React/Vue Node

--

なぜ人気か
- **モバイルアプリとRESTの統合**
- 関心事の分離(Seperation of Concerns)
- 環境の特化（webpack, Babel ...）
- インタラクティブなWebアプリの状態管理がより簡単に
- PWA


--

## Weakness of SPA
- SEO / Performance
- オブジェクトモデルの重複

--

#### SEO / Performance
## Web Framework != SPA

--

#### SPAを超えて
### SSRと静的サイト生成
##### Next.js Nuxt.js Gatsby.js ...

--

## LAMP 

Linux Apache Mysql PHP/Perl/Python

# ↓ 

## MERN

MongoDB Express React/Vue Node

↓

## JAM

Javascript, Api, Markup


--

## オブジェクトモデルの重複
Graphql / gRPCでコード生成

---

#### Before graphql
### Microservice vs Monolithic

APIはマイクロサービスか？

--

一般的には違う

--

マイクロサービスは、ビジネスドメインごとにサービスを分離すること

--

## Monolith

|          | サービス| 
|----------|:------:|
| Backend & Frontend (Server) |    ■   |


--

## API
|          | サービス| 
|----------|:------:|
| Backend  |    ■   |
| Frontend |    ■   |

--

## MicroService
|          | ユーザ  | 広告  | 閲覧履歴   |
|----------|:------:|:----:|:--------:|
| Backend  |    ■   |   ■  |     ■    |
| Frontend |    ■   |   ■  |     ■    |

--


## Why Microservice?
- 関心の分離
- スケーラビリティ

--

## Weakness of Microservice 
- Difficult to build with performance without a proper DevOps and Architect
  - Micro service cannot be done without CI
  - Unavoidable complexity that comes with scaling up

--

## 人気のツール
- K8S
- gRPC
- Graphql Federation

--

### Example Use of Microservice

<div class="mermaid">
graph TB;
    History-- gRPC ---AD;
    User-->GraphQL;
    AD-->GraphQL;
    History-->GraphQL;
    GraphQL-->Mobile_App;
    GraphQL-->Desktop;
    GraphQL-->Mobile_Browser;
</div>

---

# Graphql
APIのクエリ/ 未来的なREST

--

## Graphql??
|          | サービス| 
|----------|:------:|
| Backend  |    ■   |
| Graphql Scheme |    ■   |
| Frontend |    ■   |

--

実装ではなく仕様

公式のライブラリまたはフレームワークは無い

（Apolloは実質的に

公式の実装...）

--

## Server implementation 
- Apollo Server (Node)
- grpahql-ruby
- graphql-java
- graphql-php
- gqlgen(go) <==
- graphene(python)

--

## Client implementation
- Apollo Client <==
- Relay

--

#### Examples
## REST

URL
```
GET /blog/author/<id> 

↓

GET /blog/author/<id>/posts?last=3

↓

GET /blog/author/<id>/topics?last=3
```

--

## Graphql Request
```
{
  author (id: 6) {
    name 
    posts (last: 3) {
      title
    }
    topics (last : 3) {
     name
    }
  }
}
```


--

## Graphql Response
```
{
  "data" : {
    "author" : {
      "name" : "Adhithi Ravichandran",
      "posts" : [
        { title: "React vs. Vue : A Wholesome Comparison"},
        { title: "React Lifecycle Methods: A Deep Dive"},
        { title: "5 Essential Skills A Frontend Developer Should Possess"}
      ],
      "topics" : [
        { name: "React and Vue"},
        { name: "React"},
        { name: "General"}
      ]
    }
  }
}
```
<small> https://medium.com/@adhithiravi/graphql-vs-rest-a-comparison-16a2f5f29198
</small>


--

## Strength

- 柔軟なクエリ

- スキーマから生成されたコード

- graphql playgroundのようなすばらしいツールを使用したAPIの生成されたドキュメント

- バックエンドとフロントエンドの同時開発
  - graphql-inspectorを使用して偽データを生成する

- @deprecated


--

## resources
https://principledgraphql.com/

--

# Gotchas

QueryとMutationタイプは別物　

循環参照はリゾルバーで処理できます

--

# Apollo-Client

-VueX / Reduxに代わる強力なキャッシュ
-フラグメントのインポートによる再利用可能なクエリ
-graphql-codegenを使用したJS / TSコード生成



---

# Front End
Typescript/Nuxt/Vue-Bootstrap/ES6

--

## Nuxt is powerful
- VueX 
- Vue Router
- UI framework choices (e.g. Bootstrap)
- Jest 
- Eslint 
- Prettier 
- SSR support

--

## Typescript is powerful
Typescriptをセットアップするのは大変です

Typescript + Graphqlは効率的です

--

タイプスクリプトを学習するとき、混乱する場合は「any」を使用します

＆

eslintで詳しくなった時にときにリファクタリングする

--

## Restructuring Data with ES6
- Destructuring
- 分割代入(Destructuring)
- スプレッド演算子 (Spread Operator)
- レスト演算子　(Rest parameter)

--

## Vue's MVVM

- Model(Apollo/Graphql)
- Model View(Vue Binded Models)
- View(Vue Components)

--

## Model to Model View Conversion

```
const { // Destructuring
    Model,
    Salesperson,
    SalespersonID,
    ...Filtered // Rest operator
} = clientModel 

let salesperson: string
if (Salesperson == null) {
    salesperson = 'No Salesperson'
} else {
    salesperson = Salesperson.Name // Salesperson Obj to Str
}

const clientModelView = {
    ID: Model.ID,
    Salesperson: salesperson,
    ...Filtered // Spread Operator
}
```
<small> EditClient.vue</small>

---

# Test

--

## TDDの利点
- コードをテストするためにインターフェイスをクリック/入力する必要はありません
- 成功した場合、目で見分ける必要はありません
- 再利用可能な自動テストが得られます

--

## Milestones for mastering testing method

<div class="mermaid">
graph LR
    A(basic testing) --> B(table driven testing)
    B --> C(golden unit testing)
</div>

--

## Milestones for Testing Environments

<span class="mermaid">
graph LR
    C{Legacy_Code?}
    C -->|False| D(TDD)
    C -->|True| E(Code Coverage)
    E -->B(Continuous Integration)
    D -->B(Continuous Integration)
    B -->A(Continuous Delivery)
    A -->X(Continuous Deployment)
</span>


---

# CI / CD

--

Continuous delivery of containers (Spinnaker)

--

Backend Benchmark chart

--

Frontend Lighthouse chart

--

Diffing Frontend Screenshot

--

GraphQL Inspector

---

# Introspection

Gormの改善（Dry、KISS、YAGNI）

ファイルアーキテクチャ（MVVM）

フロントエンド側でテストする
https://qiita.com/ykhirao/items/becd9be857dbe6804314

Chaos Engineering

Mono repo??

Microservice