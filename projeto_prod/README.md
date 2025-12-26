## 📥 Como utilizar o projeto

### 1️⃣ Copiar a URL do repositório
No GitHub, clique em **Code → HTTPS** e copie a URL do repositório.


1. Clone o repositorio:
```bash
git clone https://github.com/seu_usuario/projeto_prod.git
```

2. Acessar a pasta do projeto
```bash
cd projeto_prod
```

3. Configure o ambiente
```bash
python -m venv venv
venv\Scripts\activate
```

4. Instalar dependências
```bash
pip install -r requirements.txt
```

---
### 2️⃣ Configure o bigquery

1. Copiar o arquivo `env_example`

Na raiz do projeto existe um arquivo chamado `env_example`, que serve como **modelo**. Faça uma cópia desse arquivo e renomeie para `.env`:

```bash
cp env_example .env
```

2. Atualize as credenciais do `env`
```bash
export GCP_DEV_PROJECT="seu-dev-projeto-gcp"
export DBT_DEV_SCHEMA="seu-dev-dataset"
export GCP_DEV_KEYFILE_PATH="/caminho/para/service_account.json"

export GCP_PROD_PROJECT="seu-prod-projeto-gcp"
export DBT_PROD_SCHEMA="seu-prod-dataset"
export GCP_PROD_KEYFILE_PATH="/caminho/para/service_account.json"
```

3. Carregar as variáveis de ambiente
```bash
export $(cat .env | xargs)
```

ou

Altere diretamento no profile.yml. Nesse caso, **não subo o profile para o seu repositorio git**
```bash
projeto_prod:
  target: dev
  outputs:
    dev:
      type: bigquery
      method: service-account
      project: "{{env_var('GCP_DEV_PROJECT')}}"
      dataset: "{{env_var('DBT_DEV_SCHEMA')}}"
      threads: 4
      keyfile: "{{env_var('GCP_DEV_KEYFILE_PATH')}}"
```

### 3️⃣ Teste de conexão
```bash
dbt debug
```

### 4️⃣ Rode o dbt
```bash
dbt run
```