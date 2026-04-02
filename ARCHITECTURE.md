# 📁 Project Architecture – Next.js + shadcn/ui

Estrutura base usando:

* Next.js (App Router)
* shadcn/ui
* Tailwind CSS
* TypeScript

Essa arquitetura prioriza:

* organização por domínio (features)
* escalabilidade
* reutilização de componentes
* separação clara de responsabilidades

---

# 📦 Estrutura de Pastas

```
src/
│
├── app/
│   ├── (public)/
│   │   ├── page.tsx
│   │   └── layout.tsx
│   │
│   ├── (auth)/
│   │   ├── login/
│   │   │   └── page.tsx
│   │   └── register/
│   │       └── page.tsx
│   │
│   ├── dashboard/
│   │   ├── layout.tsx
│   │   └── page.tsx
│   │
│   ├── api/
│   │   └── users/
│   │       └── route.ts
│   │
│   ├── layout.tsx
│   └── globals.css
│
├── components/
│   ├── ui/
│   ├── layout/
│   └── shared/
│
├── features/
│   ├── auth/
│   └── users/
│
├── hooks/
│
├── lib/
│
├── services/
│
├── types/
│
├── config/
│
└── styles/
```

---

# 📂 Explicação das Pastas

## app/

Contém as rotas da aplicação usando o **App Router** do Next.js.

Cada pasta representa uma rota da aplicação.

### Exemplo de rotas:

```
/               -> app/(public)/page.tsx
/login          -> app/(auth)/login/page.tsx
/dashboard      -> app/dashboard/page.tsx
/api/users      -> app/api/users/route.ts
```

### layout.tsx

Define a estrutura visual compartilhada entre páginas.

Exemplo:

* navbar
* sidebar
* footer

### api/

Define endpoints backend usando **Route Handlers**.

Exemplo:

```
GET /api/users
POST /api/users
```

---

## components/

Componentes reutilizáveis da interface.

### components/ui/

Componentes gerados pelo **shadcn/ui**.

Exemplos:

```
button.tsx
card.tsx
dialog.tsx
input.tsx
```

Não modificar diretamente a lógica principal deles.

---

### components/layout/

Componentes estruturais da aplicação.

Exemplos:

```
Header.tsx
Sidebar.tsx
Footer.tsx
MainLayout.tsx
```

Responsáveis pela estrutura visual.

---

### components/shared/

Componentes reutilizáveis entre várias features.

Exemplos:

```
PageHeader.tsx
DataTable.tsx
EmptyState.tsx
Loader.tsx
```

---

## features/

Organização por domínio/regra de negócio.

Cada feature contém:

* componentes específicos
* regras de negócio
* tipagens
* comunicação com API

Exemplo:

```
features/
 └── users/
     ├── components/
     │   └── UserCard.tsx
     │
     ├── services/
     │   └── getUsers.ts
     │
     └── types.ts
```

Benefícios:

* facilita manutenção
* facilita escalar projeto
* evita arquivos gigantes
* deixa responsabilidades claras

---

## hooks/

Custom hooks reutilizáveis.

Exemplos:

```
useAuth.ts
useDebounce.ts
usePagination.ts
useLocalStorage.ts
```

Responsáveis por:

* lógica reutilizável
* controle de estado
* integração com APIs

---

## lib/

Funções utilitárias e configurações globais.

Exemplos:

```
utils.ts
fetch.ts
auth.ts
date.ts
format.ts
```

Exemplo de util:

```ts
export function formatCurrency(value: number) {
  return new Intl.NumberFormat("pt-BR", {
    style: "currency",
    currency: "BRL"
  }).format(value)
}
```

---

## services/

Responsável por comunicação com APIs externas ou internas.

Exemplo:

```
userService.ts
authService.ts
productService.ts
```

Exemplo:

```ts
export async function getUsers() {
  const response = await fetch("/api/users")
  return response.json()
}
```

---

## types/

Tipagens globais do projeto.

Exemplo:

```
User.ts
ApiResponse.ts
Pagination.ts
index.ts
```

Ajuda a manter padronização.

---

## config/

Arquivos de configuração centralizados.

Exemplo:

```
site.ts
env.ts
navigation.ts
permissions.ts
```

Exemplo:

```ts
export const siteConfig = {
  name: "My App",
  description: "Example project"
}
```

---

## styles/

Estilos adicionais além do Tailwind.

Exemplo:

```
theme.css
animations.css
variables.css
```

---

# 🧠 Como pensar na organização

### app/

define rotas

### components/

define interface reutilizável

### features/

define regra de negócio

### lib/

define utilidades

### hooks/

define lógica reutilizável

---

# 📌 Exemplo de fluxo de criação de funcionalidade

### criar módulo de usuários

1. criar estrutura

```
features/users/
 ├── components/
 │   └── UserCard.tsx
 │
 ├── services/
 │   └── getUsers.ts
 │
 └── types.ts
```

2. criar página

```
app/dashboard/users/page.tsx
```

3. consumir service

```
getUsers()
```

---

# 🚀 Versão simplificada

```
src/
 ├── app/
 ├── components/
 ├── lib/
 └── types/
```

E evoluir conforme o projeto cresce.

---

# 👥 Trabalho em equipe com Git

## Estratégia de branches

Fluxo recomendado:

main → produção  
develop → integração das features  
feature branches → desenvolvimento isolado

### Regras

### Main

- sempre estável
- apenas código pronto para produção
- nunca fazer commit direto
- merge apenas vindo da develop

---

### Develop

- branch de integração
- recebe PR das features
- ambiente de validação
- pode ser deploy de staging

---

### Padrão de nomes para branchs:

feat/nome-da-feature <br>
fix/nome-do-bug <br>
refactor/nome-da-melhoria <br>
chore/nome-da-tarefa <br>
test/nome-do-teste <br>
docs/nome-da-doc <br>

exemplos:

feat/create-user-form <br>
feat/dashboard-metrics <br>
fix/login-validation <br>
refactor/api-pattern <br>
chore/update-eslint <br>
docs/project-architecture <br>

OBS: 2 pessoas não devem trabalhar na mesma branch, não ao mesmo tempo pelo menos.

---

# 📝 Conventional Commits

padrão:

tipo(escopo): descrição curta

exemplos:

feat(auth): add login form <br>
feat(users): create user CRUD <br>
fix(auth): correct token validation <br>
refactor(api): centralize error handler <br>
docs(readme): update setup instructions <br>
test(users): add unit tests <br>
chore(deps): update dependencies <br>

---

## Tipos mais comuns

| tipo | quando usar |
|------|-------------|
| feat | nova funcionalidade |
| fix | correção de bug |
| refactor | melhoria interna sem alterar comportamento |
| chore | tarefa técnica |
| docs | documentação |
| test | testes |
| style | formatação |
| perf | performance |
| build | build ou dependências |
| ci | configuração de CI |

---

## Boas mensagens de commit


feat(users): add pagination to users table <br>
fix(auth): prevent login with expired token <br>
refactor(api): standardize response format <br>
docs: update architecture section <br>

---

## Checklist antes de abrir PR

- código compila
- tipagem correta
- sem any desnecessário
- sem console.log
- sem código comentado
- lint passou
- testes passaram
- sem arquivos desnecessários

---

## Template de descrição de PR

implementa criação de usuário

mudanças: <br>

formulário de usuário <br>
validação com zod <br>
integração com API <br>

como testar: <br>

acessar /dashboard/users <br>
clicar em criar usuário <br>
preencher formulário <br>
verificar criação <br>
