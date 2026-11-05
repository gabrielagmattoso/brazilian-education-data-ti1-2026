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

Este checklist reconstrói o percurso a partir dos materiais disponíveis: os notebooks iniciais de exploração, as versões anteriores de análise/modelagem, o notebook exploratório atual e o relatório do grupo. A sequência abaixo registra a evolução identificável nos arquivos; eles não informam datas suficientes para atribuir cada etapa a semanas ou meses específicos do primeiro período.

- [x] **Primeiros levantamentos de dados:** exploração das bases de matrículas e de informações sobre docentes, registrada nos notebooks `tabela_matricula_docente.ipynb` e em sua segunda versão.
- [x] **Ampliação da análise institucional:** exploração de atributos das escolas do Censo Escolar 2025, incluindo matrículas, infraestrutura, recursos humanos e características institucionais.
- [x] **Primeira abordagem de vulnerabilidade:** desenvolvimento de uma versão que construía um índice de vulnerabilidade institucional e testava modelos de classificação, incluindo Random Forest, Gradient Boosting e KNN. Essa etapa está preservada no arquivo `analise_vulnerabilidade_educacional.ipynb`, incluído no material de versões anteriores.
- [x] **Revisão da abordagem metodológica:** os materiais posteriores registram a opção por não utilizar um índice próprio como variável-alvo e passar a utilizar a taxa oficial de abandono do Ensino Médio de 2024.
- [x] **Integração das bases:** combinação dos dados do Censo Escolar 2025 e das Taxas de Rendimento Escolar 2024 pela chave `CO_ENTIDADE`, com recorte de escolas que ofertam Ensino Médio regular e possuem matrículas nesse nível.
- [x] **Análise exploratória:** investigação da distribuição do abandono e das características institucionais, incluindo infraestrutura, acessibilidade, localização, recursos humanos e participação institucional.
- [x] **Preparação das variáveis:** limpeza, seleção e criação de variáveis derivadas para representar dimensões institucionais utilizadas na análise.
- [x] **Pré-processamento e divisão dos dados:** preparação dos atributos para os modelos e organização dos conjuntos de treino e teste, conforme descrito no relatório e no notebook de modelagem.
- [x] **Árvore de Decisão:** utilização de um modelo interpretável para examinar regras associadas aos níveis de abandono.
- [x] **Random Forest:** utilização de um modelo preditivo como parte do sistema de alerta.
- [x] **Sistema de alerta em cascata:** organização da classificação em três níveis — Sem abandono, Risco moderado e Alto risco — por meio de duas etapas.
- [x] **Comparação dos modelos e interpretação dos resultados:** análise do desempenho, das variáveis destacadas e da convergência entre os modelos.
- [x] **Consolidação e documentação:** organização da metodologia, dos resultados e das limitações no relatório do grupo e nos notebooks disponibilizados no repositório.

**Nota sobre a cronologia:** os arquivos comprovam essas linhas de trabalho e permitem reconstruir a evolução metodológica, mas não comprovam datas exatas nem a ordem de cada atividade dentro do calendário acadêmico. Por isso, o checklist apresenta a sequência entre versões e etapas documentadas, sem inventar datas. Os notebooks e arquivos de versões anteriores são registros do processo, não etapas que devam ser apagadas por não corresponderem à versão final.

O histórico de versões também registra estes marcos:

| Versão | Registro |
|---|---|
| 0.0.1 | Preparação dos dados. |
| 0.1.0 | Indução do primeiro modelo do agente inteligente. |
| 0.1.1 | Atualização da documentação; código permaneceu inalterado. |
