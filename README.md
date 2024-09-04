# SticklandSim

**SticklandSim** é uma ferramenta de simulação baseada em Python, projetada para modelar a produção de ATP e a dinâmica de mutação usando pares de Stickland em vários cenários ambientais e evolutivos. A ferramenta permite que os usuários explorem como diferentes taxas de mutação, pressões seletivas e mudanças ambientais impactam a aptidão da população e a produção de ATP ao longo das gerações.

## Índice

- [Recursos](#recursos)
- [Instalação](#instalação)
  - [Usando pip](#usando-pip)
  - [Usando Conda](#usando-conda)
  - [Usando Docker](#usando-docker)
- [Uso](#uso)
  - [Argumentos da Linha de Comando](#argumentos-da-linha-de-comando)
  - [Arquivos de Configuração](#arquivos-de-configuração)
  - [Exemplos](#exemplos)
- [Cenários de Simulação](#cenários-de-simulação)
  - [Cenários Disponíveis](#cenários-disponíveis)
- [Suporte a Docker](#suporte-a-docker)
- [Contribuindo](#contribuindo)
- [Licença](#licença)

---

## Recursos

- **Simulações Personalizáveis**: Defina taxas de mutação, eficiência de produção de ATP, thresholds de aptidão e mais.
- **Cenários Predefinidos**: Escolha entre diversos cenários pré-configurados ou crie o seu próprio.
- **Ajuste Dinâmico de Parâmetros**: Use machine learning para otimizar parâmetros durante a simulação.
- **Suporte a Checkpoints**: Retome simulações longas a partir de checkpoints salvos.
- **Vários Formatos de Saída**: Gere relatórios em PDF, CSV, XLSX e JSON.
- **Execução Paralela**: Execute múltiplas simulações simultaneamente para grandes conjuntos de dados.

---

## Instalação

Você pode instalar **SticklandSim** via pip, Conda ou usar a imagem Docker fornecida.

### Usando pip

1. Clone o repositório:
   \`\`\`bash
   git clone https://github.com/yourusername/sticklandsim.git
   cd sticklandsim
   \`\`\`

2. Instale os pacotes Python necessários:
   \`\`\`bash
   pip install -r requirements.txt
   \`\`\`

### Usando Conda

1. Crie um ambiente Conda e instale as dependências:
   \`\`\`bash
   conda create --name sticklandsim python=3.10
   conda activate sticklandsim
   conda install --file requirements.txt
   \`\`\`

### Usando Docker

1. Construa a imagem Docker:
   \`\`\`bash
   docker build -t sticklandsim:latest .
   \`\`\`

2. Execute a ferramenta dentro de um contêiner Docker:
   \`\`\`bash
   docker run --rm -v \$(pwd)/configs:/app/configs -v \$(pwd)/results:/app/results sticklandsim:latest --config configs/scenario1.json --output results/output.pdf
   \`\`\`

---

## Uso

Depois de instalado, **SticklandSim** pode ser usado através da linha de comando. Você pode passar arquivos de configuração, selecionar cenários predefinidos e gerar relatórios em diferentes formatos.

### Argumentos da Linha de Comando

\`\`\`bash
python sticklandsim.py --help
\`\`\`

As principais opções são:

- \`--config\`: Caminho para um ou mais arquivos de configuração JSON que definem os cenários de simulação.
- \`--template\`: Escolha entre templates predefinidos, como \`high_mutation\`, \`high_selection\`, etc.
- \`--output\`: Nome base para o relatório de saída (padrão é \`simulation_output\`).
- \`--format\`: Especifique o formato de saída: \`pdf\`, \`csv\`, \`xlsx\`, \`json\`.
- \`--parallel\`: Execute múltiplas simulações em paralelo (se múltiplos cenários forem fornecidos).
- \`--workers\`: Número de trabalhadores paralelos (padrão é o número de CPUs disponíveis).
- \`--checkpoint-interval\`: Número de gerações após as quais um checkpoint será salvo.
- \`--resume-from\`: Caminho para um arquivo de checkpoint para retomar uma simulação anterior.
- \`--ml\`: Ative o ajuste dinâmico de parâmetros usando machine learning.

---

### Arquivos de Configuração

Os arquivos de configuração são arquivos JSON que definem os parâmetros para um cenário de simulação. Abaixo está um exemplo:

\`\`\`json
{
  "scenarios": [
    {
      "name": "Standard Mutation and ATP Production",
      "mutation_rate": 0.05,
      "generations": 100,
      "fitness_threshold": 10,
      "environment_factor": 1.0,
      "stickland_pairs": [
        {
          "amino_acid_pair": "Ala-Leu",
          "efficiency": 1.2,
          "count": 10
        },
        {
          "amino_acid_pair": "Pro-Val",
          "efficiency": 1.5,
          "count": 8
        }
      ],
      "event_schedule": {
        "20": "mutation",
        "50": "selection",
        "75": "environment_change"
      }
    }
  ]
}
\`\`\`

### Exemplos

#### Executando uma Simulação Padrão

\`\`\`bash
python sticklandsim.py --config configs/scenario1_standard_mutation.json --output results/standard_simulation.pdf
\`\`\`

#### Executando uma Simulação de Alta Mutação

\`\`\`bash
python sticklandsim.py --config configs/scenario2_high_mutation.json --output results/high_mutation_output.csv --format csv
\`\`\`

#### Executando uma Simulação com Otimizações de Machine Learning

\`\`\`bash
python sticklandsim.py --config configs/scenario3_high_selection.json --ml --output results/high_selection_optimized.pdf
\`\`\`

---

## Cenários de Simulação

### Cenários Disponíveis

A ferramenta fornece diversos cenários de simulação pré-definidos, cada um com suas características exclusivas.

| Nome do Cenário                          | Nome do Arquivo                              | Resumo                                             |
|------------------------------------------|----------------------------------------------|----------------------------------------------------|
| Standard Mutation and ATP Production     | \`scenario1_standard_mutation.json\`           | Simulação básica com taxa de mutação moderada.      |
| High Mutation Rate Simulation            | \`scenario2_high_mutation.json\`               | Mutações frequentes com adaptação mais rápida.      |
| High Selection Pressure Simulation       | \`scenario3_high_selection.json\`              | Threshold de seleção elevado, simulando alta pressão.|
| Frequent Environmental Changes           | \`scenario4_frequent_environmental_changes.json\`| Mudanças ambientais rápidas ao longo da simulação. |
| Custom Scenario                          | \`scenario5_custom_simulation.json\`           | Cenário personalizável com parâmetros ajustáveis.   |
| Low Mutation Rate Simulation             | \`scenario6_low_mutation.json\`                | Taxa de mutação muito baixa, ritmo evolutivo lento. |
| High Environmental Variability           | \`scenario7_high_environmental_variability.json\`| Alta variação ambiental que afeta a produção de ATP.|
| Extreme Environmental Stress             | \`scenario8_extreme_environmental_stress.json\` | Condições estressantes e desafios de sobrevivência. |
| Adaptive Mutation Rate                   | \`scenario9_adaptive_mutation.json\`           | Taxas de mutação dinâmicas em resposta às mudanças ambientais. |
| Stable Environment with High ATP         | \`scenario10_stable_high_atp.json\`            | Ambiente estável com alta produção de ATP.          |
| Gradual Mutation Increase                | \`scenario11_gradual_mutation_increase.json\`  | Aumento gradual da taxa de mutação ao longo do tempo.|

---

## Suporte a Docker

**SticklandSim** pode ser executado dentro de um contêiner Docker. Isso permite um ambiente consistente, independentemente da configuração da máquina host.

### Construindo a Imagem Docker

\`\`\`bash
docker build -t sticklandsim:latest .
\`\`\`

### Executando uma Simulação com Docker

\`\`\`bash
docker run --rm -v \$(pwd)/configs:/app/configs -v \$(pwd)/results:/app/results sticklandsim:latest --config configs/scenario1_standard_mutation.json --output results/standard_simulation.pdf
\`\`\`

### Build Multi-stage (Otimização)

O Dockerfile usa um processo de build multi-stage para garantir que a imagem final seja o mais leve possível, contendo apenas as dependências necessárias em tempo de execução.

---

## Contribuindo

Contribuições
