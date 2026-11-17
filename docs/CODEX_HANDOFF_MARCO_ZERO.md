# Handoff para Codex — STARLINK / Marco zero

Data: 17/11/2026  
Repositório: `sempaio/Starlink-`  
Branch de referência: `main`

## Baseline e arquivos de teste

1. **Android — MARCO ZERO:** `STARLINK-EVERYCINE-VISUAL-TESTE.apk`. O operador informa que está funcionando. Preservar o binário original, assinatura, applicationId e comportamento; não sobrescrever. O APK foi recebido como material da tarefa, mas ainda não foi publicado como binário no repositório/Release.
2. **Android — referência original:** `Every Cine_v1.0.2(10002).apk`. Usar apenas para comparação.
3. **Samsung — falha reportada:** o operador informou que “4.1” não funciona em um aparelho Samsung descrito como Galaxy. A falha ainda não foi reproduzida e a causa raiz não está confirmada. Confirmar nome exato do artefato e modelo/versão do equipamento antes de alterar código.
4. **Samsung Smart TV / Tizen — QA 0.4.1:** ZIP `STARLINK_TV_EveryCine_QA_0.4.1_PROJETO_E_TESTES.zip`, com `PROJETO_TIZEN/`, testes Node/Python e WGT descrito como sem assinatura Samsung. O guia informa ID `STLEC26001`, igual à QA 0.4.0 e diferente da QA 3.1 / QA 0.3.4. Informa 13 testes Node de contrato/regressão e cinco grupos de verificações de marca/fluxos; AVPlay foi simulado, não testado fisicamente em TV. Não marcar como funcional/homologada.
5. **Samsung Smart TV / Tizen — QA 0.4.2:** `STARLINK_TV_Samsung_QA042_NAO_ASSINADO.wgt` e `LEIA_PRIMEIRO_QA042.txt`. O guia descreve ajustes no início da reprodução, foco, AVPlay e restauração da UI; testes JS locais aprovados, Chromium automatizado não iniciou e hardware Samsung não foi validado. Não tratar como funcional comprovada.
6. **Produção:** não alterar painel M81 de produção, credenciais/endpoints nem a Samsung QA 3.1 validada.

## Pedido para executar no Codex

Leia este documento, o README e [STATUS_MARCO_ZERO_QA041.md](STATUS_MARCO_ZERO_QA041.md). Não altere `main` diretamente. Crie branch e worktree isolados.

```text
Repositório: sempaio/Starlink-
Branch sugerida: codex/diagnostico-samsung-4-1

Antes de implementar:
1. Confirme o alvo físico e o artefato exato. O operador descreveu um Samsung Galaxy; se for telefone/tablet Galaxy, o alvo é Android/APK. A QA 0.4.1 disponível neste material é Tizen/WGT para Smart TV e não instala em Galaxy Android. Não misture as plataformas.
2. Solicite/registre modelo completo, versão do sistema e nome exato do arquivo “4.1” instalado. Colete mensagem de erro/log e etapa da falha (instalação, abertura, login, catálogo, player ou codec).
3. Se for Galaxy Android, inspecione o APK/projeto Android correspondente, seu manifesto, applicationId, assinatura, SDK e logs. Compare com STARLINK-EVERYCINE-VISUAL-TESTE.apk como marco zero sem modificar o APK de baseline.
4. Se for Samsung Smart TV, leia o guia QA 0.4.1 e os testes/projeto do ZIP. Inspecione config.xml, app.js, catálogo, AVPlay e scripts. Reproduza em TV real quando disponível; WGT deve ser assinado com certificado Samsung compatível.
5. Não invente causa raiz: diferencie evidência de hipótese e instalação de reprodução.
6. Faça correção pequena em branch/worktree isolado, acrescente testes de regressão e gere artefato candidato separado.
7. Não altere painel M81 de produção, credenciais/endpoints nem Samsung QA 3.1.
8. Abra PR para main com diagnóstico, evidências, arquivos alterados, testes executados, limitações e instruções. Não faça merge automaticamente.
```

## Aceite

- [ ] APK indicado como marco zero, preservado; publicação do binário em Release/repositório tratada separadamente.
- [ ] Arquivo “4.1” e plataforma confirmados (APK Android ou WGT Tizen).
- [ ] Modelo exato do equipamento e versão do sistema registrados.
- [ ] Falha reproduzida ou limitação de reprodução explicitada.
- [ ] Causa raiz sustentada por logs/evidência, não suposição.
- [ ] Testes de regressão e build candidata separada.
- [ ] Hardware real testado ou claramente marcado como não testado.
- [ ] PR aberto para revisão; nenhuma alteração direta em produção.

## Observação sobre os binários

Os APKs e WGTs fornecidos estão no material da tarefa. Os commits documentais não publicam esses binários. Não afirmar que estão disponíveis para download pelo GitHub até que o APK de marco zero e os WGTs sejam efetivamente anexados a Releases/artefatos apropriados.
