## Configurações Globais

### Configurações globais na primeira utilização do comando git:

    git config --global user.name "Vitor Monteiro"
    git config --global user.email "vitor.monteiro@tce.pa.gov.br"

### Desabilita a checagem de certificado no projeto

* SSL certificate problem: unable to get local issuer certificate

    git config http.sslVerify false

### Desabilita a checagem de certificado de forma global

    git config --global http.sslverify false

---
 
## Gestão de repositórios remotos

### Lista repositórios remotos. Rodar na pasta do projeto

    git remote -v

### Adiciona um repositório. Rodar na pasta do projeto

    git remote add origin <new_remote_repository_url>
    git remote add origin https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git

### Muda de repositório. Rodar na pasta do projeto

    git remote set-url origin git@your.git.repo.example.com:user/repository2.git

### Remove o repositório

    git remote remove <name_of_the_remote>
    git remote remove origin
    git remote rm origin

---

## Gestão de ramificações

### Verifica o branch atual

    git branch

### Muda a branch da pasta atual

    git checkout rancho-texas

### Cria um novo branch (ramificação)

    git checkout -b rancho-texas

### Muda o branch de trabalho

    git checkout master

### Remove um branch

    git branch --delete rancho-texas

---

## Gestão de código

### Inicializa um repositório git vazio

    git init

### Commit de atualizações no código (na pasta do projeto):

    git add . 
    git commit -m "Atualiza para versão 1.0"
    git push origin master

### Verifica se existem alterações que ainda não foram comitadas

    git status

### Mostra as diferenças entre a versão local e a do repositório

    git diff

### Baixa para o repositório local a versão do repositório remoto

    git pull origin

### Clona o repositório de terceiros

    git clone https://github.com/git/git

### Adicionar os arquivos modificados e faz o commit para uma branch específica

    git add Dockerfile docker-compose-10.0.0-rc1.yml glpi-start.sh
    git commit -m "Versao 10.0.0-rc1"
    git push origin versao_10.0.0-rc1

---

## Migração dos projetos da CIS do Azure DevOps antigo on-premises (http://azuredevops.tce.pa/) para o Azure DevOps na nuvem (https://dev.azure.com/tcepa/)

```sh
# Clona repositório do azure devops antigo
git clone http://azuredevops.tce.pa/CIS/Cluster%20Kubernetes/_git/documentacao

# Entra na pasta do projeto
cd pasta-projeto/

# Remove a referência antiga do repositório
git remote remove origin

# Adiciona a nova referência do repositório
git remote add origin https://tcepa@dev.azure.com/tcepa/cluster-kubernetes/_git/cluster-kubernetes

# Cria a branch 'main'
git checkout -b main

# Remove a branch 'master'
git branch --delete master

# Upload dos arquivos para o novo repositório
git push -u origin --all
```