# Registro de diagnóstico de falhas

> Status: em atualização durante os testes

## Objetivo

Este documento registra falhas observadas durante o desenvolvimento da célula, os testes realizados, as hipóteses avaliadas e os resultados obtidos.

Uma ocorrência só será marcada como resolvida quando a correção for reproduzida e validada.

## Método de diagnóstico

Para cada falha:

1. Registrar o sintoma observado.
2. Separar o sistema em processo, comunicação, I/O e lógica.
3. Testar uma hipótese por vez.
4. Registrar a evidência encontrada.
5. Aplicar a correção.
6. Repetir o teste e confirmar o resultado.

## Ocorrências

### TRB-001 — Sistema sem resposta durante os testes iniciais

| Campo | Registro |
|---|---|
| Sintoma | Nenhum movimento ou resposta visível após o comando de operação |
| Impacto | O ciclo automático não era iniciado |
| Estado atual | Resposta parcial recuperada; causa raiz ainda não documentada |
| Evidência posterior | O sistema passou a produzir, indicando que parte da execução e da comunicação começou a funcionar |

#### Pontos que precisam ser confirmados

- Estado de execução do CLP virtual
- Login e modo online do CODESYS
- Estado da variável `M_Run`
- Comunicação entre CODESYS e Factory I/O
- Correspondência entre endereços do driver e variáveis do programa
- Condições de permissividade/intertravamento

---

### TRB-002 — Produção iniciada, mas esteiras não se movimentam

| Campo | Registro |
|---|---|
| Sintoma | A produção é gerada, porém as esteiras permanecem paradas |
| Impacto | As peças não avançam pela célula e a sequência não é concluída |
| Estado atual | Em investigação |
| Subsistema provável | Comando de saída, mapeamento de I/O ou condição lógica das esteiras |

#### Plano de teste

1. Forçar temporariamente cada saída da esteira, em ambiente de simulação, para verificar se o atuador responde.
2. Observar online se a variável de saída muda para `TRUE`.
3. Comparar o endereço `%QX` no CODESYS com o endereço configurado no driver do Factory I/O.
4. Verificar se `M_Run` permanece ativo depois de soltar o botão Start.
5. Verificar contatos normalmente abertos/fechados e intertravamentos que antecedem a bobina da esteira.
6. Confirmar se o Factory I/O está em modo Run.
7. Repetir o ciclo e registrar o resultado de cada etapa.

#### Critério de resolução

A ocorrência será considerada resolvida quando:

- a saída correta estiver ativa no CODESYS;
- o driver transmitir o comando ao endereço correspondente;
- a esteira responder no Factory I/O;
- o comportamento for repetido em pelo menos dois ciclos completos;
- a causa e a correção forem registradas neste arquivo.

## Modelo para novas ocorrências

### TRB-XXX — Título curto

| Campo | Registro |
|---|---|
| Data | DD/MM/AAAA |
| Sintoma | O que foi observado |
| Impacto | Efeito sobre o processo |
| Causa raiz | Preencher somente após confirmação |
| Correção | Alteração aplicada |
| Evidência | Captura, teste ou comportamento observado |
| Estado | Aberta / Em investigação / Resolvida |
