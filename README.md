# Agent Trip

### ✈️ Planejamento Simples, Viagens Perfeitas.

> *"Toda viagem boa poderia ter sido inesquecível."*
>
> Entre o desejo de viajar e a experiência de viver existe um abismo de complexidade, fragmentação e decisões solitárias. O Agent Trip é a ponte — transforma preparação em descoberta, para que o desconhecido deixe de ser ameaça e vire a melhor parte da viagem.

<a href="https://agenttrip.com.br">
  <img src="https://img.shields.io/badge/Website-agenttrip.com.br-14B8A6?style=for-the-badge&logo=safari&logoColor=white" alt="Agent Trip Website" />
</a>
<a href="https://apps.apple.com/br/app/agent-trip-planejar-viagem/id6749809858">
  <img src="https://img.shields.io/badge/App_Store-Download-000000?style=for-the-badge&logo=apple&logoColor=white" alt="App Store" />
</a>
<a href="https://play.google.com/store/apps/details?id=br.com.agenttrip.app">
  <img src="https://img.shields.io/badge/Google_Play-Download-414141?style=for-the-badge&logo=google-play&logoColor=white" alt="Google Play" />
</a>

---

## Índice
- [Sobre o Projeto](#sobre-o-projeto)
- [Status Atual](#status-atual)
- [Arquitetura](#arquitetura)
  - [Landing Page](#landing-page)
  - [Backend/APIs](#backendapis)
  - [App Mobile](#app-mobile)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Contato](#contato)

---

## Sobre o Projeto

O **Agent Trip** é um app de viagem brasileiro focado em mulheres de 25 a 44 anos que viajam com família, amigas ou em casal. Desenvolvido de ponta a ponta por um solo founder — do produto à infraestrutura.

**O problema:** Quem viaja hoje enfrenta dois caminhos — pesquisar sozinha (15 abas, planilha, WhatsApp, noites perdidas, ninguém agradece) ou "resolver na hora" (gasta mais, vive menos, volta dizendo "foi bom"). O Agent Trip é o Caminho 3.

**A solução — 3 pilares:**
- 🔍 **Descoberta** — Destinos e experiências personalizadas que a pessoa não encontraria sozinha
- 📋 **Centralidade** — Viagem completa em um lugar só: dia a dia, orçamento, cotações, tudo integrado
- 📡 **Acompanhamento** — Cotações em tempo real, notificações e controle financeiro do desejo ao retorno

**Diferencial:** Gera uma viagem personalizada — dia a dia, com orçamento — em 30 segundos. Não em 3 semanas.

**Números atuais:** 200+ downloads · ~100 cadastros (50% conversão) · Primeiras transações reais · App Store + Google Play

---

## Status Atual

| Camada | Status |
|--------|--------|
| **Landing Page** | ✅ Estável — Hero, geração de roteiros AI, blog, pagamento integrado, SEO |
| **Backend/APIs** | ✅ Estável — 15+ módulos (auth, pagamentos, IA, cotações, localização, conteúdo, e-mail, push) |
| **App Mobile** | ✅ Publicado — App Store + Google Play. Auth, onboarding, criação de viagens, favoritos, cotações |

---

## Arquitetura

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=agent-trip&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=dracula&locale=en&hide_border=false" height="150" alt="stats graph"  />
</div>

### 📂 Estrutura de Repositórios

| Repositório | Descrição | Stack |
|-------------|-----------|-------|
| [`app`](https://github.com/agent-trip/app) | App mobile (iOS + Android) | Flutter, Dart, BLoC, GoRouter, Firebase |
| [`api`](https://github.com/agent-trip/api) | Backend e APIs | NestJS, TypeScript, Prisma, PostgreSQL, GCP |
| [`landing-page`](https://github.com/agent-trip/landing-page) | Landing page + blog | Next.js, React, Tailwind, Firebase |

> 🔒 Os repositórios são privados. Acesso disponível sob solicitação para avaliação técnica — entre em contato via [LinkedIn](https://www.linkedin.com/in/marcos-lacerda).

---

### Landing Page

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nextjs/nextjs-original.svg" height="30" alt="nextjs logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" height="30" alt="react logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/firebase/firebase-plain.svg" height="30" alt="firebase logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" height="30" alt="vscode logo"  />
</div>

**Arquitetura & Stack**
- Next.js **15.2.4** (App Router) com React 19; renderização estática forçada (`dynamic='force-static'`, `revalidate=false`).
- Layout com SEO avançado + JSON-LD (`src/app/layout.tsx`, `src/lib/jsonld.ts`), `sitemap` e `robots`.
- Pipeline de inscrição: **HeroSection → EmailSubscriptionForm → /api/subscribe** com validação **Firebase App Check** e **Mailchimp**.
- Segurança: `middleware` com CORS e rate limit (`subscribeRateLimit`).
- UI: **Tailwind 4**, **shadcn/ui**, utilitários `cn/CVA`.

**Implementações-chave**
- `EmailSubscriptionForm` valida e bloqueia submissão sem App Check; feedback visual com ícones.
- API `/api/subscribe` integra **Mailchimp**, valida ambiente, decodifica tokens via **Firebase Admin**.
- `middleware` injeta cabeçalhos e limita 3 req/min para `/api/subscribe`.

---

### Backend/APIs

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" height="30" alt="nodejs logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" height="30" alt="typescript logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nestjs/nestjs-original.svg" height="30" alt="nestjs logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg" height="30" alt="postgresql logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/firebase/firebase-plain.svg" height="30" alt="firebase logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/googlecloud/googlecloud-original.svg" height="30" alt="googlecloud logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" height="30" alt="vscode logo"  />
</div>

**Arquitetura & Stack**
- **NestJS 11** (TS 5.7, Node 20). Módulos: `Common`, `Currency`, `Content`, `LocationSearch`, `Health`.
- Persistência híbrida: **Prisma + PostgreSQL** (Accelerate) e **Firestore** via Firebase Admin.
- Integrações: HG Brasil (cotações), **Mapbox Search Box**, **Google Places**, **Cloud Monitoring**, **Firebase Storage**.
- **Swagger** em `/api/docs`, CORS e prefixo global `/api`.

**Implementações-chave**
- **Currency**: CRUD, histórico, sync com provedor externo grava em Firestore e PostgreSQL; scheduler opcional.
- **Content**: CRUD com upload de thumbnail ao Firebase Storage; filtros por tipo/data/tags; espelhamento em PostgreSQL.
- **LocationSearch**: proxy com cache, tokens de sessão (autocomplete/detalhes), valid. de origem.
- **Health**: liveness/readiness via `@nestjs/terminus`.
- Infra: Firebase Admin com múltiplas credenciais e suporte a emuladores; regras versionadas (`firestore.rules`, `storage.rules`).
- Monitoramento: interceptors para métricas HTTP/DB no Cloud Monitoring.

**CI/CD & Qualidade**
- GitHub Actions `release/**`: build, auth GCP, **Cloud Run** deploy, regras Firestore/Storage, Cloud Scheduler.

---

### App Mobile

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flutter/flutter-original.svg" height="30" alt="flutter logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/dart/dart-original.svg" height="30" alt="dart logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/androidstudio/androidstudio-original.svg" height="30" alt="androidstudio logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/firebase/firebase-plain.svg" height="30" alt="firebase logo"  />
</div>

**Arquitetura & Stack**
- Flutter com camadas: `core` (infra/constantes/serviços), `domain` (entidades/DTOs/VOs), `features` (controllers **Cubit** + presentation) e `shared` (componentes).
- Navegação: **GoRouter** com `ShellRoute` e `NavigationScaffold` (bottom navigation).
- DI: **injectable/get_it**; rede **Dio**; estado **flutter_bloc**; utilitários **dartz**, **json_serializable**.
- Inicialização: `runZonedGuarded`, `FirebaseSetup().initializeCore`, `configureDependencies()`, `MaterialApp.router` com `AppRouter`.
- Pré-aquecimento Firebase: **App Check**, **Remote Config**, **Analytics**, refresh do **FirebaseAuth**.

**Implementações-chave**
- **Auth**: login anônimo, upgrade de credenciais, sociais (Facebook/Google/Apple) com cache, ATT e validação.
- **FirestoreService**: orquestra DTO↔domínio, upload de docs.
- **CurrencyRatesService**: stream única com `BehaviorSubject` + watchers Firestore.
- **LocationService**: chama API própria via Dio com token do `IAuthService` + Crashlytics; fallback para mocks.
- **MapService**: abre Google/Apple/Waze/Web.
- Logging/erros: `LoggingService` e `ErrorService` → Crashlytics.

---

## Tecnologias Utilizadas

- **Landing Page:** Next.js 15.2.4, React 19, Tailwind 4, shadcn/ui, Firebase (App Check/Admin), Mailchimp, framer-motion, rate limit/CORS middleware.
- **Backend/APIs:** NestJS 11 (TS 5.7, Node 20), Prisma + PostgreSQL (Accelerate), Firebase Admin (Firestore/Storage), Mapbox, Google Places, Cloud Monitoring, Swagger.
- **App Mobile:** Flutter, flutter_bloc, go_router, injectable/get_it, dio, dartz, json_serializable, Firebase (Auth/Remote Config/App Check/Analytics), file_picker, map_launcher, app_tracking_transparency.

---

## Contato

<div align="left">
  <a href="mailto:contato@agenttrip.com.br" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Gmail&logo=gmail&label=&color=D14836&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="gmail logo"  />
  </a>
  <a href="https://www.instagram.com/agent.trip/" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Instagram&logo=instagram&label=&color=E4405F&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="instagram logo"  />
  </a>
  <a href="https://agenttrip.com.br" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Website&logo=safari&label=&color=14B8A6&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="website logo"  />
  </a>
  <a href="https://www.linkedin.com/in/marcos-lacerda" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Founder&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="linkedin logo"  />
  </a>
</div>
