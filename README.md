---

# 🧰 Projeto Oficina Mecânica – Modelo Conceitual e Lógico

Este projeto foi desenvolvido como parte da **Formação SQL Specialist** da **Digital Innovation One (DIO)**.
O objetivo foi criar o **modelo conceitual e lógico** de um sistema de **controle e gerenciamento de Ordens de Serviço (OS)** para uma oficina mecânica, com base na narrativa proposta pela instrutora.

---

## 🎯 Objetivo do Desafio

Construir um **esquema de banco de dados** que represente de forma completa o funcionamento de uma oficina mecânica, considerando:

* **Controle de Ordens de Serviço (OS)**, com datas, status e valor total.
* **Cadastro de clientes** e seus respectivos veículos.
* **Equipes e mecânicos**, com especialidades e histórico de alocação.
* **Serviços e peças** que compõem cada OS, permitindo cálculo do valor total.
* **Relacionamentos N:M** entre OS–Serviço e OS–Peça.

---

## 🏗️ Descrição do Projeto

O modelo foi construído no **MySQL Workbench**, seguindo os princípios da **modelagem conceitual e relacional**, representando os principais processos de uma oficina:

### 👥 Cliente

* Identificado por `idCliente`, armazena **nome**, **telefone** e **e-mail**.
* Um cliente pode possuir **vários veículos**.

### 🚗 Veículo

* Cada veículo pertence a **um cliente** e possui atributos como **placa**, **modelo**, **ano** e **chassi**.
* Um veículo pode ter **várias Ordens de Serviço** associadas.

### 🧾 Ordem de Serviço (OS)

* Contém informações sobre **data de emissão**, **data prevista**, **data de conclusão**, **status**, **autorização**, e **valor total**.
* Cada OS está vinculada a **um veículo** e **uma equipe responsável**.
* Uma OS pode conter **vários serviços** e **várias peças** (relacionamentos N:M).

### 🧑‍🔧 Equipe

* Representa o grupo de mecânicos responsáveis pela execução da OS.
* Cada equipe pode realizar **várias ordens de serviço**.

### 🔩 Mecânico

* Armazena **nome**, **endereço** e **especialidade**.
* Um mecânico pode participar de **várias equipes**, e uma equipe é composta por **vários mecânicos** (relacionamento N:M via entidade associativa `EquipeMecanico`).

### 🧱 Entidade Associativa: EquipeMecanico

* Registra **data de início** e **data de término** da participação do mecânico na equipe.
* Garante o controle histórico de alocação de pessoal.

### 🧰 Serviço

* Define cada tipo de **serviço** (como conserto ou revisão).
* Armazena **descrição**, **tipo_serviço** e **valor** de referência da mão de obra.
* Está relacionado à OS por meio da tabela **OS_Servico** (N:M).

### ⚙️ Peça

* Armazena **descrição** e **valor_unitário**.
* Relaciona-se à OS por meio da tabela **OS_Peca** (N:M).

### 🧾 Tabelas Associativas

* **OS_Servico:** representa a relação entre uma OS e os serviços executados.
* **OS_Peca:** representa a relação entre uma OS e as peças utilizadas.

---

## 🔗 Principais Relacionamentos

* Cliente **1..N** Veículo
* Veículo **1..N** OrdemServico
* Equipe **1..N** OrdemServico
* Mecânico **N..M** Equipe (via EquipeMecanico)
* OrdemServico **N..M** Serviço (via OS_Servico)
* OrdemServico **N..M** Peça (via OS_Peca)

---

## 📋 Regras de Negócio Representadas

* Um cliente pode ter **vários veículos** cadastrados.
* Cada veículo pode ter **várias Ordens de Serviço** abertas.
* Cada OS é executada por **uma equipe** e contém **vários serviços e peças**.
* O **valor total da OS** é composto pela soma da mão de obra (serviços) e das peças utilizadas.
* Cada mecânico pertence a uma ou mais equipes, com **registro histórico de participação**.

---

## 💾 Ferramenta Utilizada

* **MySQL Workbench 8.x**

  * Modelagem Entidade-Relacionamento (EER Diagram)
  * Tipos de dados padrão (`INT`, `VARCHAR(45)`, `DATE`, `DECIMAL`)
  * Cardinalidades e chaves estrangeiras mapeadas visualmente

---

## 🖼️ Diagrama do Projeto

Arquivo incluído no repositório:
**oficina.png** (modelo lógico exportado do MySQL Workbench)

---

## 💡 Conclusão

O projeto consolida os conceitos de **modelagem de dados conceitual e lógica**, representando um cenário real de **oficina mecânica**.
A estrutura proposta permite gerenciar clientes, veículos, ordens de serviço, peças, serviços e equipes de forma integrada, atendendo aos requisitos funcionais descritos na narrativa.

---

✨ *Projeto desenvolvido por Bianca Aguiar Esteves durante a Formação SQL Specialist – DIO.*

---

