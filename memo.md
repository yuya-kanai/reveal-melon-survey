# Melon Survey
Technology behind this tool

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
- No idempotency like ansible
- Similar to destroying a vagrant image
- Faster with caching

--

## Benefits of Containerization
- Quickly change configuration
  - Caching middle layer

- Download Speed
  - Minimal download time

- Operational cost
  - Automatically scale up with Orchestration 

--

# Orchestration
### Operating multiple containers

Docker-Compose, Kompose, Docker-swarm, K8s

--

## Cloud Services

Many cloud services support Container operation which support auto scaling


- ECS Fargate 
- ECS EC2
- EKS
- GKE
- Google Cloud Run
- EC2/GCE with K8S and manual provisioning

---

# Golang

--

## What is golang?

Developed by Google, to replace C++

--

## Strength of golang
- Concurrency
- Performant => 30x php
- Cleaner than C++
- Small Binary => 100x java
- Fast compilation
- Amazing tooling to support DX
  - Formatter
  - Test
  - Lint
  - Benchmark
  - Document
  - PProf

--

## Weakness

Dependencies Managed with GOPATH 

↓
 
Docker + Go mod

--

## Resources 
https://tour.golang.org/list

---

#### Before graphql
### SPA VS HTML Template

--

What are HTML TEMPLATEs?

PHP

--

What are SPAs?

Vue, React

--

## LAMP 

Linux Apache Mysql PHP/Perl/Python

# ↓ 

## MERN

MongoDB Express React/Vue Node

--

Why the popularity
- **Mobile apps integration with REST**
- Separation of Concerns
- Specialization in Ecosystem
- Easier state management in interactive web apps
- PWA


--

## Weakness of SPA
- SEO / Performance
- Duplication of Object Models

--

#### SEO / Performance
## Web Framework != SPA

--

#### Beyond SPA
### SSR and static site generation
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

## Duplication of object models
Graphql / gRPC for Code Generation

---

#### Before graphql
### Microservice vs Monolithic

Are APIs Microservice?

--

Usually not

--

Microservice is more about isolating sections of a service by business domain

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
- Seperation of concerns
- Scalability

--

## Weakness of Microservice 
- Difficult to build with performance without a proper DevOps and Architect
  - Micro service cannot be done without CI
  - Unavoidable complexity that comes with scaling up

--

## Popular Tools
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
A query language for your API / Replacement for REST

--

## Graphql??
|          | サービス| 
|----------|:------:|
| Backend  |    ■   |
| Graphql Scheme |    ■   |
| Frontend |    ■   |

--

Specification not an implementation

No official library or framework

(Although apollo is virtually the

official implementation...)

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

- Flexible Query

- Generated Code from schema

- Generated Documentation for APIs with amazing tools like graphql playground

- Simultaneous development of backend and frontend 
  - Generate fake data using graphql-inspector

- @deprecated


--

## resources
https://principledgraphql.com/

--

# Gotchas

Query types and mutation types are separate

Circular dependency can be handled with resolvers

--

# Apollo-Client

- Powerful Caching replacing VueX / Redux
- Reusable Query through Importing Fragments
- JS/TS Code Generation with graphql-codegen



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

While setting up Typescript is painful 

Typescript + Graphql is efficient

--

When learning typescript use "any" if confused 

&

refactor any when you know better with eslint

--

## Restructuring Data with ES6
- Destructuring
- Spread Operator
- Rest parameter

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

Benefits of TDD
- No need to click / type on interfaces to test your code
- No need to diff with your eyes if it succeeded
- You get reusable automated test function

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

Improve Gorm(Dry, KISS, YAGNI)

File Architecure (MVVM)

Test on Frontend side
https://qiita.com/ykhirao/items/becd9be857dbe6804314

Chaos Engineering

Mono repo??

Microservice
