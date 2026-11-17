# STARLINK

Projeto de evolução do Every Cine para STARLINK, preservando as funções existentes.

## Marco zero oficial

**STARLINK-EVERYCINE-VISUAL-TESTE.apk** é a referência funcional Android informada pelo operador em 17/11/2026. Tratar esse build como **MARCO ZERO**: preservar sem alterações, usar como referência visual/funcional e ponto de comparação/rollback. Não sobrescrever nem substituir por builds experimentais.

> O APK de marco zero ainda precisa ser anexado ao repositório (ou a uma Release) para ficar versionado aqui. O arquivo local fornecido nesta conversa não foi enviado como binário para este commit.

## Candidata Samsung/Tizen

A QA 0.4.1 é um pacote **Tizen/WGT para Samsung TV**, não deve ser confundido com o APK Android. O material fornecido informa que o WGT está sem assinatura e que a execução física em TV não foi validada. Não promover QA 0.4.1 a versão estável.

A QA 0.4.2 descrita em `LEIA_PRIMEIRO_QA042.txt` também é candidata de teste sem assinatura; os testes JavaScript locais passaram, mas não houve validação em hardware Samsung. Não alterar painel M81 de produção nem a Samsung QA 3.1 já validada.

## Próximo trabalho

Siga o roteiro de diagnóstico e correção em [docs/CODEX_HANDOFF_MARCO_ZERO.md](docs/CODEX_HANDOFF_MARCO_ZERO.md). Toda correção deve ocorrer em branch/worktree isolado, com testes de regressão e PR para revisão.
