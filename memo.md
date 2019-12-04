# Melon Survey
Technology behind this tool

---

### SPA VS HTML Template

--

What is HTML TEMPLATE?

--

What is SPA?

--

## LAMP 

Linux Apache Mysql PHP/Perl/Python

# ↓ 

## MERN

MongoDB Express React/Vue Node

--

Why the popularity
- Mobile apps integration with REST
- Team Isolation
- Specialization in Ecosystem
- Interactive content with JS
- PWA

--

Weakness of SPA
- SEO
- Duplication of Models

--

## Web Framework != SPA

--

## Beyond spa
### SSR and static site generation
Next.js Nuxt.js Gatsby.js ...

--

## Duplication of object models
Graphql / gRPC for Code Generation

---

### Microservice vs Monolithic

Are APIs Microservice?

--

No 

--

Microservice is more about isolating sections of a service by business domain

From GUI to Database

--

Why Microservice?
- Responsibility Isolation
- Scalability

--

## Weakness of Microservice 
- Difficult to build with performance without a proper DevOps and Architect
  - Micro service cannot be done without CI
  - Unavoidable complexity that comes with scaling up

--

## Popular Tools
- gRPC
- K8S
- Graphql Federation

---

# Docker / K8S

--

Docker vs Vagrant + Ansible
https://www.youtube.com/watch?v=u8dW8DrcSmo

--

## DockerScript
- No idempotency like ansible
- Similar to destroying a vagrant image
- Faster with caching

--

## Benefits of Containerization
### Quickly change configuration
- Caching middle layer

### Download Speed
- Minimal download time

### Operational cost
- Automatically scale up with Orchestration 

--

# Orchestration
### Operating multiple containers

Docker-Compose, Kompose, Docker-swarm, K8s

--

## Cloud Services

Many cloud services support Container operation which support auto scaling

--

- ECS Fargate 
- ECS EC2
- EKS
- GKE
- Google Cloud Run
- Anthos
- EC2/GCE with K8S and provisioning

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
- Small Binary
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

Lack of generics

↓
 
No solution

Dependencies Managed with GOPATH 

↓
 
Docker + Go mod


---

# Graphql
A query language for your API / Replacement for REST

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
- gqlgen(go)
- graphene(python)

--

## Client implementation
- Apollo Client
- Relay

--

## Strength

- Flexible Query

- Generated Code from schema

- Generated Documentation for APIs with amazing tools like graphql playground

- Simultaneous development of backend and frontend 
  - Generate fake data using graphql-inspector

- @deprecated

DEMO

--

# Gotchas

Query types and mutation types are separate

Circular dependency can be handle with resolvers

--

# Gqlgen

Code Generation

Directives

--

# Authentication
Jwt vs Session

--

# Solution
Splitting JWT

--

## Graphql Directives

--

# Authorization

Doing join to ensure the user is the one mutating or referencing is costly

--

### Caching with Redis (Concept)

Values mutated or accessed are generally queried beforehand
Session keys are connected to Protobuffer val on Redis with dictionary which contain ids of manipulatable objects

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
- UI framework (e.g. Bootstrap)
- Jest 
- Eslint 
- Prettier 
- SSR support

--

While setting up Typescript is painful 

Typescript + Graphql is good

--

When learning typescript use "any" if confused 

&

refactor any when you know better with eslint

--

## Restructuring Data with ES6
- Destructuring
- Spread Operator
- Key/property shorthand

---

# Test

--

## Milestones for mastering testing method
basic testing 

-> table driven testing

-> golden unit testing

--

## Milestones for Testing Environments
Fresh Code ? TDD : Code Coverage -> Continuous Integration -> Continuous Delivery -> Continuous Deployment

---

# CI / CD

--

Continuous delivery of docker 

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

Gorm(Dry, KISS, YAGNI)

File Architecure

Test on Frontend side
https://qiita.com/ykhirao/items/becd9be857dbe6804314

Mono repo??

Microservice
