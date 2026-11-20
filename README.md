# Atividade Prática 04 — Versionamento de Dados e Modelos

## Objetivo

Versionar datasets e modelos de Machine Learning utilizando Git e DVC, comparar duas versões do modelo e demonstrar a restauração de uma versão anterior em um clone limpo.

## Estrutura do projeto

- `data/`: datasets e descritores DVC.
- `src/`: código de treinamento.
- `models/`: modelos treinados.
- `reports/`: métricas, manifestos e relatórios.
- `params.json`: parâmetros do treinamento.
- `dvc.yaml` (se utilizado): pipeline do DVC.

## Pré-requisitos

- Git instalado.
- Python instalado.
- DVC instalado.
- Acesso ao repositório GitHub.
- Acesso ao armazenamento remoto configurado no DVC.

Instalação do DVC:

```bash
pip install dvc
```

## Configuração do armazenamento DVC

O projeto utiliza um armazenamento DVC identificado como `storage`.

Para conferir a configuração:

```bash
dvc remote list
```

Para configurar o armazenamento local, caso ainda não esteja configurado, utilize o caminho correspondente à pasta `dvc-storage`:

```bash
dvc remote add -d storage ../dvc-storage
```

## Restauração de uma versão

Clone o repositório:

```bash
git clone <URL_DO_REPOSITORIO> aula-ml-restauracao
cd aula-ml-restauracao
```

Selecione a versão desejada:

```bash
git switch --detach modelo-r1
```

Configure o acesso ao armazenamento DVC, se necessário, e recupere os arquivos:

```bash
dvc pull
```

Confira os arquivos restaurados e valide os hashes utilizando o manifesto em `reports/modelo.json`.

## Versões registradas

- `dados-v1`: dataset original.
- `modelo-r1`: primeiro modelo treinado.
- `dados-v2`: dataset com correção do rótulo do chamado 006.
- `modelo-r2`: modelo treinado com o dataset corrigido.

## Relatório de comparação

Os resultados da comparação entre os modelos estão documentados em [`reports/comparacao.md`](reports/comparacao.md).