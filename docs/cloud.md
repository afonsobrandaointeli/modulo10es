# Roadmap das Aulas

Confira o cronograma das aulas e os tópicos que serão abordados:

![Roadmap das Aulas](https://res.cloudinary.com/dyhjjms8y/image/upload/v1717115396/Captura_de_tela_2024-05-31_002953_evnk75.png)

## Como dialogar com o seu ambiente cloud?

| Curso | Semana | Pontuação |
|-------|--------|-----------|
| [O que é o Terraform?](https://www.ibm.com/br-pt/topics/terraform) | Semana 09 | 0 |
| [Terraform em 10 Minutos](https://www.youtube.com/watch?v=0EAjJe8aPkc) | Semana 09 | 0 |
| [Build infrastructure](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/aws-build) | Semana 09 | 2 |
| [What is Infrastructure as Code with Terraform?](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/infrastructure-as-code) | Semana 09 | 0 |
| [Install Terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli) | Semana 09 | 0 |

### Documentação e Instalação

[Documentação Terraform/AWS](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/aws-build)  
[Instalação Terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

## Passo a Passo para Criar uma Instância EC2 com Terraform

### Requisitos Pré-requisitos

Antes de iniciar, certifique-se de que você tem uma conta na [AWS Academy](https://awsacademy.instructure.com/).  
Além disso, você pode encontrar um repositório de exemplo para Terraform em: [Repositório de Exemplo Terraform](https://github.com/afonsobrandaointeli/terraform-demo).

### Instalando o Terraform CLI

Siga os passos abaixo para instalar o Terraform CLI no Windows usando PowerShell:

1. Abra o PowerShell como Administrador.
2. Baixe o Terraform executando o comando:
    ```powershell
    Invoke-WebRequest -Uri https://releases.hashicorp.com/terraform/1.0.11/terraform_1.0.11_windows_amd64.zip -OutFile terraform.zip
    ```
3. Extraia o arquivo ZIP:
    ```powershell
    Expand-Archive -Path terraform.zip -DestinationPath C:\terraform
    ```
4. Adicione o Terraform ao PATH do sistema:
    ```powershell
    [System.Environment]::SetEnvironmentVariable('PATH', $env:PATH + ';C:\terraform', [System.EnvironmentVariableTarget]::Machine)
    ```
5. Verifique a instalação executando:
    ```powershell
    terraform -v
    ```

### Instalando o AWS CLI

Siga os passos abaixo para instalar o AWS CLI no Windows usando PowerShell:

1. Abra o PowerShell como Administrador.
2. Baixe o instalador do AWS CLI executando:
    ```powershell
    Invoke-WebRequest -Uri https://awscli.amazonaws.com/AWSCLIV2.msi -OutFile AWSCLIV2.msi
    ```
3. Instale o AWS CLI executando:
    ```powershell
    Start-Process msiexec.exe -Wait -ArgumentList '/I AWSCLIV2.msi /quiet'
    ```
4. Verifique a instalação executando:
    ```powershell
    aws --version
    ```

### Configurando as Credenciais da AWS

Configure suas credenciais da AWS executando o comando:
```powershell
aws configure
```
Forneça suas credenciais de acesso (AWS Access Key ID, AWS Secret Access Key, região padrão e formato de saída).

Em seguida, configure o AWS Access Token diretamente no arquivo de credenciais:

1. Abra o PowerShell e navegue até o diretório de configuração da AWS:
    ```powershell
    cd ~\.aws\
    ```
2. Abra o arquivo `credentials` em um editor de texto:
    ```powershell
    notepad credentials
    ```
3. Adicione ou edite a seção com o seguinte conteúdo:
    ```plaintext
    [default]
    aws_access_key_id = YOUR_ACCESS_KEY_ID
    aws_secret_access_key = YOUR_SECRET_ACCESS_KEY
    aws_session_token = YOUR_SESSION_TOKEN
    ```

### Criando uma Instância EC2 com Terraform

Crie um arquivo de configuração Terraform chamado `main.tf` com o seguinte conteúdo:
```hcl
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

#### Inicializando o Terraform

Abra o PowerShell no diretório onde está o arquivo `main.tf` e execute:
```powershell
terraform init
```

#### Planejando a Infraestrutura

Para ver o que será criado, execute:
```powershell
terraform plan
```

#### Aplicando a Configuração

Para criar a instância EC2, execute:
```powershell
terraform apply
```
Digite `yes` quando solicitado para confirmar a aplicação da configuração.

#### Resolvendo Erros de AMI

Se você encontrar o erro `InvalidAMIID.NotFound`, significa que o ID da AMI não é válido para a região especificada. Para encontrar uma AMI válida, você pode usar o comando AWS CLI:
```powershell
aws ec2 describe-images --owners amazon --filters "Name=name,Values=amzn2-ami-hvm-2.0.????????-x86_64-gp2"
```
Isso retornará uma lista de AMIs válidas que você pode usar. Substitua o ID da AMI em seu arquivo `main.tf` por uma das AMIs listadas.

#### Limpando a Infraestrutura

Para destruir a instância criada, execute:
```powershell
terraform destroy
```
Digite `yes` quando solicitado para confirmar a destruição da infraestrutura.

## Infraestrutura como Código e Projetos

### O que é infraestrutura como código

Que problemas você encontrou ao criar recursos na nuvem até agora? ❓  
Uma solução é Infraestrutura como Código 💡  
Infraestrutura como código (IaC) é a prática de definir os recursos de nuvem que você precisa em código e, em seguida, permitir que eles sejam criados por meio dessas ferramentas em vez de manualmente pelo provedor de nuvem.

#### Exemplo

Por exemplo, em vez de criar uma máquina virtual diretamente, descrevemos a máquina virtual em código e depois permitimos que nossa ferramenta, no nosso caso Terraform, a crie para nós!  
❗️ Isso parece trabalho adicional 😅

#### Benefícios 🟢

- Escalabilidade: Com infraestrutura como código, as equipes podem provisionar e desprovisionar rapidamente recursos de infraestrutura para atender às necessidades do negócio.
- Consistência: Como a infraestrutura é definida em código, as equipes têm mais confiança de que o ambiente será consistente em todas as implantações.
- Gerenciamento de mudanças: Quando alterações são feitas no código de infraestrutura, fica mais fácil rastrear e gerenciar essas mudanças ao longo do tempo.
- Colaboração: A infraestrutura como código incentiva a colaboração e o controle de versão para garantir o mesmo ambiente em todas as equipes.

#### Desvantagens ❌

- Complexidade: Com infraestrutura como código, você acaba com uma grande base de código que pode ser difícil de gerenciar.
- Tempo: Escrever infraestrutura como código leva muito tempo inicialmente, então para projetos pequenos pode ser mais eficiente não utilizá-lo!
- Bloqueio: A maioria da infraestrutura como código é específica para o provedor de nuvem, se você quiser mudar de provedor, também precisará migrar todo o seu IaC!

#### Vamos ver na prática 🛠!

### Terraform

Terraform é uma ferramenta IaC de código aberto desenvolvida pela HashiCorp. O Terraform é diferente de outras ferramentas IaC porque se concentra na construção de uma representação estática da infraestrutura desejada e, em seguida, atualiza incrementalmente a infraestrutura com base nas mudanças de configuração.

#### Principais benefícios do Terraform:

- Sintaxe declarativa: Com o Terraform, você descreve o estado desejado de sua infraestrutura em uma sintaxe declarativa, o que facilita o entendimento e o raciocínio.
- Suporte multi-cloud: O Terraform suporta vários provedores de nuvem, permitindo que você use uma única ferramenta para gerenciar infraestrutura em diferentes plataformas.
- Dependências de recursos: O Terraform determina automaticamente a ordem das operações necessárias para criar recursos de infraestrutura com dependências de outros recursos (muito importante para configurações complexas).
- Gerenciamento de estado: Através do uso de arquivos de estado, o Terraform rastreia mudanças na infraestrutura e ajuda a prevenir a divergência de configuração (crítico para trabalho em equipe).

## Autoestudo: Construindo Infraestrutura

**Atividade ponderada:** 2 pontos  
**Atividade obrigatória**

### Descrição

Assista ao vídeo no link fornecido e siga o passo a passo do tutorial para criar seu ambiente utilizando o Terraform como IaC (Infraestrutura como Código).

[Tutorial](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/aws-build)

### Conteúdos Relacionados

- Construção de Infraestrutura

### Pergunta

1. **Execute o passo a passo do tutorial:** Utilize o Terraform para criar seu ambiente como IaC.
2. **Crie um repositório no GitHub:** Armazene o código no repositório.
3. **Documente no README:** No arquivo README, descreva o passo a passo executado, incluindo imagens e descrições breves e objetivas sobre cada etapa e seu propósito.
4. **Adicione prints:** Ao executar os comandos do Terraform, inclua prints dos resultados obtidos.
5. **Documente os itens provisionados:** Crie uma seção para documentar os itens provisionados na nuvem pelo Terraform, utilizando prints como evidência.
6. **Mantenha a qualidade:** Certifique-se de que o trabalho seja coerente, objetivo, organizado e bem apresentado.

### Barema

- (De 0 a 3): Completude do passo a passo do autoestudo.
- (De 0 a 2): Organização do arquivo README e dos códigos no repositório.
- (De 0 a 2): Corretude e coesão das informações descritas no arquivo README.
- (De 0 a 3): Evidências do funcionamento na nuvem da criação do ambiente.

## Tutoriais Terraform

| Tutoriais Terraform |
|---------------------|
| [Terradocs](https://brun0meira.github.io/terradocs/) |
| [Ponderada Semana 9 M10 - Abner](https://abnersilvabarbosa.github.io/Ponderada-semama-9-M10/) |
| [Ponderada Terraform - Felipe Santos](https://felipesantosinteli.github.io/ponderada-terraform/) |
| [Entregas de Prog - Stefano](https://naoassisto.github.io/Entregas-de-prog/) |
| [Terraform Tutorial - Pingu =)](https://pingu01.github.io/terraform-tutorial/) |

## Sua Opinião é Importante!

Deixe seu feedback com estrelas e comentários e ajude-nos a melhorar o Inteli e o curso.
