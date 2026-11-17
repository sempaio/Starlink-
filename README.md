# STARLINK

Projeto de evolução do Every Cine para STARLINK.

## Marco zero oficial — Android

**`STARLINK-EVERYCINE-VISUAL-TESTE.apk`** foi indicado pelo operador como build funcional em 17/11/2026. É a baseline oficial Android: preservar o binário original, assinatura, identificador e comportamento; usar para comparação e rollback. Não sobrescrever com builds experimentais.

O APK foi recebido no material da tarefa, mas ainda **não foi publicado como binário** neste repositório/Release. A marcação documental como marco zero não significa que o APK já esteja anexado ao GitHub.

## Samsung — QA 0.4.1 / “4.1”

O operador reportou que a versão “4.1” não funciona em um dispositivo Samsung descrito como Galaxy. A falha ainda não foi reproduzida e não há causa raiz confirmada.

**Atenção à plataforma:** o pacote recebido como `STARLINK_TV_EveryCine_QA_0.4.1_PROJETO_E_TESTES.zip` é um WGT para Samsung Smart TV/Tizen. Um Galaxy Android usa APK, não WGT. Não misturar os dois pacotes nem declarar a QA 0.4.1 como funcional: os testes locais descritos no guia não comprovam reprodução física em uma TV Samsung, e o WGT é informado como não assinado.

A QA 0.4.2 também é um WGT candidato sem assinatura Samsung. O guia registra testes JavaScript locais, mas informa que o Chromium automatizado não iniciou e que não houve validação em hardware Samsung. Não tratá-la como funcional comprovada.

Consulte [docs/STATUS_MARCO_ZERO_QA041.md](docs/STATUS_MARCO_ZERO_QA041.md) para o status, a incompatibilidade de plataforma e os dados necessários para diagnosticar a falha.

**Não alterar** o painel M81 de produção nem a Samsung QA 3.1 já validada. Assinar WGTs com certificado Samsung compatível antes de instalar em uma Smart TV.

## Próximo trabalho

Siga [docs/CODEX_HANDOFF_MARCO_ZERO.md](docs/CODEX_HANDOFF_MARCO_ZERO.md). Confirmar o modelo exato do equipamento e qual arquivo/versão falha; depois diagnosticar a plataforma correta com logs e evidência. Trabalhar em branch/worktree isolado e abrir PR para revisão.
