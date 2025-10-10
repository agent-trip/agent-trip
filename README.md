# Agent Trip

> Planejamento Simples, Viagens Perfeitas.

## Índice
- [Sobre o Projeto](#sobre-o-projeto)
- [Arquitetura](#arquitetura)
  - [Landing Page](#landing-page)
  - [Backend/APIs](#backendapis)
  - [App mobile](#app-mobile)
- [Funcionalidades](#funcionalidades)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Contribua](#contribua)
- [Agradecimentos e Referências](#agradecimentos-e-referências)

---

## Sobre o Projeto
# Proposta de Valor

# Agent Trip

Planejamento Simples, Viagens Perfeitas

### **Proposta de Valor**

> Organize sua viagem do início ao fim. Desde a escolha seu destino ao último dia de aventura, com planejamento inteligente e controle total do seu orçamento e atividades, o Agent Trip oferece tudo o que você precisa para transformar suas viagens em experiências inesquecíveis.
> 

---

### Descrição Detalhada:

> O **Agent Trip** é o aplicativo essencial para quem busca organizar e planejar viagens com praticidade e precisão. Com foco em proporcionar controle total e personalização, o app integra todas as etapas do planejamento de uma viagem em uma única plataforma.
> 

---

### Entrega de Valor:

<aside>
💡

**O que Agent Trip te proporciona ?**

Planejamento Simples, Viagens Perfeitas

</aside>

1. **Busca por Destinos Ideais:** *Descubra novos lugares com base em seus interesses e histórico de viagem.*
    - Busca inteligente de destinos
    - Duração da viagem
    - **Melhores Datas para Viajar:** *Receba sugestões das datas mais convenientes e econômicas para sua viagem.*
        - Análise de melhor período (preços e clima)
        - Planejamento adaptável para viagens com datas fixas ou flexíveis.
        - Visualização de preços e disponibilidade para diferentes períodos.
        
2. **Passagens Áreas**
    - Busca e comparação de voos
    - Alertas de melhor momento para compra
    - Monitoramento de promoções
    - Filtros de preferências (horários, companhias, escalas)
    - Gestão de milhas e programas de fidelidade
    - Definição de budget para gasto com Passagens Áreas
        - Tracking dos preços das hospedagem desejadas e sua conformidade com budget definido
        
3. **Acomodação**
    - Busca de hospedagens por data
    - Gestão de check-in/check-out
    - Comparativo de preços e localizações
    - Reservas integradas
    - Definição de budget para gasto com hospedagem
        - Tracking dos preços das Passagens Áreas desejadas e sua conformidade com budget definido
        
4. **Roteiro de Atividades**
    - Organização dia a dia
    - Horários de funcionamento
    - Tempo estimado em cada local
    - Distâncias e deslocamentos
    - Reservas em restaurantes
    - Ingressos para atrações
    
5. **Controle Financeiro**
    - Orçamento total da viagem
    - Divisão por categorias:
        - Hospedagem
        - Transporte
        - Alimentação
        - Atrações
        - Compras
    - Tracking de gastos planejados vs. realizados
    - Cotação de moedas em tempo real
    
6. **Aluguel de Veículos e Locomoção**
    - Aluguel de veículos
        - Comparativo de preços e locadoras
        - Diferentes categorias de veículos
        - Pontos de retirada e devolução
    - Transporte público
        - Passes e bilhetes
        - Rotas principais
    - Transfers
    - Aplicativos de mobilidade locais
    - Estimativa de custos por opção
    - Definição de budget para gasto com locomoção
        - Tracking dos preços de aluguel de carro desejados e sua conformidade com budget definido
        
7. **Aquisição de Moeda Estrangeira** : *Organização e planejamento geram **economia** financeira e uma viagem tranquila*
    - Planejamento de câmbio
        - Tracking de cotações
        - Alertas de melhor momento para compra
        - Comparativo entre casas de câmbio
        - Simulador de valores
    - Modalidades de câmbio
        - Papel moeda
        - Cartão pré-pago
        - Cartão de crédito internacional
    - Definição de estratégia de uso
        - Quanto levar em cada modalidade
        - Onde usar cada tipo de pagamento
        - Reserva de emergência
    - Definição de budget para aquisição de moeda estrangeira
        - Tracking de preços das moedas desejadas e sua conformidade com budget definido
        

### Queremos ir além :

<aside>
💡

**O que mais Agent Trip pode te proporciona ?**

“Planeje com precisão, viaje sem preocupações”

</aside>

1. **Recomendações Personalizadas:** *Explore sugestões únicas de lugares, eventos e atrações que combinam com seu perfil.*
    
    **AI Travel Assistant**
    
    - Sugestões contextuais
    - Otimização de roteiros
    - Dicas de planejamento
    - Sugestões em tempo real para ajustar o planejamento
    
2. **Conteúdos Exclusivos:** *Acesse artigos, vídeos e guias detalhados sobre seu destino, reunidos de diversas fontes na internet.*
    - Acesso a guias, artigos e vídeos sobre destinos e experiências.
    - Dicas de viajantes
    - Avaliações de locais
    
3. **Pacotes Personalizados para Eventos**
    - Planejamento colaborativo para viagens em grupo e financiamento coletivo para experiências únicas.
    
4. **Experiências Inspiradoras**
    - Sugestões de passeios e atividades exclusivas no destino.
    
5. **Social e Compartilhamento**
    - Compartilhamento de roteiros
    - Dicas da comunidade
    - Experiências recomendadas

<aside>
💡

Com o Agent Trip cada viagem se torna uma experiência perfeitamente planejada e personalizada, garantindo que você aproveite ao máximo cada momento.


---

## Arquitetura

### Landing Page
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

**Funcionalidades**
- Hero pré-lançamento, captura de e-mail com bloqueio automático sem App Check, seções “Como Funciona” e “Features”, SEO + JSON-LD + sitemap/robots. **Status:** estável.

**CI/CD & Qualidade**
- Lint: `next lint`.  
- Testes automatizados, pipelines e badges: **Não encontrado** no repositório.

**Licença e Metadados**
- Licença: **Não encontrado**.
- Observação: credenciais `firebase-key.json` versionadas para uso local — revisar segurança.

---

### Backend/APIs
**Arquitetura & Stack**
- **NestJS 11** (TS 5.7, Node 20). Módulos: `Common`, `Currency`, `Content`, `LocationSearch`, `Health`.
- Persistência híbrida: **Prisma + PostgreSQL** (Accelerate) e **Firestore** via Firebase Admin.
- Integrações: HG Brasil (cotações), **Mapbox Search Box**, **Google Places**, **Cloud Monitoring**, **Firebase Storage**.
- **Swagger** em `/api/docs`, CORS e prefixo global `/api`.

**Implementações-chave**
- **Currency**: CRUD, histórico, sync com HG Brasil; grava em Firestore e PostgreSQL; scheduler opcional.
- **Content**: CRUD com upload de thumbnail ao Firebase Storage; filtros por tipo/data/tags; espelhamento em PostgreSQL.
- **LocationSearch**: proxy com cache, tokens de sessão (autocomplete/detalhes), valid. de origem.
- **Health**: liveness/readiness via `@nestjs/terminus`.
- Infra: Firebase Admin com múltiplas credenciais e suporte a emuladores; regras versionadas (`firestore.rules`, `storage.rules`).
- Monitoramento: interceptors para métricas HTTP/DB no Cloud Monitoring.

**Funcionalidades**
- Gestão de cotações com histórico e sync externa; endpoints de conteúdo; busca/autocomplete/detalhes de locais; health-checks; endpoint raiz de verificação.  
**Status formal:** **Não encontrado** no repositório.

**CI/CD & Qualidade**
- GitHub Actions (`.github/workflows/deploy.yml`) em `release/**`: build, auth GCP, **Cloud Run** deploy, regras Firestore/Storage, Cloud Scheduler.  
- `lint`/`test` existem mas **não** executados no workflow.  
- Cobertura/badges: **Não encontrado**.  
- Testes presentes apenas para `app.controller` (unit/e2e) e “Hello World!”.

**Licença e Metadados**
- `package.json`: **UNLICENSED**.  
- Arquivo LICENSE: **Não encontrado**.  
- Autor/metadata: não preenchidos.

---

### App mobile
**Arquitetura & Stack**
- Flutter com camadas: `core` (infra/constantes/serviços), `domain` (entidades/DTOs/VOs), `features` (controllers **Cubit** + presentation) e `shared` (componentes).
- Navegação: **GoRouter** com `ShellRoute` e `NavigationScaffold` (bottom navigation).
- DI: **injectable/get_it**; rede **Dio**; estado **flutter_bloc**; utilitários **dartz**, **json_serializable**.
- Inicialização: `runZonedGuarded`, `FirebaseSetup().initializeCore`, `configureDependencies()`, `MaterialApp.router` com `AppRouter`.
- Pré-aquecimento Firebase: **App Check**, **Remote Config**, **Analytics**, refresh do **FirebaseAuth**.

**Implementações-chave**
- **Auth**: login anônimo, upgrade de credenciais, sociais (Facebook/Google/Apple) com cache, ATT e validação.
- **FirestoreService**: orquestra DTO↔domínio, upload de docs; várias operações ainda em `mock/TODO`.
- **CurrencyRatesService**: stream única com `BehaviorSubject` + watchers Firestore.
- **LocationService**: chama API própria via Dio com token do `IAuthService` + Crashlytics; fallback para mocks.
- **MapService**: abre Google/Apple/Waze/Web.  
- Logging/erros: `LoggingService` e `ErrorService` → Crashlytics; `BusinessAnalyticsService` com TODOs.

**Funcionalidades**
- **Estáveis**: Splash (aquecimento + roteamento), autenticação (email/sociais/upgrade anônimo), onboarding (preferências), Home (perfil, conteúdos, favoritos, cotações), Trips (listar/criar/validar períodos/merge destinos, atualização via backend quando disponível), Favoritos (listar/filtrar/remover/abrir links).
- **Em progresso**: Detalhe de destino; formulários de transporte/hospedagem/atividade; orçamento e anexos manipulando apenas estado local (dependem de métodos não implementados).

**CI/CD & Qualidade**
- Lint: `flutter_lints`.  
- Testes: apenas template padrão de contador.  
- Scripts de cobertura, pipelines e badges: **Não encontrado**.

**Licença e Metadados**
- Licença: **Não encontrado**.  
- `pubspec.yaml` contém metadados (nome, descrição, homepage, keywords).  
- Android: flavours `dev/prod` com Firebase BoM/Crashlytics/Perf; iOS: plists separados e entitlements (Sign in with Apple/App Attest).

---

## Funcionalidades
- **Landing Page (estável):** Hero/CTA; captura de e-mail com App Check; `/api/subscribe` (Mailchimp); “Como Funciona”; “Features”; SEO/JSON-LD/sitemap/robots.
- **Backend/APIs (implementado):** Cotações (histórico + sync HG Brasil); Conteúdos (CRUD + thumbnail Storage); Busca de locais (Mapbox/Google com cache/sessões); Health.
- **App (estáveis):** Splash, Auth (email/sociais/upgrade), Onboarding, Home, Trips, Favoritos.  
- **App (em progresso):** Detalhes de destino; formulários Transporte/Hospedagem/Atividade; Orçamento/Anexos (estado local, persistência pendente).

## Tecnologias Utilizadas
- **Landing Page:** Next.js 15.2.4, React 19, Tailwind 4, shadcn/ui, Firebase (App Check/Admin), Mailchimp, framer-motion, rate limit/CORS middleware.
- **Backend/APIs:** NestJS 11 (TS 5.7, Node 20), Prisma + PostgreSQL (Accelerate), Firebase Admin (Firestore/Storage), Mapbox, Google Places, Cloud Monitoring, Swagger.
- **App mobile:** Flutter, flutter_bloc, go_router, injectable/get_it, dio, dartz, json_serializable, Firebase (Auth/Remote Config/App Check/Analytics), file_picker, map_launcher, app_tracking_transparency.


## Contato
> Informação pendente - aguardar resposta do Codex.

## Agradecimentos e Referências
> Informação pendente - aguardar resposta do Codex.
