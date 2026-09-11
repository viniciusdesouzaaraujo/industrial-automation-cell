# Industrial Automation Cell

Projeto de automação industrial desenvolvido como ambiente de estudo e comissionamento virtual utilizando **Factory I/O**, **CODESYS** e programação **Ladder**.

> Status: 🚧 Em desenvolvimento

## Objetivo

Desenvolver e documentar uma célula industrial virtual capaz de integrar sensores, atuadores, esteiras e lógica de controle por CLP.

O projeto tem como objetivo aplicar conceitos de:

* Automação industrial
* Programação de CLPs
* Linguagem Ladder
* Mapeamento de entradas e saídas
* Sensores e atuadores
* Intertravamentos
* Sequenciamento de processos
* Diagnóstico de falhas
* Comissionamento virtual

## Arquitetura

```text
Factory I/O
    │
    │ Entradas e saídas digitais
    ▼
CODESYS
    │
    ▼
Programa Ladder
    │
    ▼
Lógica de controle
    │
    ▼
Sensores • Esteiras • Atuadores
```

## Tecnologias

| Tecnologia  | Aplicação                                         |
| ----------- | ------------------------------------------------- |
| Factory I/O | Simulação da célula industrial                    |
| CODESYS     | Ambiente de programação e execução do CLP virtual |
| Ladder      | Desenvolvimento da lógica de controle             |
| GitHub      | Versionamento e documentação técnica              |

## Funcionamento planejado

A célula será organizada para executar uma sequência automatizada utilizando sinais de sensores e comandos para os atuadores.

A lógica será responsável por funções como:

1. Inicialização e parada segura do processo
2. Acionamento das esteiras
3. Detecção de peças pelos sensores
4. Controle dos atuadores
5. Sequenciamento das etapas
6. Intertravamentos para impedir comandos incompatíveis
7. Reset do sistema
8. Tratamento e diagnóstico de falhas

## Estado atual

O projeto encontra-se em fase de desenvolvimento e testes.

Atualmente estou trabalhando em:

* Estrutura da célula no Factory I/O
* Mapeamento das entradas e saídas
* Comunicação com o CODESYS
* Desenvolvimento da lógica Ladder
* Testes individuais de sensores e atuadores
* Sequenciamento do processo

Os problemas encontrados durante o desenvolvimento e suas respectivas soluções também serão documentados neste repositório.

## Estrutura planejada do repositório

```text
industrial-automation-cell/
│
├── README.md
│
├── docs/
│   ├── architecture.md
│   ├── io-map.md
│   ├── sequence.md
│   └── troubleshooting.md
│
├── plc/
│   └── codesys/
│
├── factory-io/
│
└── images/
```

## Documentação

| Documento | Conteúdo | Estado |
|---|---|---|
| [Arquitetura do sistema](./docs/architecture.md) | Fluxo de sinais e responsabilidades de cada camada | Versão inicial |
| [Mapa de entradas e saídas](./docs/io-map.md) | Variáveis, endereços e procedimento de validação | Em levantamento |
| [Sequência operacional](./docs/sequence.md) | Etapas do ciclo automático | Pendente |
| [Registro de falhas](./docs/troubleshooting.md) | Problemas, diagnóstico, correções e resultados | Pendente |

Durante o desenvolvimento também serão adicionadas capturas da lógica Ladder, imagens da célula no Factory I/O e evidências dos testes.

## Próximas etapas

* [ ] Validar todas as entradas e saídas
* [ ] Testar acionamento individual dos atuadores
* [ ] Finalizar controle das esteiras
* [ ] Implementar intertravamentos
* [ ] Finalizar sequência automática
* [ ] Implementar parada e reset
* [ ] Documentar mapa de I/O
* [ ] Documentar lógica de funcionamento
* [ ] Adicionar imagens e demonstração do sistema
* [ ] Executar testes do ciclo completo

## Aprendizados

Este projeto está sendo desenvolvido como parte do meu aprendizado em **automação industrial e mecatrônica**, buscando compreender não apenas a programação de um CLP, mas também o processo de integração, teste, diagnóstico e documentação de um sistema automatizado.

---

**Vinicius de Souza Araújo**  
Estudante de Eletroeletrônica  
Interesses: Automação Industrial • Mecatrônica • Sistemas Embarcados
