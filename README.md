# Next.js Project

Projeto criado com **Next.js** usando `create-next-app`, configurado para desenvolvimento moderno com **App Router**, **TypeScript** e **shadcn/ui**.

---

# 📋 Pré-requisitos

Antes de começar, instale:

* Node.js >= 18
* npm, yarn, pnpm ou bun
* Git

Verificar versões:

```bash
node -v
npm -v
git --version
```

---

# 🔑 Configurando chave SSH (caso ainda não tenha)

Verifique se já existe uma chave:

```bash
ls ~/.ssh
```

Se não existir, crie:

```bash
ssh-keygen -t ed25519 -C "seu-email@example.com"
```

Pressione **Enter** para aceitar o caminho padrão.

Depois, copie a chave pública:

```bash
cat ~/.ssh/id_ed25519.pub
```

Adicione no GitHub:

Settings → SSH and GPG keys → New SSH key

Teste a conexão:

```bash
ssh -T git@github.com
```

---

# 📦 Instalação

Clone o repositório:

```bash
git clone git@github.com:Engenharia-Software-Estacio/FrontEnd.git
```

Entre na pasta:

```bash
cd FrontEnd
```

Instale as dependências:

```bash
npm install
```


---

# 🚀 Rodando o projeto

Inicie o servidor de desenvolvimento:

```bash
npm run dev
```

Abra no navegador:

http://localhost:3000

O projeto atualiza automaticamente ao editar arquivos.

Arquivo inicial:

```
app/page.tsx
```

---

# 🗂 Estrutura básica do projeto

```
src/
│
├── app/                # rotas (App Router)
│   ├── layout.tsx      # layout global
│   ├── page.tsx        # página inicial
│   └── globals.css     # estilos globais
│
├── components/         # componentes reutilizáveis
│
├── lib/                # utilidades e configurações
│
├── hooks/              # hooks customizados
│
├── services/           # integração com APIs
│
└── types/              # tipagens globais
```

---

# 📚 Scripts disponíveis

```bash
npm run dev      # ambiente de desenvolvimento
npm run build    # build de produção
npm run start    # roda build
npm run lint     # lint do projeto
```

---

# 🌐 Deploy

Build de produção:

```bash
npm run build
```

Deploy recomendado:

https://vercel.com/new

Documentação:

https://nextjs.org/docs/app/building-your-application/deploying

---

# 📄 Licença

MIT
