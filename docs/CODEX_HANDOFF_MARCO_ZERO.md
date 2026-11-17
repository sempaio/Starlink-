# Handoff para Codex — STARLINK / Marco zero

Data de referência: 17/11/2026  
Repositório: `sempaio/Starlink-`  
Branch de produção: `main`

## Estado conhecido (não misturar plataformas)

1. **Android — marco zero funcional:** `STARLINK-EVERYCINE-VISUAL-TESTE.apk`. O operador informou que esse APK está funcionando. É a baseline oficial para comparação. Preserve o arquivo original, assinatura, applicationId e comportamento; não o sobrescreva com uma build de teste.
2. **Android — original de referência:** `Every Cine_v1.0.2(10002).apk`. Use somente para comparação com o app original.
3. **Samsung TV / Tizen — QA 0.4.1:** o ZIP `STARLINK_TV_EveryCine_QA_0.4.1_PROJETO_E_TESTES.zip` contém `PROJETO_TIZEN/`, testes Node/Python e um WGT sem assinatura. A instrução QA 0.4.1 diz que o ID é `STLEC26001`, igual ao da QA 0.4.0 e diferente da QA 3.1 / QA 0.3.4. O operador reporta que essa versão não funciona no equipamento Samsung/Galaxy referido; reproduza e diagnostique antes de alterar.
4. **Samsung TV / Tizen — QA 0.4.2:** `LEIA_PRIMEIRO_QA042.txt` descreve uma candidata WGT sem assinatura, com ajustes de abertura do player, foco, AVPlay e retorno à UI. Os testes JS locais são descritos como aprovados, mas o próprio arquivo diz que Chromium automatizado não iniciou e que não houve validação em hardware Samsung. Não tratar como funcional comprovada.
5. **Produção:** não alterar o painel M81 de produção nem a Samsung QA 3.1 já validada.

## Instrução de execução

Copie este pedido para o Codex no repositório GitHub:

```text
Trabalhe no repositório sempio/Starlink-. Primeiro leia README.md e docs/CODEX_HANDOFF_MARCO_ZERO.md. Não faça alterações diretamente em main. Crie uma branch e worktree isolados, por exemplo codex/samsung-galaxy-qa-diagnostico.

Objetivo:
- Registrar STARLINK-EVERYCINE-VISUAL-TESTE.apk como MARCO ZERO funcional Android, sem modificá-lo.
- Investigar por que a QA 0.4.1 falha no dispositivo Samsung indicado pelo operador.
- Antes de codificar, determine se o alvo é um telefone Samsung Galaxy (Android/APK) ou uma Samsung Smart TV (Tizen/WGT). Não misture APK Android com WGT Tizen. Se a descrição do hardware continuar ambígua, registre a dúvida e peça o modelo exato antes de qualquer alteração específica de plataforma.
- Inspecione o projeto, manifesto/configuração, identificadores, assinatura/instalação, logs e fluxo de inicialização/reprodução. Diferencie falha de instalação, autenticação, navegação, player/codec e compatibilidade de dispositivo.
- Compare qualquer mudança com o APK de marco zero e preserve as funções existentes. Não altere o painel M81 de produção, credenciais, endpoints ou Samsung QA 3.1 validada.
- Reproduza a falha com testes automatizados e, quando disponível, teste no hardware real. Não declare reprodução validada apenas por simulação.
- Faça uma correção pequena e focada, acrescente testes de regressão e documente claramente o que foi e não foi testado.
- Gere artefato de teste separado, sem substituir o marco zero. Se for Tizen, explique que o WGT precisa ser assinado com certificado Samsung compatível antes da instalação.
- Ao terminar, faça commit na branch, abra um Pull Request para main com diagnóstico, causa raiz, arquivos alterados, comandos/testes executados, limitações e instruções para instalar/testar. Não faça merge automaticamente.
```

## Critérios de aceite

- [ ] APK de marco zero preservado e claramente identificado como baseline.
- [ ] Plataforma e modelo de dispositivo confirmados; Android e Tizen tratados separadamente.
- [ ] Causa da falha 0.4.1 sustentada por evidência (log/reprodução), não por suposição.
- [ ] Testes de regressão cobrindo a falha corrigida.
- [ ] Build candidata separada, com versão/identificador documentados.
- [ ] PR aberto para revisão; nenhuma alteração direta em produção.

## Limites do material recebido

Os nomes dos arquivos e as instruções QA 0.4.1/QA 0.4.2 foram recebidos nesta tarefa. O APK de marco zero e os pacotes binários não estão anexados como arquivos versionados neste repositório por este commit. Antes de afirmar que os binários foram publicados, faça upload deles em uma GitHub Release ou no repositório usando o fluxo apropriado para arquivos binários.
