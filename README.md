# Stater Platform — Documentação

Documentação pública da API Pix da Stater, construída no [Mintlify](https://mintlify.com).

## Estrutura

```
.
├── docs.json                     # Configuração: nome, cores, navegação, tabs
├── introduction.mdx              # Landing dos guias
├── quickstart.mdx                # Primeiros passos (5 min)
├── guides/
│   ├── authentication.mdx        # Bearer + X-Pix-Account-Id
│   ├── money-format.mdx          # Centavos como string
│   ├── idempotency.mdx           # Idempotency-Key
│   ├── errors.mdx                # Códigos de erro
│   ├── rate-limits.mdx           # 429 e backoff
│   ├── send-pix.mdx              # Fluxo: consulta de chave → transferência Pix
│   ├── receive-pix.mdx           # Cobranças + Pix por chave (webhook / extrato)
│   └── webhooks.mdx              # Configuração + handlers
├── api-reference/
│   ├── introduction.mdx          # Visão geral
│   └── openapi.yaml              # Spec da Stater Platform 0.1.0
├── logo/                         # opcional: assets locais (ou use URL no docs.json)
└── images/                       # diagramas, screenshots (opcional)
```

## Setup local

```bash
# 1. Instalar o CLI do Mintlify
npm i -g mint

# 2. Rodar preview na pasta do projeto
mint dev
# O comando mostra no terminal a URL de preview da documentação.
```

## Publicação

1. **Crie uma conta** em [mintlify.com](https://mintlify.com).
2. **Faça push** deste projeto para um repositório no GitHub.
3. **Instale o GitHub App** da Mintlify no repo (em
   `Settings → GitHub App` no painel da Mintlify).
4. A cada `git push` na branch principal, a doc é redeployada automaticamente.

## O que ainda falta personalizar

- [x] Logo no `docs.json` (URL S3 em `logo.light` / `logo.dark`)
- [ ] `favicon.svg` na raiz (referenciado em `docs.json`)
- [ ] Confirmar URLs no `docs.json`: `app.stric.io`, `status.stric.io`,
      links de redes sociais, e-mail de suporte
- [ ] Validar exemplos de payload do quickstart com a API real
      (chaves, contas, valores)
- [ ] Alinhar exemplos de `events` em `guides/webhooks.mdx` com o que o produto aceita no painel
- [ ] Adicionar diagramas (Mermaid) onde fizer sentido — Mintlify suporta
      nativamente
- [ ] Configurar domínio customizado (ex.: `docs.stric.io`)

## Comandos úteis

```bash
# Validar o OpenAPI
npx @redocly/cli lint api-reference/openapi.yaml

# Gerar páginas MDX individuais a partir do OpenAPI
# (caso queira customizar página por página em vez de auto-render)
npx @mintlify/scraping@latest openapi-file ./api-reference/openapi.yaml \
  -o ./api-reference/endpoints
```

## Referências

- [Mintlify docs](https://www.mintlify.com/docs) — documentação oficial
- [OpenAPI setup no Mintlify](https://www.mintlify.com/docs/api-playground/openapi-setup)
- [Componentes MDX disponíveis](https://www.mintlify.com/docs/content/components)
