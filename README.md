# Desafio: Criando sua Primeira Stack com AWS CloudFormation

Este repositório faz parte do desafio de aprendizado para implementar a primeira Stack na **AWS** utilizando o **AWS CloudFormation**.  
O objetivo é compreender como automatizar a criação de recursos na nuvem e documentar o processo de forma clara e prática.

---

## ☁️ Descrição do Projeto

O projeto consiste na criação de uma **instância EC2** simples utilizando um **template CloudFormation**.  
O template define os recursos necessários para provisionar uma máquina virtual na AWS de forma automática.

---

## 🚀 Passo a Passo da Implementação

1. Acesse o console da **AWS**  
2. Vá até **CloudFormation → Create Stack → With new resources (standard)**  
3. Faça o upload do arquivo `template.yaml`  
4. Clique em **Next** e preencha as informações da stack  
5. Revise as configurações e clique em **Create Stack**  
6. Aguarde o status mudar para **CREATE_COMPLETE**  
7. Vá até o serviço **EC2** e verifique a instância criada  

---

## 💡 Insights e Aprendizados

- O **CloudFormation** automatiza e padroniza o provisionamento de recursos.  
- O formato **YAML** facilita a leitura e manutenção de templates.  
- Pequenas alterações no template podem recriar ou atualizar recursos de forma segura.  
- Documentar o processo ajuda a consolidar o aprendizado.  
- A prática reforça o conceito de **Infrastructure as Code (IaC)**, essencial para automação na nuvem.  

---

## 🧰 Tecnologias Utilizadas

- **AWS CloudFormation**  
- **AWS EC2**  
- **YAML**  
- **GitHub**  

---

## 🏁 Conclusão

Este laboratório foi essencial para compreender a base do **Infrastructure as Code (IaC)** com a **AWS**.  
Através do **CloudFormation**, é possível reproduzir ambientes completos de forma rápida, segura e escalável.

## 📜 Template CloudFormation (Exemplo)

```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: "Criação de uma instância EC2 simples usando AWS CloudFormation"

Resources:
  MyEC2Instance:
    Type: "AWS::EC2::Instance"
    Properties:
      ImageId: ami-0c02fb55956c7d316   # AMI Amazon Linux 2 (substitua conforme sua região)
      InstanceType: t2.micro
      KeyName: my-key-pair             # Nome do seu par de chaves existente
      SecurityGroups:
        - !Ref MySecurityGroup

  MySecurityGroup:
    Type: "AWS::EC2::SecurityGroup"
    Properties:
      GroupDescription: "Permitir SSH e HTTP"
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 22
          ToPort: 22
          CidrIp: 0.0.0.0/0
        - IpProtocol: tcp
          FromPort: 80
          ToPort: 80
          CidrIp: 0.0.0.0/0

