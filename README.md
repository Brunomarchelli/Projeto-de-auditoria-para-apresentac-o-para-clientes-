# Painel de Auditoria v5 — GitHub Pages

Painel de auditoria compartilhado: todos os visitantes veem e editam os mesmos dados em tempo real.

---

## 🚀 Como publicar no GitHub Pages

### Passo 1 — Criar o repositório

1. Acesse [github.com](https://github.com) e crie um repositório **público** (ex: `painel-auditoria`)
2. Faça upload do arquivo `index.html` (arraste para a área de upload ou use `git push`)

### Passo 2 — Configurar o JSONBin (backend gratuito)

O JSONBin.io é usado para armazenar e compartilhar os dados entre todos os visitantes.

1. Acesse **[https://jsonbin.io](https://jsonbin.io)** e crie uma conta gratuita
2. Vá em **API Keys** → copie a sua **Master Key** (começa com `$2a$10$...`)
3. Clique em **Bins** → **+ Create Bin**
   - Cole este conteúdo no bin: `{}`
   - Clique em **Create**
4. Copie o **Bin ID** exibido no topo da página (ex: `64f3a1b2e...`)

### Passo 3 — Configurar o arquivo `index.html`

Abra o `index.html` e encontre estas duas linhas no início do `<script>`:

```javascript
const JSONBIN_MASTER_KEY = '$2a$10$zmMQkYyuDVZTjofrgEXbI.VjKawwM4n2y66fJpFOjLPAEqaTp118O';
const JSONBIN_BIN_ID     = '$2a$10$fBHcwJLASVk0VwDdny5vKeF4Uux3INWcLdlU9TkYjLXR6NZ6mlEVO';
```

Substitua pelos valores copiados:

```javascript
const JSONBIN_MASTER_KEY = '$2a$10$SuaChaveAqui...';
const JSONBIN_BIN_ID     = '64f3a1b2e3c4d5e6f7a8b9c0';
```

### Passo 4 — Ativar o GitHub Pages

1. No repositório, vá em **Settings → Pages**
2. Em **Source**, selecione **Deploy from a branch**
3. Selecione o branch `main` e a pasta `/ (root)`
4. Clique em **Save**
5. Aguarde ~1 minuto e acesse a URL exibida (ex: `https://seu-usuario.github.io/painel-auditoria`)

---

## 🔄 Como os dados são sincronizados

| Situação | Comportamento |
|---|---|
| Visitante abre a página | Busca os dados mais recentes do JSONBin |
| Visitante adiciona/edita um registro | Salva imediatamente no JSONBin |
| Outro visitante está com a página aberta | Os dados são atualizados automaticamente a cada **30 segundos** |
| JSONBin indisponível | Usa cache local (localStorage) como fallback |

---

## 🔒 Segurança

- A **Master Key** fica visível no código-fonte HTML. Para uso interno de equipe isso é aceitável.
- Para restringir escrita, considere usar uma **Access Key** de somente-leitura para visitantes e manter a Master Key apenas para o administrador.
- O plano gratuito do JSONBin suporta até **10.000 requests/mês**, suficiente para uso moderado.

---

## 📁 Estrutura do repositório

```
painel-auditoria/
├── index.html   ← arquivo principal (tudo em um único arquivo)
└── README.md
```

---

Desenvolvido com 💚 | Painel de Auditoria v5
