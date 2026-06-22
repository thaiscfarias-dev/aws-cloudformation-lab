# 🚀 Implementando Minha Primeira Stack com AWS CloudFormation

## 📖 Sobre o Projeto

Este repositório foi criado como parte do desafio da DIO para praticar os conceitos de **AWS CloudFormation**, um dos principais serviços de Infraestrutura como Código (IaC) da AWS.

O objetivo foi compreender como automatizar a criação de recursos na nuvem através de templates, eliminando a necessidade de configurações manuais e tornando os ambientes mais padronizados, reproduzíveis e seguros.

---

# 🎯 Objetivos do Desafio

✅ Entender o funcionamento do AWS CloudFormation

✅ Criar minha primeira Stack

✅ Aplicar conceitos de Infraestrutura como Código (IaC)

✅ Documentar o processo de aprendizagem

✅ Utilizar o GitHub como ferramenta de documentação técnica

---

# ☁️ O que é AWS CloudFormation?

O AWS CloudFormation é um serviço da AWS que permite criar, atualizar e gerenciar recursos de infraestrutura utilizando arquivos de configuração escritos em YAML ou JSON.

Em vez de criar recursos manualmente pelo Console da AWS, você descreve toda a infraestrutura em um arquivo chamado Template.

O CloudFormation interpreta esse template e cria automaticamente todos os recursos necessários.

---

## 💡 Exemplo sem CloudFormation

Imagine que você precise criar:

* 1 VPC
* 2 Subnets
* 1 Security Group
* 1 Instância EC2

Sem CloudFormation você teria que:

1. Acessar o Console AWS
2. Criar cada recurso manualmente
3. Configurar dependências
4. Repetir tudo novamente caso precise recriar o ambiente

---

## 💡 Exemplo com CloudFormation

Você cria um único arquivo YAML:

```yaml
Resources:
  MinhaInstancia:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
```

Depois basta executar a Stack.

O CloudFormation cria automaticamente os recursos definidos.

---

# 🏗️ Conceitos Fundamentais

## 📄 Template

É o arquivo que descreve a infraestrutura.

Pode ser escrito em:

* YAML (mais utilizado)
* JSON

Exemplo:

```yaml
AWSTemplateFormatVersion: '2010-09-09'

Resources:
  MeuBucket:
    Type: AWS::S3::Bucket
```

---

## 📦 Stack

Uma Stack é uma coleção de recursos AWS criada a partir de um Template.

Exemplo:

Uma Stack pode conter:

* EC2
* S3
* IAM
* VPC
* RDS

Todos gerenciados como uma única unidade.

---

## 🔄 Change Sets

Permitem visualizar alterações antes de aplicá-las.

Muito útil para evitar erros em ambientes produtivos.

---

## 📋 Parameters

Permitem personalizar o template sem alterar o código.

Exemplo:

```yaml
Parameters:

  InstanceType:
    Type: String
    Default: t2.micro
```

Na criação da Stack, o usuário pode escolher outro tipo de instância.

---

## 📤 Outputs

Permitem exibir informações importantes após a criação da Stack.

Exemplo:

```yaml
Outputs:

  InstanceId:
    Value: !Ref MinhaInstancia
```

---

# 🔥 Vantagens do CloudFormation

## 🚀 Automação

Criação automática da infraestrutura.

## 🔄 Reutilização

O mesmo template pode ser utilizado várias vezes.

## 📚 Versionamento

Os templates podem ser armazenados no GitHub.

## 🛡️ Padronização

Evita erros manuais.

## 💰 Economia de Tempo

Reduz significativamente o tempo de provisionamento.

---

# 🏛️ Estrutura de um Template CloudFormation

Um template geralmente possui:

```yaml
AWSTemplateFormatVersion
Description
Parameters
Mappings
Conditions
Resources
Outputs
```

---

## Exemplo Completo

```yaml
AWSTemplateFormatVersion: '2010-09-09'

Description: Minha primeira Stack

Parameters:

  InstanceType:
    Type: String
    Default: t2.micro

Resources:

  MinhaInstancia:
    Type: AWS::EC2::Instance

    Properties:
      ImageId: ami-123456789
      InstanceType: !Ref InstanceType

Outputs:

  InstanceID:
    Description: ID da Instância
    Value: !Ref MinhaInstancia
```

---

# ⚙️ Como Criar uma Stack

## 1️⃣ Acessar o CloudFormation

No Console AWS:

```text
AWS Console
→ CloudFormation
```

## 2️⃣ Criar Stack

Selecionar:

```text
Create Stack
```

## 3️⃣ Escolher Template

Opções:

* Upload de arquivo
* Amazon S3 URL

## 4️⃣ Configurar Nome

Exemplo:

```text
MinhaPrimeiraStack
```

## 5️⃣ Informar Parâmetros

Caso existam parâmetros configuráveis.

## 6️⃣ Revisar Configurações

Verificar:

* Recursos
* Permissões IAM
* Tags

## 7️⃣ Criar Stack

Clicar em:

```text
Create Stack
```

---

# 🔍 Monitorando a Criação

Na aba:

```text
Events
```

É possível acompanhar:

* Recursos sendo criados
* Possíveis erros
* Status atual

---

## Estados Comuns

| Status             | Significado          |
| ------------------ | -------------------- |
| CREATE_IN_PROGRESS | Criando recursos     |
| CREATE_COMPLETE    | Criação concluída    |
| CREATE_FAILED      | Falha na criação     |
| UPDATE_IN_PROGRESS | Atualizando recursos |
| DELETE_IN_PROGRESS | Removendo recursos   |
| DELETE_COMPLETE    | Exclusão concluída   |

---

# 🧠 Aprendizados Obtidos

Durante a realização deste laboratório aprendi:

* O conceito de Infraestrutura como Código (IaC)
* Como criar recursos AWS utilizando Templates
* Como criar e gerenciar Stacks
* Como reutilizar infraestrutura através de código
* Como monitorar eventos de provisionamento
* Como utilizar YAML para definir recursos AWS
* A importância do versionamento da infraestrutura

---

# ⚠️ Boas Práticas

## ✅ Utilize YAML

Mais legível que JSON.

## ✅ Versione os Templates

Armazene no GitHub.

## ✅ Use Parâmetros

Evite valores fixos.

## ✅ Documente Tudo

Facilita manutenção futura.

## ✅ Exclua Recursos Não Utilizados

Evita cobranças inesperadas.

---

# 🛠️ Principais Recursos AWS Compatíveis

O CloudFormation suporta centenas de recursos.

| Serviço  | Tipo                  |
| -------- | --------------------- |
| EC2      | AWS::EC2::Instance    |
| S3       | AWS::S3::Bucket       |
| IAM      | AWS::IAM::Role        |
| Lambda   | AWS::Lambda::Function |
| DynamoDB | AWS::DynamoDB::Table  |
| RDS      | AWS::RDS::DBInstance  |
| VPC      | AWS::EC2::VPC         |

---

# 📚 Infraestrutura como Código (IaC)

Infraestrutura como Código é a prática de gerenciar infraestrutura utilizando arquivos de configuração.

Ao invés de:

❌ Criar manualmente

Fazemos:

✅ Definição em código

Benefícios:

* Reprodutibilidade
* Automação
* Escalabilidade
* Controle de versão
* Redução de erros

---

# 🏆 Conclusão

O AWS CloudFormation é uma ferramenta essencial para profissionais que trabalham com computação em nuvem. Ele permite criar ambientes completos de forma automatizada, segura e padronizada através de código.

Este laboratório foi importante para compreender os conceitos de Infraestrutura como Código (IaC) e como a AWS automatiza o provisionamento de recursos utilizando Templates e Stacks.

---

# 📖 Referências

* AWS CloudFormation Documentation
* AWS CloudFormation User Guide
* GitHub Docs
* GitHub Markdown Guide

---

⭐ Projeto desenvolvido para fins educacionais no Bootcamp da DIO.
