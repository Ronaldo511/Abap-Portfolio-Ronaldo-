# 🚚 Sistema de Gestão e Escalonamento de Frota Logística (ABAP OO)

![SAP S/4HANA](https://img.shields.io/badge/SAP-S%2F4HANA-blue)
![ABAP 7.40+](https://img.shields.io/badge/ABAP-7.40%2B-orange)
![Paradigma](https://img.shields.io/badge/Paradigma-Orientado%20a%20Objetos-green)

## 📌 Visão Geral do Projeto

Este projeto consiste em uma solução ABAP desenvolvida para otimizar o planejamento operacional de frotas no setor logístico. O programa realiza o **escalonamento dinâmico de reservas de veículos** dentro de uma janela de tempo definida pelo usuário, aplicando regras de negócio para depreciação de ativos e exibição dos resultados em um relatório interativo (**ALV Grid**).

O grande diferencial da solução é a integração entre a **regra de negócio operacional (chão de fábrica e logística)** e uma **arquitetura de código limpa e moderna (ABAP 7.40+)**.

---

## ⚙️ Funcionalidades Principais

- **Escalonamento Proporcional de Janelas:** Distribuição automática da frota em blocos de tempo baseados na amplitude do período informado.
- **Depreciação Financeira Dinâmica:** Cálculo progressivo de desvalorização dos veículos com base no ano de fabricação (taxa composta de 10% a.a.).
- **Interface Orientada a Objetos (ABAP OO):** Encapsulamento de lógica de negócio em classes locais (`LCL_FROTA`), garantindo fácil manutenção e escalabilidade.
- **Relatório ALV Interativo:** Apresentação dos dados processados via `CL_SALV_TABLE` com formatação personalizada de colunas.

---

## 🏗️ Arquitetura e Lógica de Negócio

### 1. Escalonamento da Frota
Dada uma janela total de dias ($D$), o algoritmo calcula o intervalo individual ($J$) por veículo proporcionalmente:

$$J = \frac{\text{Data Fim} - \text{Data Início}}{\text{Total de Veículos}}$$

A data de reserva de cada veículo é atribuída sequencialmente com base na sua posição no fluxo operacional.

### 2. Cálculo de Depreciação
A depreciação é calculada dinamicamente utilizando a idade do veículo ($I = \text{Ano Atual} - \text{Ano do Veículo}$):

$$\text{Valor Final} = \text{Valor Base} \times (0.90)^I$$

---

## 💻 Recursos Técnicos & Sintaxes Utilizadas

- **ABAP 7.40+:** Construtores de valor `VALUE #()`, declarações em linha `DATA(...)`, e instanciação simplificada `NEW`.
- **Orientação a Objetos:** Separação clara entre camada de apresentação, seleção de dados e processamento de regras de negócio.
- **ALV Object Model:** Utilização da classe padrão `CL_SALV_TABLE` para exibição de dados com tratamento de exceções (`CX_SALV_MSG`).

---

## 📁 Estrutura do Código

| Componente | Tipo | Descrição |
| :--- | :--- | :--- |
| `lcl_frota` | Class (Def/Imp) | Lógica principal de processamento de frota e depreciação. |
| `p_datini` / `p_datfim` | Selection Parameters | Parâmetros de entrada de intervalo de datas na tela de seleção. |
| `mt_veiculos` | Internal Table | Tabela interna estruturada para manipulação dos dados em memória. |

---

## 🚀 Como Executar o Código no Ambiente SAP

1. Acesse a transação **SE38** ou **SE80** em seu ambiente SAP / SAP GUI (ou ADT no Eclipse).
2. Crie um programa executável do tipo *Report* com o nome `ZR_GESTAO_FROTA_LOGISTICA`.
3. Cole o código do arquivo `zr_gestao_frota_logistica.abap` contido neste repositório.
4. Ative o programa (`Ctrl + F3`) e execute (`F8`).
5. Informe o período desejado na tela de seleção e visualize a tabela ALV gerada.

---

## 👨‍💻 Autor

**Ronaldo**  
*Desenvolvedor ABAP em transição de carreira | Especialista em Operações Logísticas*  
- LinkedIn: [Seu Perfil do LinkedIn](Https://www.linkedin.com/in/ronaldo-silva-dev-erp-abap-ccharp)
