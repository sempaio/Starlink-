# STARLINK

Projeto de evolução do Every Cine para STARLINK.

## Marco zero oficial — Android

**`STARLINK-EVERYCINE-VISUAL-TESTE.apk`** foi indicado pelo operador como build funcional em 17/11/2026. É a baseline oficial: preservar o binário original, assinatura, identificador e comportamento; usar para comparação e rollback. Não sobrescrever com builds experimentais.

O APK foi recebido localmente nesta tarefa, mas ainda **não foi publicado como binário** neste repositório/Release. A marcação documental como marco zero não significa que o APK já esteja anexado ao GitHub.

## Samsung TV — Tizen/WGT

A QA 0.4.1 é um pacote WGT para Samsung Smart TV, sem assinatura Samsung. Seu guia informa o ID `STLEC26001`, igual ao da QA 0.4.0 e diferente da QA 3.1 / QA 0.3.4. O guia registra 13 testes Node de contrato/regressão e 5 grupos de verificações de marca/fluxos aprovados; AVPlay foi simulado, mas não houve execução física na TV.

A QA 0.4.2 também é WGT sem assinatura. Seu guia registra testes JavaScript locais aprovados para contratos Xtream, login, abertura do player, foco, séries e fallback de contêiner; Chromium automatizado não iniciou e não houve validação em hardware Samsung. O guia informa que ela mantém o mesmo identificador da QA 0.4.1, permitindo atualização dessa edição sem alterar o ID da QA 3.1.

**Nenhuma das validações locais comprova reprodução real em uma TV.** Assinar os WGTs com certificado Samsung compatível antes de instalar. Não alterar o painel M81 de produção nem a Samsung QA 3.1 já validada.

## Próximo trabalho

Siga [docs/CODEX_HANDOFF_MARCO_ZERO.md](docs/CODEX_HANDOFF_MARCO_ZERO.md). Diagnosticar a falha relatada da QA 0.4.1 com evidência, confirmar o modelo exato do equipamento Samsung e separar Android/APK de Samsung TV/Tizen/WGT. Trabalhar em branch/worktree isolado e abrir PR para revisão.
