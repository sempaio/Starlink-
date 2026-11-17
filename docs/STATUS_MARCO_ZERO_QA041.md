# Status do marco zero e da versão 4.1

Data: 17/11/2026  
Repositório: `sempaio/Starlink-`  
Branch desta documentação: `docs/marco-zero-qa041-status-20261117`

## Marco zero — confirmado por indicação do operador

- Arquivo: `STARLINK-EVERYCINE-VISUAL-TESTE.apk`
- Plataforma: Android.
- Status: **MARCO ZERO FUNCIONAL**, conforme relato do operador em 17/11/2026.
- Regra: preservar o APK original, sua assinatura, applicationId e comportamento. Toda nova build deve ser candidata separada e comparada com esta baseline.
- Publicação: o arquivo existe no material recebido, mas ainda não está anexado ao repositório nem a uma GitHub Release. Este documento não afirma que o binário foi publicado.

## Relato de falha — “4.1” em Samsung Galaxy

O operador informou que a versão “4.1” não funciona em um aparelho Samsung descrito como Galaxy. O relato é registrado como **falha reportada, ainda sem reprodução técnica ou causa raiz confirmada**.

Há uma incompatibilidade importante a esclarecer antes de alterar código:

- O pacote recebido com o nome `STARLINK_TV_EveryCine_QA_0.4.1_PROJETO_E_TESTES.zip` é documentado como aplicativo **Samsung Smart TV / Tizen**, distribuído como WGT.
- Um Samsung Galaxy é normalmente um dispositivo **Android**. Um WGT Tizen não é um APK Android e não deve ser instalado em um telefone Galaxy.
- Portanto, não é possível concluir apenas pelo relato se “4.1” significa a QA 0.4.1 para Smart TV ou uma versão APK Android 4.1 separada.

O guia associado à QA 0.4.1 registra testes locais de contrato/regressão e simulação do AVPlay, mas não comprova execução física em uma TV Samsung. O WGT recebido também é descrito como não assinado. Assim, a QA 0.4.1 não deve ser marcada como funcional/homologada.

## Próximo passo técnico seguro

Antes de corrigir a versão reportada, confirmar:

1. O nome exato do arquivo instalado (APK ou WGT) e se o número é `4.1` ou `0.4.1`.
2. O modelo completo do aparelho (por exemplo, Galaxy A/S/Tab ou modelo da Smart TV) e a versão do Android ou Tizen.
3. Em que etapa falha: instalação, abertura, login, catálogo, início da reprodução ou reprodução/codec. Anexar mensagem de erro ou log, se houver.

Se o alvo for um Galaxy Android, investigar o APK e o projeto Android separadamente; não tentar instalar nem adaptar o WGT Tizen para esse telefone. Se o alvo for uma Samsung Smart TV, seguir o diagnóstico Tizen/WGT, verificar assinatura/instalação, ID do aplicativo, AVPlay e logs na TV real.

## Restrições de preservação

- Não sobrescrever ou recompilar sobre o APK de marco zero.
- Gerar qualquer correção como artefato candidato separado.
- Não alterar painel M81 de produção, credenciais/endpoints ou a Samsung QA 3.1 validada.
- Trabalhar em branch/worktree isolado, adicionar testes de regressão e abrir PR para revisão.
- Distinguir explicitamente testes automatizados/simulados de testes realizados em hardware real.
