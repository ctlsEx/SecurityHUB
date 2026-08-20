| Area | Estado atual | Recurso nativo Android | Prioridade | Esforco | Observacao |
| --- | --- | --- | --- | --- | --- |
| Login e sessao | Web/BFF com cookies HttpOnly e CSRF; API bearer para endpoints publicos | Login nativo via API, refresh token e armazenamento seguro no Android Keystore | Alta | Medio | Para app nativo, o fluxo deve favorecer bearer token e storage seguro, nao cookies de painel. |
| Visao geral da conta | Renderizada no painel web via `/account` e `/v1/account/overview` | Tela Compose com resumo de conta, produtos, licencas e status | Alta | Medio | Bom primeiro modulo Android porque a API ja entrega dados agregados. |
| Licencas | Criacao/admin no painel; ativacao por `/v1/client/activate` | Ativacao nativa de licenca, exibicao de validade e status | Alta | Medio | Exige definir fingerprint Android e mensagens claras de erro. |
| Heartbeat | Endpoint `/v1/client/heartbeat` | WorkManager periodico com retry/backoff | Alta | Baixo/Medio | Mantem sessao viva mesmo com app em segundo plano, respeitando restricoes do Android. |
| Dispositivos | Listagem e reset via painel/admin | Tela nativa de dispositivos vinculados e solicitacao/reset controlado | Media | Medio | Acoes destrutivas devem exigir confirmacao forte. |
| Produtos | Catalogo no painel e schema de produtos/planos/features | Lista nativa de produtos e planos disponiveis/ativos | Media | Medio | Pode aproveitar o modelo atual de produtos e planos. |
| Updates de artefatos | Manifesto e arquivos em `/apps/production_feature/update` | DownloadManager, checksum, progresso e historico de downloads | Media | Medio/Alto | Android tem restricoes para instalacao e updates fora da Play Store. |
| bot profiles | Resolve por processo, janela, titulo e hash de executavel | Cache/sync de profiles publicados, se houver equivalente Android | Media | Medio | O modelo atual e muito desktop; precisa adaptar os sinais de deteccao. |
| Admin usuarios | Painel web completo | Fluxos nativos apenas para operacoes frequentes | Baixa/Media | Alto | Migrar tudo para Android aumenta custo e superficie de seguranca. |
| Admin licencas | Painel cria, edita, exclui e reseta dispositivos | Tela admin nativa para criar/editar licencas | Media | Alto | Util para suporte em campo, mas requer UX cuidadosa e auditoria forte. |
| RBAC | Backend valida roles e permissoes por modulo | UI nativa com menus filtrados por permissao | Alta | Baixo | E apenas experiencia; seguranca permanece no backend. |
| MFA/biometria | MFA administrativo obrigatorio no provedor | BiometricPrompt para desbloqueio local de area sensivel | Media | Medio | Biometria complementa, mas nao substitui MFA remoto. |
| Auditoria | `audit_events` no Supabase | Eventos mobile para login, sync, ativacao e acoes admin | Media | Medio | Ajuda suporte, antifraude e rastreabilidade. |
| Offline/cache | Pouco evidente no painel web | Room/DataStore com estado de sincronizacao | Media | Medio | Importante para licencas e profiles em falhas temporarias de rede. |
| Notificacoes | Nao ha recurso nativo | Notificacoes locais/push para expiracao, update e bloqueios | Baixa/Media | Medio | Depende de estrategia de engajamento e permissao do usuario. |
| Diagnostico | Request ID no backend | Tela de diagnostico com versao, request id e ultimo sync | Media | Baixo | Reduz tempo de suporte. |
| Contratos de API | Rotas definidas em PHP, sem OpenAPI evidente | OpenAPI + geracao de cliente Android | Alta | Medio | Reduz divergencia entre backend e app. |