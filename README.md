#  Projeto EER para Oficina Mecânica - Modelo Conceitual
**Modelo conceitual de banco de dados para um sistema de Oficina Mecânica.**

---

##  Sobre o Projeto
Este projeto consiste na **modelagem conceitual de um sistema de controle de Ordens de Serviço (OS)** para uma oficina mecânica.  
O esquema foi desenvolvido no **MySQL Workbench** a partir da narrativa proposta no desafio da plataforma DIO, visando representar clientes, veículos, equipes de mecânicos, ordens de serviço, serviços e peças utilizadas.

---

## 📌 Narrativa do Desafio
- Clientes levam veículos à oficina mecânica para consertos ou revisões periódicas.  
- Cada veículo é associado a uma **Ordem de Serviço (OS)**.  
- Uma **equipe de mecânicos** é responsável pela execução de cada OS.  
- Cada OS contém: número, data de emissão, valor total, status e data de conclusão.  
- Serviços são cadastrados em uma tabela de referência de mão de obra.  
- Peças utilizadas também compõem o valor da OS.  
- Mecânicos possuem código, nome, endereço e especialidade.  

---

## 🎯 Modelagem do Projeto

### Entidades e Atributos

- **Cliente**
  - idCliente (PK)  
  - nome  
  - endereço  
  - telefone  

- **Veículo**
  - idVeiculo (PK)  
  - placa  
  - modelo  
  - ano  
  - idCliente (FK)  

- **Mecânico**
  - idMecanico (PK)  
  - nome  
  - endereço  
  - especialidade  

- **Equipe**
  - idEquipe (PK)  
  - nome_equipe  

- **Equipe/Mecanico** (associativa)
  - idEquipe (FK)  
  - idMecanico (FK)  

- **Serviço**
  - idServico (PK)  
  - descricao  
  - valor_mao_obra  

- **Peça**
  - idPeca (PK)  
  - descricao  
  - valor_unitario  

- **Ordem Servico (OS)**
  - idOs (PK)  
  - data_emissao  
  - data_conclusao  
  - valor_total  
  - status  
  - idVeiculo (FK)  
  - idEquipe (FK)  

- **OS Servico** (associativa)
  - idOs (FK)  
  - idServico (FK)  
  - quantidade  

- **OS Peca** (associativa)
  - idOs (FK)  
  - idPeca (FK)  
  - quantidade  

---

## 🔗 Relacionamentos
- Cliente **1:N** Veículo  
- Veículo **1:N** Ordem Servico  (OS) 
- Ordem_Servico **N:N** Serviço (via OS Servico)  
- Ordem_Servico **N:N** Peça (via OS Peca)  
- Ordem_Servico **N:1** Equipe  
- Equipe **N:N** Mecânico (via Equipe/Mecanico)  

---

## 🔑 Pontos de Destaque
Alguns pontos não estavam explícitos na narrativa e foram definidos por interpretação lógica:  
- Foi adotado que Cliente pode possuir **vários veículos**.  
- Para Ordem de Serviço foi considerado que pode se ter **vários serviços e várias peças**.  
- Mecânicos podem pertencer a mais de uma equipe (relacionamento N:N).  
- Para o valor total da OS deve ser calculado a partir da soma de serviços + peças.  

---  

## 🛠️ Ferramentas Utilizadas
- **MySQL Workbench** → modelagem conceitual e refinamento do diagrama.  
- **MySQL** → implementação das tabelas e constraints.  

---

## 📂 Estrutura do Repositório
📦 dio-projeto-ecommerce-eer   
┣ README.md  
┣ diagrama_oficina_img.png **# Diagrama EER exportado**   
┗ diagrama_oficina.mwb **# Arquivo nativo do MySQL Workbench**  

## 📝 Autor
Desenvolvido por **Fábio Barros de Oliveira** para o desafio DIO.


*📌 Projeto criado para fins educacionais e para compor o portfólio de modelagem de banco de dados.*

