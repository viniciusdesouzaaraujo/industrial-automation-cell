# Mapa de entradas e saídas (I/O)

> Status: em levantamento e validação  
> Última atualização: 11/09/2026

## Objetivo

Este documento registra a correspondência entre os sinais da célula no **Factory I/O** e as variáveis utilizadas no **CODESYS**.

O mapa será atualizado conforme cada sensor e atuador for testado. Endereços ainda não confirmados não serão tratados como definitivos.

## Convenção de endereçamento

| Prefixo | Significado | Direção |
|---|---|---|
| `%IX` | Entrada digital | Factory I/O → CODESYS |
| `%QX` | Saída digital | CODESYS → Factory I/O |
| `M_` | Memória interna do programa | Lógica interna |

## Entradas digitais confirmadas

| Variável CODESYS | Endereço | Dispositivo/Função | Estado de validação |
|---|---:|---|---|
| `I_Start` | `%IX21.0` | Botão de partida do sistema | Endereço identificado; teste funcional pendente |
| `I_Reset` | `%IX21.1` | Botão de reset do sistema | Endereço identificado; teste funcional pendente |
| `I_Stop` | `%IX21.2` | Botão de parada do sistema | Endereço identificado; teste funcional pendente |

## Entradas digitais a confirmar

Os sensores da célula serão adicionados aqui depois da conferência simultânea no Factory I/O e no CODESYS.

| Variável CODESYS | Endereço | Dispositivo/Função | Estado |
|---|---:|---|---|
| A definir | A definir | Sensor de entrada de peça | Pendente |
| A definir | A definir | Sensor da estação de processamento | Pendente |
| A definir | A definir | Sensor de classificação/identificação | Pendente |
| A definir | A definir | Sensor de posição do atuador 1 | Pendente |
| A definir | A definir | Sensor de posição do atuador 2 | Pendente |

## Saídas digitais a confirmar

| Variável CODESYS | Endereço | Dispositivo/Função | Estado |
|---|---:|---|---|
| A definir | A definir | Esteira de entrada | Pendente |
| A definir | A definir | Esteira principal | Pendente |
| A definir | A definir | Atuador/empurrador 1 | Pendente |
| A definir | A definir | Atuador/empurrador 2 | Pendente |
| A definir | A definir | Sinalização do sistema | Pendente |

## Variáveis internas já identificadas

Estas variáveis não representam pontos físicos de I/O. Elas armazenam estados e comandos da lógica de controle.

| Variável | Função |
|---|---|
| `M_Run` | Memória de funcionamento geral do sistema |
| `M_PusherBusy` | Indica que um ciclo de empurrador está em andamento |
| `M_Pusher1Cycle` | Memória de ciclo do empurrador 1 |

## Procedimento de validação

Para validar cada ponto de I/O:

1. Colocar o CODESYS em modo online.
2. Abrir a lista de variáveis e observar o valor do sinal.
3. Acionar apenas um botão, sensor ou atuador por vez no Factory I/O.
4. Confirmar se o endereço correto muda de `FALSE` para `TRUE`.
5. Registrar neste arquivo o nome, o endereço e a função.
6. Testar novamente para evitar associação incorreta.
7. Somente depois marcar o ponto como **Validado**.

## Critérios para considerar um sinal validado

- O nome da variável corresponde à função real.
- O endereço do CODESYS coincide com o mapeamento do driver do Factory I/O.
- A mudança de estado pode ser observada online.
- O teste foi repetido pelo menos duas vezes.
- O atuador responde ao comando esperado sem acionar outra saída.

## Observação técnica

Variáveis internas como `M_Run` não devem receber endereços `%IX` ou `%QX`. Elas pertencem à lógica do programa. Entradas representam sinais recebidos pelo CLP; saídas representam comandos enviados pelo CLP aos atuadores.
