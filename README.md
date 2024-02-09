Passo 1: Preparação dos Dados
Antes de começarmos, é essencial preparar os dados que serão usados para treinar e testar o modelo. Para este exemplo, utilizaremos um conjunto de dados de alugueis de bicicletas.

Passo 2: Configuração do Azure Machine Learning
Acesse o portal do Azure (https://portal.azure.com/) e crie um novo recurso de Machine Learning.

Dentro do recurso, crie um novo workspace do Azure Machine Learning.

Grupo de recursos : Crie ou selecione um grupo de recursos.
Nome : Insira um nome exclusivo para seu espaço de trabalho.
Região : Selecione a região geográfica mais próxima.
Registro de contêiner : Nenhum
Selecione + criar e Criar . A criação pode demorar alguns minutos, em seguida vá para o recurso implantado.
Passo 3: Treinamento do Modelo
Escolha um algoritmo de machine learning adequado para o seu problema. Neste exemplo, utilizaremos um modelo de regressão linear.
No Azure Machine Learning Studio, crie um novo experimento e selecione o algoritmo de regressão linear.
Configure o experimento para usar os conjuntos de dados de treinamento e teste carregados anteriormente.
Defina métricas de avaliação, como o coeficiente de determinação (R²), para acompanhar o desempenho do modelo durante o treinamento.
Execute o experimento e ajuste os hiperparâmetros conforme necessário para melhorar o desempenho do modelo.
##Exemplo de configuração feita para este caso: Configurações básicas: Nome do trabalho : mslearn-bike-automl (nome aleatório criado pelo sistema) Novo nome do experimento : mslearn-bike-rental Descrição : Aprendizado de máquina automatizado para previsão de aluguel de bicicletas Marcadores : nenhum

Tipo de tarefa e dados:Selecione o tipo de tarefa : Regressão

Selecionar conjunto de dados : crie um novo conjunto de dados com as seguintes configurações:

Tipo de dados: Nome : aluguel de bicicletas Descrição : dados históricos de aluguel de bicicletas Tipo : Tabular

Fonte de dados: Selecione Dos arquivos da web

URL da Web: URL da Web :https://aka.ms/bike-rentals Ignorar validação de dados : não selecionar

Configurações: Formato de arquivo : Delimitado Delimitador : Vírgula Codificação : UTF-8 Cabeçalhos de coluna : apenas o primeiro arquivo possui cabeçalhos Pular linhas : Nenhum O conjunto de dados contém dados multilinhas : não selecione

Esquema: Incluir todas as colunas exceto Caminho

Selecione Criar . Após a criação do conjunto de dados, selecione o conjunto de dados de aluguel de bicicletas para continuar a enviar o trabalho de ML automatizado.

Configurações de tarefa: Tipo de tarefa : Regressão Conjunto de dados : aluguel de bicicletas Coluna de destino : Aluguéis (inteiro)

Configurações adicionais: Métrica primária : raiz do erro quadrático médio normalizado Explique o melhor modelo : Não selecionado Usar todos os modelos suportados : Desmarcado. Modelos permitidos : Selecione apenas RandomForest e LightGBM

Limites: Máximo de testes : 3 Máximo de testes simultâneos : 3 Máximo de nós : 3 Limite de pontuação da métrica : 0.085 Tempo limite : 15 Tempo limite de iteração : 15 Habilitar rescisão antecipada : selecionado

Validação e teste: Tipo de validação : divisão de validação de treinamento Porcentagem de dados de validação : 10 Conjunto de dados de teste : Nenhum

Calcular: Selecione o tipo de computação : sem servidor Tipo de máquina virtual : CPU Camada de máquina virtual : Dedicada Tamanho da máquina virtual : Standard_DS3_V2* Número de instâncias : 1

Passo 4: Implantação do Modelo
Após treinar um modelo satisfatório, registre-o no Azure Machine Learning Studio.
Crie um serviço de implantação para o modelo registrado, especificando o tipo de serviço (por exemplo, ACI - Azure Container Instances).
Configure pontos de extremidade (endpoints) para permitir que seus aplicativos façam previsões usando o modelo implantado.
