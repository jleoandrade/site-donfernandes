# Site da Barbearia Don Fernandes · Mens Club

Site estático (HTML + CSS, sem instalação, sem banco de dados). Funciona direto no GitHub + Vercel, de graça.

## O que tem nesta pasta

```
barbearia-don-fernandes/
├── index.html          ← página de escolha (mostra os 3 modelos)
├── modelo-1/index.html ← Clássico (escuro, premium)
├── modelo-2/index.html ← Vintage (claro, editorial)
├── modelo-3/index.html ← Moderno (urbano, agendamento em 3 passos)
├── assets/
│   ├── logo.webp       ← logo usada no site
│   ├── logo.png        ← logo para prévia no WhatsApp/Facebook
│   └── favicon.png     ← ícone da aba do navegador
└── README.md           ← este passo a passo
```

Para ver no seu computador: dê dois cliques em `index.html`.

---

## Passo 1 · Trocar os dados de exemplo

Abra o `index.html` do modelo escolhido num editor de texto (Bloco de Notas funciona; o **VS Code** é melhor e gratuito) e use **Localizar e substituir** (Ctrl+H) para trocar:

| Procure por | Troque por | Exemplo |
|---|---|---|
| `https://SEU-LINK-DE-AGENDAMENTO.com.br` | Link do seu sistema de agendamento (Trinks, AppBarber, Booksy, Google Agenda etc.) | `https://www.trinks.com/donfernandes` |
| `5500000000000` | Seu WhatsApp: 55 + DDD + número, só números | `5511987654321` |
| `[(00) 00000-0000]` | Seu telefone formatado | `(11) 98765-4321` |
| `SEU_INSTAGRAM` | Seu usuário do Instagram, sem @ | `barbeariadonfernandes` |
| `[@seu_instagram]` (modelo 2) | Seu @ | `@barbeariadonfernandes` |
| `https://maps.google.com/?q=Barbearia+Don+Fernandes` | Link do Google Maps (Maps → sua barbearia → Compartilhar → Copiar link) | `https://maps.app.goo.gl/...` |
| `[Rua Exemplo, 000 · Bairro ...]` | Endereço real | |
| `[09h às 20h]`, `[09h às 18h]`, `[Fechado]` | Horários reais | |
| `R$ 00` | Preço de cada serviço e plano | `R$ 45` |
| `[Nome]`, `[Nome do barbeiro]`, `[Especialidade...]` | Equipe | |
| `[Cortes inclusos no mês]`, `[Benefício extra do clube]` | Regras do Mens Club | |
| `https://SEU-SITE.vercel.app` | Endereço final do site (depois do Passo 3) | |

Os textos entre colchetes `[ ]` são para trocar. Depois apague os colchetes.

### Colocar fotos no lugar dos quadros listrados

1. Coloque as fotos na pasta `assets/` com nomes simples, sem espaço ou acento (`corte-1.jpg`, `joao.jpg`).
2. No HTML, troque o quadro:

```html
<div class="ph">Foto de corte</div>
```

por:

```html
<img src="../assets/corte-1.jpg" alt="Corte degradê" style="width:100%;height:100%;aspect-ratio:1;object-fit:cover;border-radius:8px">
```

Use `aspect-ratio:1` para foto quadrada (galeria) e `aspect-ratio:4/5` para retrato (equipe). No modelo 2, as fotos da equipe são redondas: use `border-radius:50%`.

Dica: diminua as fotos antes de subir (até ~1200 px de largura, menos de 300 KB). O site fica rápido no celular.

---

## Passo 2 · Colocar no GitHub (sem instalar nada)

1. Crie uma conta grátis em **github.com** (se ainda não tiver).
2. No canto superior direito, clique em **+ → New repository**.
3. **Repository name:** `barbearia-don-fernandes` · deixe **Public** · clique em **Create repository**.
4. Na página seguinte, clique no link **uploading an existing file**.
5. Abra a pasta do site no seu computador, **selecione tudo o que está dentro dela** (`index.html`, `README.md`, `assets`, `modelo-1`, `modelo-2`, `modelo-3`) e arraste para a página do GitHub.
   - Arraste o **conteúdo** da pasta, não o arquivo .zip.
   - Use Chrome ou Edge; eles mantêm as subpastas no upload.
6. Espere carregar, escreva algo como "Primeira versão do site" e clique em **Commit changes**.
7. Confira: na página do repositório devem aparecer as pastas `assets`, `modelo-1`, `modelo-2`, `modelo-3` e o `index.html` **na raiz** (não dentro de outra pasta).

> Se você usa terminal, o mesmo em comandos (dentro da pasta do site):
> ```bash
> git init
> git add .
> git commit -m "Primeira versão do site"
> git branch -M main
> git remote add origin https://github.com/SEU_USUARIO/barbearia-don-fernandes.git
> git push -u origin main
> ```

---

## Passo 3 · Publicar na Vercel

1. Acesse **vercel.com** → **Sign Up** → escolha **Continue with GitHub** (use a mesma conta do Passo 2).
2. No painel, clique em **Add New… → Project**.
3. Na lista de repositórios, ache `barbearia-don-fernandes` e clique em **Import**.
   - Se ele não aparecer, clique em **Adjust GitHub App Permissions** e libere o acesso ao repositório.
4. Na tela de configuração:
   - **Framework Preset:** `Other`
   - **Root Directory:** `./` (padrão)
   - **Build Command** e **Output Directory:** deixe em branco/padrão (o site não precisa de build).
5. Clique em **Deploy**. Em menos de um minuto aparece o link, algo como `https://barbearia-don-fernandes.vercel.app`.
6. Abra o link: a página inicial mostra os 3 modelos. Teste cada um no celular.

**Atualizações:** toda vez que você mudar um arquivo no GitHub (lápis ✏️ para editar ou **Add file → Upload files** para trocar fotos) e clicar em **Commit changes**, a Vercel publica a nova versão sozinha em ~1 minuto.

---

## Passo 4 · Deixar o modelo escolhido como página principal

Hoje o endereço principal mostra a página de escolha. Depois de decidir o modelo (exemplo: modelo 2):

1. Abra `modelo-2/index.html` e copie todo o conteúdo.
2. Com **Localizar e substituir**, troque `../assets/` por `assets/` (sem os dois pontos e a barra do começo).
3. Cole esse conteúdo no `index.html` **da raiz**, substituindo a página de escolha.
4. Envie para o GitHub (Commit). A Vercel atualiza sozinha.
5. Opcional: apague as pastas dos modelos que não vai usar.

No `index.html` final, troque também `https://SEU-SITE.vercel.app/assets/logo.png` pelo endereço real. Assim a logo aparece quando alguém compartilha o link no WhatsApp.

---

## Passo 5 (opcional) · Domínio próprio (ex.: donfernandes.com.br)

1. Registre o domínio `.com.br` em **registro.br**.
2. Na Vercel: projeto → **Settings → Domains → Add** → digite o domínio.
3. A Vercel mostra os registros de DNS (tipo **A** e/ou **CNAME**). Cadastre esses valores no registro.br, em **DNS → Editar zona**.
4. Aguarde a propagação (de minutos a algumas horas). O HTTPS (cadeado) é ativado automaticamente.

---

## Checklist depois de publicar

- [ ] Clique em **Agendar** e confira se abre o seu sistema de agendamento.
- [ ] No celular, clique em **WhatsApp** e confira se abre a conversa com a mensagem pronta.
- [ ] **Como chegar** abre a barbearia certa no Google Maps.
- [ ] Coloque o link do site no **Perfil da Empresa no Google**, na bio do **Instagram** e no **WhatsApp Business**.
- [ ] Peça aos clientes que avaliem no Google: o botão de avaliações do site leva para lá.
