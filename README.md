# Configuração do Terraform com AWS

Este guia detalhado ensina como usar o Terraform para gerenciar recursos na AWS. 

## Pré-requisitos

Antes de iniciar, certifique-se de que você possui o seguinte:

- Conta na AWS Academy: [AWS Academy](https://aws.amazon.com/academy/)
- Terraform CLI instalado
- AWS CLI instalado

## Instalação do Terraform CLI

Para instalar o Terraform no Windows usando PowerShell, siga estes passos:

1. **Abrir PowerShell como Administrador:**
   - Clique com o botão direito no menu Iniciar e selecione 'Windows PowerShell (Admin)'.
    <img src = "./assets/img1">

2. **Baixar o Terraform:**
   ```powershell
   Invoke-WebRequest -Uri https://releases.hashicorp.com/terraform/1.0.11/terraform_1.0.11_windows_amd64.zip -OutFile terraform.zip
   ```
     <img src = "./assets/img2">


3. **Extraia o arquivo ZIP:**
   ```powershell
    Expand-Archive -Path terraform.zip -DestinationPath C:\terraform
   ```
    <img src = "./assets/img3">

4. **Adicione o Terraform ao PATH do sistema:**
   ```powershell
    [System.Environment]::SetEnvironmentVariable('PATH', $env:PATH + ';C:\terraform', [System.EnvironmentVariableTarget]::Machine)
   ```
    <img src = "./assets/img4">

5. **Verifique se foi instalado:**
   ```powershell
    terraform -v
   ```


## Instalação do AWS CLI

1. **Baixar o instalador do AWS CLI:**
   ```powershell
    Invoke-WebRequest -Uri https://awscli.amazonaws.com/AWSCLIV2.msi -OutFile AWSCLIV2.msi
   ```

2. **Instalar o AWS CLI:**
   ```powershell
    Start-Process msiexec.exe -Wait -ArgumentList '/I AWSCLIV2.msi /quiet'
   ```

3. **Verificar a instalação:**
   ```powershell
    aws --version
   ```

## Configuração das credenciais do AWS

1. Abra o AWS Academy e inicie um módulo:
    - Escolha um curso que você esteja inscito:
    <img src ="./assets/img6">

    - Vá na aba Módulos e depois acesse o Laboratório de aprendizagem da AWS Academy:
    <img src ="./assets/img7">

    - Inicie o lab:
    <img src ="./assets/img8">

2. Para configurar as credenciais va no PowerShell e digite 
   ```powershell
    cd ~\.aws\
   ```


3. Abra o arquivo credentials no notepad pelo comando:
    ```powershell
    notepad credentials
   ```

4. Vá até o AWS Academy e pegue suas credenciais :

    <img src ="./assets/img9">

5. Cole elas no notepad que você abriu

## Criando uma Instância EC2 com Terraform:
    
1. Crie um arquivo de configuração Terraform chamado main.tf com o seguinte conteúdo:
    ```
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c02fb55956c7d316"  # Amazon Linux 2 AMI (HVM), SSD Volume Type
  instance_type = "t2.micro"

  tags = {
    Name = "TerraformExample"
  }
}   
```

## Criando a instância: 

1. Abra o terminal e execute o comando:
```
terraform init

```

2.Para ver o que será criado, execute:
```
terraform plan
```

3. Para criar a instância EC2, execute:

```
terraform apply

``` 

Digite **yes** quando solicitado para confirmar a aplicação da configuração.

4. Limpe a infraestrutura com:
```
terraform destroy
```

### Passo a passo com prints:

    <img src ="./assets/img11">
    <img src ="./assets/img12">
    <img src ="./assets/img13">
    <img src ="./assets/img14">
    <img src ="./assets/img15">
    <img src ="./assets/img16">
    <img src ="./assets/img17">
    <img src ="./assets/img18">
    <img src ="./assets/img19">
    <img src ="./assets/img20">
    <img src ="./assets/img21">
    <img src ="./assets/img22">

    -No final é possivel ver a instancia criada no AWS:
    <img src ="./assets/img23">




