# 📊 Projeto dbt — Dbt Ecommerce

Este repositório contém um projeto **dbt (data build tool)** desenvolvido para a modelagem e transformação de dados no **BigQuery**, seguindo boas práticas de **engenharia analítica** e arquitetura em camadas.

O objetivo do projeto é transformar dados brutos em **tabelas analíticas**, prontas para consumo por ferramentas de BI e análises avançadas.

---

## 🧱 Stack utilizada

- **dbt Core** 1.11.x  
- **BigQuery**
- **SQL**
- **Python** (ambiente virtual)
- **Git / GitHub**

---

## 📂 Estrutura do projeto

```text
models/
  projeto_um/
    staging/        # Dados brutos tratados (stg)
    intermediate/   # Regras de negócio (int)
    marts/          # Tabelas finais analíticas
seeds/              # Dados estáticos (CSV)
tests/              # Testes customizados
macros/             # Macros reutilizáveis
snapshots/          # Snapshots (SCD)
