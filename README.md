# SecurityHUB

Esse repositorio é destinado a migração de sua versão (Web) para uso nativo (Android)

SecurityHUB é um sistema simples de gerenciamento, utiliza um pacote PHP unico para o painel administrativo, BFF,
Host API, licencas, updates e integracao Supabase.

Tem como sua estrutura principal um desenvolvimento simples para compatibilidade para versão compartilhada (single-plan) - Hostinger;

```text
SecurityHUB/
|-- src/
|   |-- core/
|   |-- vendor/
|   |-- public_html/
|   |   |-- api/
|   |   |-- apps/
|   |   `-- admin/
|   |-- .env.example
|   |-- composer.json
|   |-- composer.lock
|   `-- config.example.php
|-- schemas/
|   |-- schema.sql
|   `-- migrations/
|-- docs/
|-- deploy/
|-- .gitignore
|-- composer.json
`-- README.md
```

`src/public_html/admin/` serve o painel e suas rotas para gerenciamento `/bff/v1/*`.
`src/public_html/api/` serve a API publica em `/api/v1/*`.
Somente `public_html/` fica exposto na rota publica; `core/`, `vendor/` e
`config.php` ficam na raiz privada do pacote.

# [Matriz de Migração](docs/matriz_de_migracao.md)
