# Handoff para Codex — STARLINK / Marco zero

Data: 17/11/2026  
Repositório: `sempaio/Starlink-`  
Branch de referência: `main`

## Baseline e arquivos de teste

1. **Android — MARCO ZERO:** `STARLINK-EVERYCINE-VISUAL-TESTE.apk`. O operador informa que está funcionando. Preservar o binário original, assinatura, applicationId e comportamento. Não sobrescrever. O arquivo foi recebido localmente nesta tarefa, mas ainda não foi publicado como binário no repositório/Release.
2. **Android — referência original:** `Every Cine_v1.0.2(10002).apk`. Usar para comparação, não como baseline funcional nova.
3. **Samsung Smart TV / Tizen — QA 0.4.1:** ZIP `STARLINK_TV_EveryCine_QA_0.4.1_PROJETO_E_TESTES.zip`, com `PROJETO_TIZEN/`, testes Node/Python e WGT sem assinatura. O guia informa ID `STLEC26001`, igual à QA 0.4.0 e diferente da QA 3.1 / QA 0.3.4. Informa 13 testes Node de contrato/regressão + 5 grupos de verificações de marca/fluxos aprovados; AVPlay foi simulado, não testado fisicamente em TV.
4. **Samsung Smart TV / Tizen — QA 0.4.2:** `STARLINK_TV_Samsung_QA042_NAO_ASSINADO.wgt` e `LEIA_PRIMEIRO_QA042.txt`. O guia descreve ajustes no início da reprodução, foco, AVPlay e restauração da UI; testes JS locais aprovados, Chromium automatizado não iniciou e hardware Samsung não foi validado. O guia diz que mantém o mesmo ID independente da QA 0.4.1, sem alterar o identificador da QA 3.1.
5. **Produção:** não alterar painel M81 de produção, credenciais/endpoints nem a Samsung QA 3.1 validada.

## Pedido para executar no Codex

Leia este documento e o README. Não altere `main` diretamente. Crie branch e worktree isolados.

```text
Repositório: sempaio/Starlink-
Branch sugerida: codex/diagnostico-samsung-qa041

Antes de implementar:
1. Confirme o alvo físico exato. O pacote QA 0.4.1 descrito nos arquivos é Tizen/WGT para Samsung Smart TV. O marco zero indicado é APK Android. Não confunda um telefone Samsung Galaxy (Android) com uma Samsung Smart TV (Tizen). Se o usuário estiver falando de telefone Galaxy, diagnostique o APK/Android separadamente e peça modelo/versão Android e logs; não tente instalar WGT nele.
2. Leia o guia QA 0.4.1, o guia QA 0.4.2 e os testes/projeto do ZIP. Inspecione config.xml, app.js, catálogo, player AVPlay e scripts de teste.
3. Reproduza a falha QA 0.4.1 e identifique se ocorre na instalação/assinatura, login, navegação, abertura do player, AVPlay, formato/codec ou retorno à interface. Colete logs e evidência. Não invente causa raiz.
4. Compare mudanças com STARLINK-EVERYCINE-VISUAL-TESTE.apk como baseline Android, sem modificar/substituir o APK. Não copie comportamento Android para Tizen sem justificativa técnica.
5. Faça correção pequena e isolada, testes de regressão e documentação. Não altere painel M81 de produção nem Samsung QA 3.1.
6. Gere artefato candidato separado. WGT precisa de assinatura com certificado Samsung compatível antes da instalação; documente se a atualização preserva ID/dados.
7. Teste em hardware real quando disponível. Diferencie claramente testes simulados/automatizados de reprodução física em TV. Se hardware não estiver disponível, marque como não validado.
8. Commit apenas na branch isolada e abra PR para main com causa sustentada por evidência, arquivos alterados, comandos/testes, limitações e instruções de instalação. Não faça merge automaticamente.
```

## Aceite

- [ ] APK indicado como marco zero, preservado; binário publicado em Release ou repositório se for necessário disponibilizá-lo no GitHub.
- [ ] Modelo exato e plataforma confirmados (Android Galaxy ou Samsung TV/Tizen).
- [ ] Falha 0.4.1 reproduzida ou limitação de reprodução explicitada.
- [ ] Causa raiz sustentada por logs/evidência, não suposição.
- [ ] Testes de regressão e build candidata separada.
- [ ] Hardware real testado ou claramente marcado como não testado.
- [ ] PR aberto para revisão; nenhuma alteração direta em produção.

## Observação sobre os binários

Os APKs e WGTs fornecidos nesta tarefa estão no ambiente local da sessão. Os commits deste handoff atualizam documentação; não publicam os binários. Publique o APK de marco zero e os WGTs em GitHub Releases/artefatos apropriados antes de dizer que estão disponíveis para download pelo repositório.
