# Análise de fatores institucionais e estruturais associados ao abandono escolar no Ensino Médio brasileiro

**Estudo com dados do Censo Escolar 2025 e das Taxas de Rendimento Escolar 2024**

## Sobre o projeto

Este projeto investiga a relação entre características institucionais e estruturais das escolas públicas que ofertam Ensino Médio regular e a ocorrência de abandono escolar no Brasil.

A análise integra informações do Censo Escolar 2025 — como infraestrutura, localização, dependência administrativa, acessibilidade, recursos humanos e participação institucional — com as Taxas de Rendimento Escolar de 2024, das quais é utilizada a taxa oficial de abandono do Ensino Médio por escola.

O estudo trabalha com duas frentes complementares:

- **Análise descritiva e interpretativa:** investigar características institucionais associadas ao abandono escolar.
- **Modelagem preditiva:** desenvolver um sistema de alerta que classifica as escolas em níveis de risco.

Os resultados apresentados no projeto são exploratórios e associativos. Eles não demonstram relações de causa e efeito.

## Objetivos

- Descrever características institucionais das escolas analisadas.
- Investigar associações entre essas características e a taxa de abandono escolar.
- Comparar modelos supervisionados com funções complementares.
- Organizar uma proposta de classificação de escolas em níveis de risco.

## Fontes de dados

| Arquivo esperado | Ano | Utilização |
|---|---:|---|
| `Tabela_Escola_2025.csv` | 2025 | Atributos institucionais das escolas |
| `Tabela_Matricula_2025.csv` | 2025 | Matrículas no Ensino Médio regular, diurno e noturno |
| `tx_rend_escolas_2024.xlsx` | 2024 | Taxa oficial de abandono do Ensino Médio por escola |

As bases são integradas pela variável `CO_ENTIDADE`, identificador da escola.

**Limitação temporal:** os atributos institucionais utilizados são de 2025, enquanto a variável-alvo de abandono é de 2024. Essa diferença deve ser considerada na interpretação dos resultados.

As fontes oficiais para obtenção dos dados estão descritas em [assets/data/README.md](assets/data/README.md).

## Metodologia e notebooks

O repositório contém dois notebooks:

| Notebook | Conteúdo |
|---|---|
| [Análise exploratória inicial](src/analise_explorat%C3%B3ria_inicial.ipynb) | Organização das bases, recorte do Ensino Médio regular e análise exploratória de atributos institucionais. |
| [Modelos de abandono escolar](src/abandono_escolar_modelos.ipynb) | Integração das bases, preparação das variáveis, Árvore de Decisão, Random Forest e sistema de alerta em cascata. |

### Modelos utilizados

- **Árvore de Decisão:** utilizada para produzir regras interpretáveis e apoiar a análise dos fatores associados ao abandono.
- **Random Forest:** utilizada na etapa preditiva do sistema de alerta.

O sistema descrito no notebook de modelagem utiliza duas etapas para classificar as escolas em três níveis: **Sem abandono**, **Risco moderado** e **Alto risco**.

## Principais fatores discutidos

As conclusões registradas no notebook de modelagem destacam associações com:

- proporção de matrículas no turno noturno;
- carência de recursos pedagógicos;
- disponibilidade de profissionais de apoio psicossocial;
- participação institucional, incluindo grêmio estudantil e associação de pais e mestres;
- localização e dependência administrativa.

Esses resultados devem ser interpretados dentro do recorte e das limitações do estudo, sem atribuição de causalidade.

## Estrutura do repositório

```text
.
├── README.md
├── CITATION.cff
├── assets/
│   └── data/
│       └── README.md
├── docs/
│   ├── figuras e gráficos
│   └── diagramas do projeto
└── src/
    ├── abandono_escolar_modelos.ipynb
    └── analise_exploratória_inicial.ipynb
```

## Como reproduzir a análise

Os notebooks esperam os arquivos de dados listados na seção [Fontes de dados](#fontes-de-dados). Esses arquivos não estão armazenados atualmente no repositório.

Para reproduzir a análise, é necessário obter as bases nas fontes oficiais indicadas em [assets/data/README.md](assets/data/README.md), disponibilizar os arquivos no ambiente de execução e conferir os caminhos definidos no início de cada notebook.

As dependências e versões utilizadas ainda precisam ser documentadas. Por isso, este README não apresenta comandos de instalação ou execução que não estejam confirmados pelo projeto.

## Limitações

- A variável-alvo é referente a 2024, enquanto os atributos institucionais são de 2025.
- Variáveis individuais, como renda familiar e necessidade de trabalhar, não estão disponíveis na base utilizada.
- O Censo Escolar registra a presença de recursos, mas não necessariamente sua qualidade, manutenção ou utilização.
- O recorte do estudo considera escolas públicas que ofertam Ensino Médio regular tradicional.
- Os modelos identificam associações nos dados analisados; não estabelecem causalidade.

## Integrantes

- Gabriela Gomes Mattoso
- Daniela Ferreira Chame
- Giovanna Brito Silva Ribeiro
- Isabella Oliveira Araujo Barbosa Moreira
- Lívia Hilbert de Oliveira

## Professores

- Gabriel Barbosa da Fonseca
- Marco Paulo Soares Gomes

## Trajetória do projeto

Este checklist registra o caminho que aparece nos notebooks e no relatório do grupo. Ele não tenta fazer o projeto parecer linear ou perfeito: houve exploração, teste de abordagens e revisão metodológica. Como os materiais não datam cada atividade, a ordem abaixo representa a evolução identificável entre as versões, e não um calendário exato do primeiro período.

- [x] **Levantamentos iniciais:** exploração de dados de matrículas e de características das escolas, registrada nos notebooks iniciais de análise de matrículas e dados escolares.
- [x] **Exploração mais ampla do Censo Escolar:** análise de atributos institucionais de 2025, incluindo matrículas, infraestrutura, recursos humanos e características das escolas.
- [x] **Teste de uma abordagem por índice de vulnerabilidade:** o notebook `analise_vulnerabilidade_educacional.ipynb`, recebido entre os materiais complementares, preserva uma etapa em que foi construído um índice institucional e testados classificadores como Random Forest, Gradient Boosting e KNN. O próprio material também registra experimentos posteriores com a taxa de abandono. Ele ajuda a mostrar a mudança de abordagem, mas não deve ser confundido com a metodologia final consolidada no relatório.
- [x] **Revisão da variável-alvo:** nos materiais posteriores, a análise passa a utilizar a taxa oficial de abandono do Ensino Médio de 2024 como variável-alvo, em vez de classificar as escolas pelo índice próprio de vulnerabilidade.
- [x] **Integração e delimitação da base:** combinação do Censo Escolar 2025 com as Taxas de Rendimento Escolar 2024 pela chave `CO_ENTIDADE`, considerando escolas com Ensino Médio regular e matrículas nesse nível.
- [x] **Análise exploratória:** investigação da distribuição do abandono e de características institucionais, como infraestrutura, acessibilidade, localização, recursos humanos e participação institucional.
- [x] **Preparação das variáveis:** limpeza, seleção e criação de variáveis derivadas para representar dimensões institucionais utilizadas no estudo.
- [x] **Pré-processamento e divisão dos dados:** preparação dos atributos e organização dos conjuntos de treino e teste, conforme descrito no relatório e no notebook de modelagem.
- [x] **Árvore de Decisão:** aplicação de um modelo interpretável para examinar regras associadas aos níveis de abandono.
- [x] **Random Forest:** aplicação de um modelo preditivo como parte do sistema de alerta.
- [x] **Sistema de alerta em cascata:** classificação em três níveis — Sem abandono, Risco moderado e Alto risco — organizada em duas etapas.
- [x] **Comparação e interpretação:** análise do desempenho dos modelos, das variáveis destacadas e das limitações do estudo.
- [x] **Consolidação do trabalho:** registro da metodologia, dos resultados e das limitações no relatório do grupo e nos notebooks.

**O que o histórico do Git comprova:** os principais arquivos do projeto foram registrados no repositório em 26/08/2026, em commits de criação e envio de arquivos. Isso confirma quando o material foi colocado no GitHub, mas não permite concluir em que dia cada análise foi feita pelo grupo nem estabelecer a ordem exata de todas as atividades acadêmicas.

**O que não foi inventado:** não foram atribuídas datas individuais às etapas, nem afirmado que a sequência acima corresponde a semanas específicas. O notebook de vulnerabilidade é citado como uma abordagem anterior encontrada nos materiais complementares, não como parte da versão final do método.

O histórico de versões também registra estes marcos:

| Versão | Registro |
|---|---|
| 0.0.1 | Preparação dos dados. |
| 0.1.0 | Indução do primeiro modelo do agente inteligente. |
| 0.1.1 | Atualização da documentação; código permaneceu inalterado. |
