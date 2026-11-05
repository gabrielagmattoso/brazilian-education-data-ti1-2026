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

O checklist abaixo acompanha o percurso que aparece nos notebooks: da organização dos dados até a análise dos modelos e o registro dos resultados. A ordem representa as etapas do trabalho documentadas no código, não datas específicas.

- [x] **Preparação dos dados:** definição das bases utilizadas e leitura dos arquivos do Censo Escolar 2025 e das Taxas de Rendimento Escolar 2024.
- [x] **Recorte das escolas:** seleção das instituições que ofertam Ensino Médio regular e possuem matrículas nesse nível de ensino.
- [x] **Integração das bases:** combinação das informações pela chave `CO_ENTIDADE`.
- [x] **Análise exploratória:** observação da distribuição das taxas de abandono e das características institucionais das escolas.
- [x] **Preparação das variáveis:** seleção, limpeza e criação de variáveis derivadas para representar aspectos institucionais.
- [x] **Pré-processamento:** organização das variáveis para utilização nos modelos.
- [x] **Árvore de Decisão:** aplicação do modelo para explorar regras interpretáveis e fatores associados ao abandono.
- [x] **Random Forest:** aplicação do modelo na etapa preditiva.
- [x] **Sistema de alerta:** organização da classificação em três níveis de risco, por meio de etapas em cascata.
- [x] **Comparação e conclusões:** análise dos resultados dos modelos, dos fatores destacados e das limitações do estudo.
- [x] **Documentação:** registro do projeto, da metodologia e dos resultados no repositório.

O histórico de versões também registra estes marcos:

| Versão | Registro |
|---|---|
| 0.0.1 | Preparação dos dados. |
| 0.1.0 | Indução do primeiro modelo do agente inteligente. |
| 0.1.1 | Atualização da documentação; código permaneceu inalterado. |
