# 🚚 Sistema de Gestão, Precificação e Reserva de Frota (ABAP)

![SAP S/4HANA](https://img.shields.io/badge/SAP-S%2F4HANA-blue)
![ABAP 7.40+](https://img.shields.io/badge/ABAP-7.40%2B-orange)
![Banco de Dados Z](https://img.shields.io/badge/Persist%C3%AAncia-Tabela%20Z-green)

## 📌 Visão Geral do Projeto

Este projeto consiste em um programa executável (*Report*) desenvolvido em ABAP para simular a gestão, filtragem e reserva de veículos em uma frota logística. 

A solução integra a **persistência de dados em tabela transparente (`ZRESERVAS_DB_V3`)**, a interatividade na tela de seleção com geração de dados de teste via botão customizado e o processamento de regras de negócio avançadas, incluindo **distribuição de janelas operacionais de 20%** e **depreciação de ativos**.

---

## 📷 Demonstração do Sistema

![Demonstração da Execução do Report](https://github.com/user-attachments/assets/7d87ab6b-e7bd-46b3-bed4-71108dd1d2a0)

---

https://github.com/user-attachments/assets/c45c5afb-6a53-4639-8589-7fde9a0763bc



## ⚙️ Funcionalidades Principais

- **Persistência em Banco de Dados (Tabela Z):** Gravação e manipulação de registros de reservas diretamente na tabela transparente `ZRESERVAS_DB_V3`.
- **Geração Dinâmica de Massa de Teste:** Botão de ação na `SELECTION-SCREEN` (`USER-COMMAND 'GERA'`) para inserção automática de dados de teste via `INSERT` e `COMMIT WORK`.
- **Filtro de Usabilidade e Valores:** Parâmetros `P_V_MIN` e `P_V_MAX` para validação e restrição de faixas de preço aceitáveis na locação.
- **Escalonamento Proporcional (Janela de 20%):** Algoritmo que calcula o intervalo entre a data inicial e final (`S_DATA`) e distribui os veículos proporcionalmente ao longo do tempo.
- **Precificação e Depreciação de Ativos:** Aplicação de efeito cascata na valoração dos veículos com base no ano de fabricação.
- **Relatório Formatado e Tratamento de Exceções:** Saída visual estruturada com molduras e feedback visual (`FORMAT COLOR COL_NEGATIVE`) em cenários de busca sem resultados.

---

## 🏗️ Estrutura e Componentes da Solução

| Componente | Tipo | Descrição |
| :--- | :--- | :--- |
| `zreservas_db_v3` | Tabela Transparente | Estrutura de banco de dados para armazenamento do histórico de reservas. |
| `P_NOME` | Parameter | Nome do cliente impresso no relatório final (`LOWER CASE`). |
| `P_V_MIN` / `P_V_MAX` | Parameters | Faixa mínima e máxima de valor para filtragem dos modelos da frota. |
| `S_DATA` | Select-Options | Intervalo de datas utilizado para calcular as janelas de reserva de 20%. |
| `BTN_GERA` | Pushbutton | Botão interativo acionado pelo evento `AT SELECTION-SCREEN`. |

---

## 💻 Recursos Técnicos & Sintaxes Utilizadas

- **Sintaxes Modernas (7.40+):** Construtor de tabelas internas `VALUE #()`, *String Templates* `|{ ... }|` e declarações em linha `DATA(...)`.
- **Eventos de Relatório:** Uso estratégico de `INITIALIZATION`, `AT SELECTION-SCREEN` e `START-OF-SELECTION`.
- **Formatação de Saída:** Uso de comandos `WRITE` avançados com formatação de linhas (`SY-VLINE`), moeda (`CURRENCY 'BRL'`) e mensagens de status (`MESSAGE ... TYPE 'S'`).

---

## 🚀 Como Executar no Ambiente SAP

1. Certifique-se de que a tabela transparente `ZRESERVAS_DB_V3` esteja ativa no Dictionary (**SE11**).
2. Acesse a transação **SE38** ou **SE80** (ou ADT no Eclipse).
3. Crie o programa executável `Z_EXIBE_RESERVAS_V3`.
4. Cole o código-fonte presente em `src/Z_EXIBE_RESERVAS_V3.abap`.
5. Ative (`Ctrl + F3`) e execute (`F8`).
6. *(Opcional)* Clique no botão **"GERA DADOS DE TEXTO"** na tela inicial para popular a massa de dados inicial no banco.

---

## 👨‍💻 Autor

**Ronaldo Silva**  
*Desenvolvedor ABAP em transição de carreira | Especialista em Operações Logísticas*  
- **LinkedIn:** [ronaldo-silva-550151322](https://www.linkedin.com/in/ronaldo-silva-550151322)
