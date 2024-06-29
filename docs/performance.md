# Roadmap das Aulas

Confira o cronograma das aulas e os tópicos que serão abordados:

![Roadmap das Aulas](https://res.cloudinary.com/dyhjjms8y/image/upload/v1717115396/Captura_de_tela_2024-05-31_002953_evnk75.png)

## Aspectos avançados de programação: Vamos falar sobre performance de código?

| Curso | Semana | Pontuação |
|-------|--------|-----------|
| [Padrões de software](https://philos.sophia.com.br/terminal/9418/acervo/detalhe/16553?guid=1701182055297%20e%20returnUrl=%2fterminal%2f9418%2fresultado%2flistar%3fguid%3d1701182055297%26quantidadePaginas%3d1%26codigoRegistro%3d16553%2316553%20e%20i=1) | Semana 08 | 0 |
| [Manipulação de bits: uma técnica essencial para programação de alta performance](https://www.youtube.com/watch?v=Tuok3H5Girw) | Semana 08 | 0 |
| [Fundamentals of garbage collection](https://learn.microsoft.com/en-us/dotnet/standard/garbage-collection/fundamentals) | Semana 08 | 0 |
| [Mapa de memória de um processo](https://www.gta.ufrj.br/~cruz/courses/eel770/slides/9_memoria.pdf) | Semana 08 | 0 |
| [Coletando métricas](https://learn.microsoft.com/pt-br/aspnet/core/log-mon/metrics/metrics?view=aspnetcore-8.0) | Semana 08 | 2 |

### Performance de Código: A Busca pelo Limite

Atingir o máximo de performance em código exige um mergulho profundo nos mecanismos internos da linguagem de programação. Pequenas otimizações podem fazer uma grande diferença, especialmente em operações repetidas milhões de vezes.

#### Exemplo: Par ou Ímpar?

Uma maneira comum de verificar se um número é par ou ímpar é usar o operador módulo (%). No entanto, existe uma alternativa mais rápida: o operador bit a bit AND (&) combinado com o número 1.

```python
def eh_par_modulo(numero):
    return numero % 2 == 0

def eh_par_bitwise(numero):
    return (numero & 1) == 0
```

Em Python, a segunda função (`eh_par_bitwise`) tende a ser mais rápida. Isso porque o operador `& 1` realiza uma operação bit a bit, verificando apenas o último bit do número em sua representação binária. Se o último bit for 0, o número é par; se for 1, é ímpar. Essa operação é mais simples e direta do que o cálculo do módulo.

### Indo Além da Performance

Embora a otimização seja importante, é crucial equilibrar performance com legibilidade e manutenibilidade do código. Em muitos casos, a diferença de velocidade entre duas abordagens pode ser insignificante. Priorize a clareza do código, a menos que o desempenho seja um fator crítico na sua aplicação.

Lembre-se: o conhecimento profundo da linguagem é a chave para desbloquear todo o potencial de performance do seu código!

## Telemetria vs. Logs de Negócio: Entendendo a Diferença

Compreender a distinção entre telemetria e logs de negócio é importante para construir um sistema de monitoramento eficiente e obter insights valiosos sobre o desempenho e o comportamento do seu software.

### Telemetria

A telemetria é a coleta automatizada de dados sobre o desempenho, o uso e a saúde do seu software em tempo real. Ela fornece informações sobre métricas como tempo de resposta, utilização de recursos, taxas de erro e comportamento do usuário.

- Dados quantitativos
- Foco em métricas e indicadores
- Usada para monitoramento e análise de tendências

### Logs de Negócio

Os logs de negócio registram eventos específicos relacionados às atividades do seu software, como transações, logins de usuários, alterações de dados e erros. Eles fornecem um registro detalhado do que aconteceu em um determinado momento.

- Dados qualitativos
- Foco em eventos e ações
- Usados para auditoria, depuração e análise de causa raiz

## InfluxDB: A Base para suas Métricas

O InfluxDB é um banco de dados especializado em séries temporais, ideal para armazenar e analisar dados que mudam ao longo do tempo, como métricas, eventos e logs.

### Por que escolher o InfluxDB?

- Otimizado para séries temporais: Alta performance na escrita e consulta de dados com timestamps.
- Modelo de dados flexível: Permite armazenar dados com tags e campos personalizados.
- Linguagem de consulta poderosa: Flux, uma linguagem de consulta SQL-like para manipular e agregar dados de séries temporais.
- Integração com outras ferramentas: Compatível com Prometheus, Grafana e outras ferramentas do ecossistema de monitoramento.

### Comparativo com MongoDB e Prometheus

| Característica | InfluxDB | MongoDB | Prometheus |
|----------------|----------|---------|------------|
| Tipo de dados  | Séries temporais | Documentos (JSON) | Métricas |
| Modelo de dados | Flexível (tags e campos) | Flexível (sem esquema) | Métricas com rótulos |
| Linguagem de consulta | Flux (SQL-like) | MongoDB Query Language (MQL) | PromQL |
| Armazenamento | Otimizado para séries temporais | Armazenamento geral | Armazenamento em memória |
| Uso principal | Monitoramento, análise de séries temporais | Armazenamento de dados de aplicativos, bancos de dados de propósito geral | Monitoramento, alertas |

## OpenTelemetry, Dynatrace e Prometheus: Observabilidade Aprimorada

Explore as ferramentas que elevam a observabilidade do seu sistema, permitindo monitorar, rastrear e analisar o desempenho de suas aplicações de forma abrangente.

### OpenTelemetry

OpenTelemetry é um conjunto de APIs, SDKs, ferramentas e integrações que permite instrumentar, gerar, coletar e exportar dados de telemetria (traces, métricas e logs) para análise.

- Padrão aberto e independente de fornecedor
- Coleta de dados de telemetria completa
- Integração com diversas ferramentas de observabilidade

### Dynatrace

Dynatrace é uma plataforma de observabilidade completa que oferece monitoramento de aplicações, infraestrutura, experiência do usuário e análise de negócios.

- Monitoramento full-stack
- Detecção automática de problemas
- Análise de causa raiz com inteligência artificial

### Prometheus

Prometheus é um sistema de monitoramento e alerta de código aberto, projetado para coletar métricas de séries temporais.

- Coleta de métricas em tempo real
- Linguagem de consulta poderosa (PromQL)
- Alertas flexíveis

## InfluxDB e Prometheus com Docker: Rápido e Fácil

Inicie rapidamente uma instância do InfluxDB e Prometheus usando o Docker e explore o exemplo de código em Python para enviar métricas:

### Comando Docker

```bash
docker run -d -p 8086:8086 --name my-influxdb influxdb:latest
docker run -d -p 9090:9090 --name prometheus -v C:/Users/Intelii/source/repos/aulatal/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus
```

### Código Python (app.py)

```python
from flask import Flask
from prometheus_client import Gauge, start_http_server
from influxdb_client import InfluxDBClient, Point, WritePrecision
from influxdb_client.client.write_api import SYNCHRONOUS
import random
import time
from dotenv import load_dotenv
import os
from threading import Thread

# Carrega as variáveis de ambiente do arquivo .env
load_dotenv()

app = Flask(__name__)

# Conexão com o InfluxDB (lendo do .env)
influx_url = os.getenv('INFLUXDB_URL')
influx_token = os.getenv('INFLUXDB_TOKEN')
influx_org = os.getenv('INFLUXDB_ORG')
influx_bucket = os.getenv('INFLUXDB_BUCKET')

try:
    client = InfluxDBClient(url=influx_url, token=influx_token, org=influx_org)
    write_api = client.write_api(write_options=SYNCHRONOUS)
except Exception as e:
    print(f"Erro ao conectar ao InfluxDB: {e}")
    exit(1)  # Encerra o aplicativo se não conseguir conectar ao InfluxDB

# Métricas
temperature = Gauge('temperature_celsius', 'Temperature in Celsius')
humidity = Gauge('humidity_percent', 'Humidity in Percentage')
pressure = Gauge('pressure_hpa', 'Pressure in hPa')

@app.route('/')
def index():
    return "Hello, World!"

def generate_metrics():
    while True:
        temp_value = random.uniform(15, 35)
        humidity_value = random.uniform(40, 80)
        pressure_value = random.uniform(980, 1030)

        temperature.set(temp_value)
        humidity.set(humidity_value)
        pressure.set(pressure_value)

        print(f"Metrics updated - Temperature: {temp_value}°C, Humidity: {humidity_value}%, Pressure: {pressure_value}hPa")

        point = Point("metrics").tag("host", "server01").\
            field("temperature", temp_value).\
            field("humidity", humidity_value).\
            field("pressure", pressure_value).\
            time(int(time.time_ns()), WritePrecision.NS)

        try:
            write_api.write(bucket=influx_bucket, org=influx_org, record=point)
            print(f"Metrics sent to InfluxDB - Temperature: {temp_value}°C, Humidity: {humidity_value}%, Pressure: {pressure_value}hPa")
        except Exception as e:
            print(f"Erro ao escrever no InfluxDB: {e}")

        time.sleep(1)

if __name__ == '__main__':
    start_http_server(8000)  # Inicia o servidor de métricas Prometheus na porta 8000
    print("Prometheus metrics server started on port 8000")
    
    metrics_thread = Thread(target=generate_metrics)
    metrics_thread.start()
    app.run(host='0.0.0.0', port=5000)
    print("Flask server started on port 5000")
```

### .env

```plaintext
INFLUXDB_URL=http://localhost:8086
INFLUXDB_TOKEN=
INFLUXDB_ORG=
INFLUXDB_BUCKET=
```

### prometheus.yml

```yaml
global:
  scrape_interval: 15s  # Intervalo de coleta de métricas

scrape_configs:
  - job_name: 'flask_app'
    static_configs:
      - targets: ['host.docker.internal:8000']
```

### requirements.txt

```plaintext
Flask
prometheus_client
influxdb-client
python-dotenv
```

## Aplicando a Aprendizagem Baseada em Times (TBL) com Autoestudo Ponderado

Agora é hora de colocar em prática o que você aprendeu sobre métricas, logs e observabilidade! Nesta atividade TBL, você trabalhará em equipes mistas para aplicar o autoestudo "Como extrair boas métricas da sua aplicação" em um projeto prático.

### Desafio TBL:

Seu time deverá aplicar ao seu projeto. Utilizando os conceitos de métricas, logs e as ferramentas apresentadas (InfluxDB, Prometheus, Grafana, OpenTelemetry), vocês deverão:

1. Coletar métricas relevantes da aplicação.
2. Implementar o Prometheus para coletar e armazenar as métricas.
3. Configurar o Grafana para visualizar as métricas em dashboards.
4. Documentar todo o processo em um arquivo README.md, incluindo:
    - Passo a passo detalhado da implementação.
    - Prints das métricas coletadas e dos dashboards do Grafana.
    - Explicações claras e objetivas sobre as decisões tomadas.
    - Uso de commits semânticos para facilitar o acompanhamento do desenvolvimento.

### Instruções Completas do Desafio TBL

**Descrição:**

Como extrair boas métricas da sua aplicação

**Conteúdos Relacionados:**

Coletando Métricas

**Pergunta:**

Crie um repositório para armazenar os códigos gerados no autoestudo. Siga o passo a passo, implementando a coleta de métricas, implementação do Prometheus e Grafana.

Documente o passo a passo em arquivo readme de forma que possa ser reproduzido posteriormente. Utilize prints e texto de forma clara, objetiva e coesa.

Crie uma seção demonstrando os gráficos em funcionamento.

**Barema:**

- Codificação de todas as etapas - 3 pontos
- Código e Testes compilando e executando sem erros - 2 pontos
- Métricas coletadas e evidenciadas no relatório - 2 pontos
- Commit semântico e Organização do relatório - 1 ponto
- Relatório em markdown escrito de forma clara, concisa e objetiva - 2 pontos

## Autoestudo Ponderado

![Guia de Autoestudo Ponderado](https://res.cloudinary.com/dyhjjms8y/image/upload/v1717121132/Captura_de_tela_2024-05-31_020525_uqy7l0.png)

## Sua Opinião é Importante!

Deixe seu feedback com estrelas e comentários e ajude-nos a melhorar o Inteli e o curso de ES.