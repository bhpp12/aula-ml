# Comparação entre os modelos r1 e r2

## 1. Alteração realizada

O dataset `chamados-v1` possuía um erro de anotação no chamado de ID 006, classificado incorretamente como `comum`.

Na versão `chamados-v2`, o rótulo foi corrigido para `urgente`, conforme a regra de rotulagem estabelecida.

A partição de treino e teste foi mantida inalterada nas duas versões.

## 2. Comparação das métricas

| Métrica | Modelo r1 | Modelo r2 |
|---|---:|---:|
| Acurácia | 75% | 100% |
| Recall — comum | 100% | 100% |
| Recall — urgente | 50% | 100% |

### Análise

O modelo r2 apresentou melhora de 25 pontos percentuais na acurácia e de 50 pontos percentuais no recall da classe urgente.

O recall da classe comum permaneceu em 100%, sem redução.

## 3. Evidência de restauração em clone limpo

A restauração foi realizada em uma cópia independente do repositório, selecionando a tag `modelo-r1` e recuperando os arquivos com `dvc pull`.

Hashes SHA-256 verificados:

| Arquivo | Hash SHA-256 |
|---|---|
| `data/chamados.csv` | bc3fd86a3a5f598841a58839a9726d901fa7e8361ffe79c5b43873ad8a1328ac |
| `data/split.csv` | 2ef820171c1a4625fe216e6da67c7c8dcf9d97a08288c0239cd23f1a6961d981 |
| `models/model.json` | 72a3a67936139a3473838a6dcfa7aae1acb4c23467be1ef1056d51d485b94840 |

SHA do commit selecionado na restauração:

`6cb4f21f4d2937e483d1e0392548296e47094f45`

Todos os hashes devem corresponder aos valores registrados no manifesto de `modelo-r1`.

## 4. Decisão sobre o modelo r2

**Decisão: ACEITAR o modelo r2 para este exercício.**

O critério de aceitação estabelecido foi melhorar o recall da classe urgente sem reduzir o recall da classe comum, utilizando a mesma partição de teste.

O modelo r2 atendeu ao critério: o recall de urgentes aumentou de 50% para 100%, enquanto o recall de comuns permaneceu em 100%.

A decisão é válida para os resultados deste exercício. Como o conjunto de teste possui apenas quatro exemplos, é necessário ter cautela ao generalizar o desempenho para dados reais.