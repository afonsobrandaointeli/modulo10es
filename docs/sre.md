# Roadmap das Aulas

Confira o cronograma das aulas e os tópicos que serão abordados:

![Roadmap das Aulas](https://res.cloudinary.com/dyhjjms8y/image/upload/v1717115396/Captura_de_tela_2024-05-31_002953_evnk75.png)

## SRE: Você está fazendo isso errado!

| Curso | Semana | Pontuação |
|-------|--------|-----------|
| [Princípios e práticas fundamentais da SRE: ciclos virtuosos](https://learn.microsoft.com/pt-br/training/modules/intro-to-site-reliability-engineering/4-key-principles-1-virtuous-cycles) | Semana 09 | 0 |
| [Princípios e práticas fundamentais da SRE: O lado humano da SRE](https://learn.microsoft.com/pt-br/training/modules/intro-to-site-reliability-engineering/5-key-principles-2-human-side-of-sre) | Semana 09 | 0 |
| [SRE na prática. Como as empresas tem usado essa disciplina na prática?](https://learn.microsoft.com/pt-br/training/modules/intro-to-site-reliability-engineering/6-getting-started) | Semana 09 | 0 |
| [Site Reliability Engineer (SRE)](https://cloudcasters.io/pt-br/site-reliability-engineer-sre/) | Semana 09 | 0 |

### Repositório GitHub

[Repositório GitHub - Django com Render](https://github.com/render-examples/django)

## Vamos ver se vocês estão fazendo Autoestudos!

Prepare-se para o quiz!

[Jogar Kahoot!](https://kahoot.it/)

## SRE (Site Reliability Engineering)

Explorando a Engenharia de Confiabilidade de Sites

### Principais Conceitos

- **Automatização:** Eliminação de trabalho manual repetitivo para aumentar a eficiência e reduzir erros.
- **Monitoramento e Observabilidade:** Coleta de dados e métricas para entender o comportamento do sistema e identificar problemas.
- **Gerenciamento de Incidentes:** Processos para responder e resolver incidentes de forma rápida e eficaz.
- **Engenharia de Capacidade:** Garantia de que o sistema tenha recursos suficientes para atender à demanda.
- **Gerenciamento de Mudanças:** Implementação de mudanças de forma controlada para minimizar o risco de interrupções.

### Benefícios

- Maior confiabilidade e disponibilidade do sistema.
- Redução do tempo de inatividade e interrupções.
- Melhora da escalabilidade e desempenho do sistema.
- Maior eficiência operacional e redução de custos.
- Melhora da colaboração entre equipes de desenvolvimento e operações.

## Tecnologias Essenciais para SRE

Ferramentas que capacitam a Engenharia de Confiabilidade de Sites

### Kubernetes

Plataforma open source para automatizar a implantação, o dimensionamento e o gerenciamento de aplicativos em contêineres.

[Saiba mais](https://kubernetes.io/)

### Rancher

Plataforma completa de gerenciamento de Kubernetes que facilita a operação de clusters em qualquer lugar.

[Saiba mais](https://www.rancher.com/)

### Terraform

Ferramenta de código aberto para provisionar e gerenciar infraestrutura em nuvem de forma segura e eficiente.

[Saiba mais](https://www.terraform.io/)

### Ansible

Ferramenta de automação de TI que simplifica tarefas como provisionamento em nuvem, gerenciamento de configuração e implantação de aplicativos.

[Saiba mais](https://www.ansible.com/)

## Tutorial de Instalação e Configuração do Minikube no Windows

### Passo 1: Instalar Dependências

Primeiro, instale o Docker para Windows. Baixe e instale o Docker Desktop no site oficial:

[Baixar Docker Desktop](https://www.docker.com/products/docker-desktop)

Após a instalação, inicie o Docker Desktop e certifique-se de que está rodando.

### Passo 2: Instalar o Minikube

Baixe e instale o Minikube:
```powershell
Invoke-WebRequest -Uri "https://storage.googleapis.com/minikube/releases/latest/minikube-installer.exe" -OutFile "minikube-installer.exe"
Start-Process -FilePath ".\minikube-installer.exe" -Wait
```

### Passo 3: Iniciar o Minikube

Inicie o Minikube:
```powershell
minikube start --driver=docker
```

### Passo 4: Instalar o Kubectl

Baixe e instale o Kubectl:
```powershell
Invoke-WebRequest -Uri "https://dl.k8s.io/release/v1.23.0/bin/windows/amd64/kubectl.exe" -OutFile "kubectl.exe"
$env:Path += ";$pwd"
kubectl version --client
```

### Passo 5: Criar Aplicação Flask

Crie uma aplicação Flask simples. Crie um diretório para o projeto e um arquivo `app.py`:
```powershell
mkdir flask-app
cd flask-app
New-Item -Path . -Name "app.py" -ItemType "file"
```
Adicione o seguinte conteúdo ao `app.py`:
```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return "Hello, World!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```
Crie um arquivo `requirements.txt`:
```powershell
New-Item -Path . -Name "requirements.txt" -ItemType "file"
```
Adicione o seguinte conteúdo:
```plaintext
Flask==2.1.1
```

### Passo 6: Criar Dockerfile

Crie um arquivo `Dockerfile` com o seguinte conteúdo:
```powershell
New-Item -Path . -Name "Dockerfile" -ItemType "file"
Set-Content -Path "Dockerfile" -Value @"
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt

COPY . .

CMD ["python", "app.py"]
"@
```

### Passo 7: Construir e Enviar a Imagem Docker

Construa a imagem Docker:
```powershell
minikube -p minikube docker-env | Invoke-Expression
docker build -t flask-app:latest .
```

### Passo 8: Criar Manifests do Kubernetes

Crie um arquivo `deployment.yaml`:
```powershell
New-Item -Path . -Name "deployment.yaml" -ItemType "file"
```
Adicione o seguinte conteúdo:
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: flask-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: flask-app
  template:
    metadata:
      labels:
        app: flask-app
    spec:
      containers:
      - name: flask-app
        image: flask-app:latest
        imagePullPolicy: Never
        ports:
        - containerPort: 5000
```
Crie um arquivo `service.yaml`:
```powershell
New-Item -Path . -Name "service.yaml" -ItemType "file"
```
Adicione o seguinte conteúdo:
```yaml
apiVersion: v1
kind: Service
metadata:
  name: flask-app
spec:
  type: NodePort
  selector:
    app: flask-app
  ports:
  - protocol: TCP
    port: 5000
    targetPort: 5000
    nodePort: 30007
```

### Passo 9: Aplicar Manifests do Kubernetes

Aplique os arquivos de configuração:
```powershell
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

### Passo 10: Verificar os Pods e Serviço

Verifique os pods:
```powershell
kubectl get pods
```
Verifique o serviço:
```powershell
kubectl get svc
```

### Passo 11: Obter URL de Acesso

Obtenha a URL de acesso:
```powershell
minikube service flask-app --url
```
Abra a URL no navegador para ver a aplicação Flask em execução.

### Passo 12: Ver o Minikube Dashboard

Inicie o Minikube dashboard:
```powershell
minikube dashboard
```
Acesse a URL fornecida para visualizar o dashboard.

## Como se Tornar um Excelente SRE

### Introdução ao SRE

Um Site Reliability Engineer (SRE) é responsável por garantir a confiabilidade e disponibilidade dos sistemas em produção. Aqui estão os passos essenciais para se tornar um excelente SRE.

### 1. Compreender os Fundamentos

É crucial ter uma forte compreensão dos fundamentos de computação e redes, incluindo sistemas operacionais, redes, protocolos de comunicação e arquitetura de sistemas distribuídos.

- Estude conceitos de sistemas operacionais como processos, threads, gerenciamento de memória e sistemas de arquivos.
- Aprenda sobre redes, incluindo TCP/IP, DNS, HTTP/HTTPS e firewalls.

### 2. Aprender Programação e Automação

A automação é uma parte vital do SRE. Familiarize-se com linguagens de programação como Python, Go, ou Ruby, e ferramentas de automação como Ansible, Puppet, e Chef.

- Desenvolva scripts para automatizar tarefas repetitivas.
- Crie e gerencie pipelines de CI/CD.

### 3. Conhecer Ferramentas de Monitoramento e Logging

Um SRE deve ser proficiente em monitoramento e logging para detectar e solucionar problemas rapidamente.

- Aprenda a usar ferramentas como Prometheus, Grafana, ELK Stack (Elasticsearch, Logstash, Kibana), e Splunk.
- Configure alertas para monitorar a saúde dos sistemas.

### 4. Dominar Cloud e Contêineres

O conhecimento em tecnologias de cloud e contêineres é essencial.

- Estude serviços de cloud como AWS, Google Cloud, e Azure.
- Aprenda a usar contêineres com Docker e orquestração de contêineres com Kubernetes.

### 5. Praticar Resolução de Problemas e Resiliência

Desenvolva habilidades de resolução de problemas e melhore a resiliência dos sistemas.

- Realize exercícios de Chaos Engineering para testar a resiliência dos sistemas.
- Participe de simulações de incidentes para praticar a resposta a incidentes.

### 6. Focar na Cultura e Comunicação

Um excelente SRE deve promover uma cultura de colaboração e comunicação eficaz.

- Trabalhe em estreita colaboração com equipes de desenvolvimento e operações.
- Participe de revisões pós-incidente (Postmortems) para identificar áreas de melhoria.

### Recursos Adicionais

Para aprofundar seus conhecimentos em DevOps e Segurança da Informação, explore os seguintes recursos:

[Trilha de DevOps](https://roadmap.sh/devops)  
[Trilha de Segurança da Informação](https://www.freecodecamp.org/learn/information-security/)

### Conclusão

Tornar-se um excelente SRE requer uma combinação de habilidades técnicas e soft skills. Continuar aprendendo e se adaptando às novas tecnologias e práticas é essencial para o sucesso nesta carreira.

## Sua Opinião é Importante!

Deixe seu feedback com estrelas e comentários e ajude-nos a melhorar o Inteli e o curso.