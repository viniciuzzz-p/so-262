# Atividade 07 — Algoritmo do Banqueiro

**Aluno:** Vinicius Silva Pereira

## Como executar

Com Python 3 instalado, entre nesta pasta e execute:

```bash
python3 bankers_algorithm.py
```

A saída completa fica registrada em `saida_completa.txt`. Os arquivos `teste-01.png`, `teste-02.png` e `teste-03.png` são capturas ilustrativas da saída do terminal, identificadas com o nome do aluno. Para evidência acadêmica, recomenda-se também executar o programa no próprio terminal/IDE e tirar capturas reais da tela com o nome visível.

## Teste 1 — Verificação do estado inicial

O sistema começa com recursos totais `E = [10, 5, 7]` e recursos disponíveis `A = [3, 3, 2]`. A necessidade de cada processo é calculada por `Need = Max - Allocation`. O algoritmo encontra uma sequência segura: **P1 → P3 → P0 → P2 → P4**. Portanto, o estado inicial é seguro, pois todos os processos conseguem terminar nessa ordem e liberar os recursos alocados.

## Teste 2 — Requisição de P1: `[1, 0, 2]`

A requisição não ultrapassa a necessidade restante de P1 e há recursos disponíveis para atendê-la. O programa faz uma alocação provisória e verifica novamente a segurança. Como encontra uma sequência segura, a requisição é **concedida**. O vetor de recursos disponíveis passa a ser `[2, 3, 0]`, e a necessidade restante de P1 passa a ser `[0, 2, 0]`.

## Teste 3 — Requisição de P4: `[3, 3, 0]`

Após o atendimento de P1, os recursos disponíveis são `[2, 3, 0]`. P4 solicita 3 unidades do recurso R0, mas só existem 2 disponíveis. A requisição é **bloqueada por falta de recursos disponíveis**, antes da etapa de teste de segurança. O estado permanece inalterado: `[2, 3, 0]`.

**Observação importante:** neste código e nesta execução, o terceiro teste não chega a demonstrar um estado inseguro nem rollback; ele é recusado no teste de disponibilidade. Isso é diferente de uma requisição que cabe nos recursos disponíveis, mas que tornaria o estado inseguro.
