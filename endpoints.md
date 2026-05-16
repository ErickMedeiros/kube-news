# Documentação dos Endpoints

## Endpoints da Aplicação

**GET /**
Descrição: Página inicial com lista de todos os posts
Parâmetros: nenhum
Retorno: página HTML renderizada com lista de posts
Códigos HTTP: 200 (sucesso), 500 (erro interno)

**GET /post**
Descrição: Formulário para criação de novo post
Parâmetros: nenhum
Retorno: página HTML com formulário de edição
Códigos HTTP: 200 (sucesso), 500 (erro interno)

**POST /post**
Descrição: Criar novo post via formulário web
Parâmetros:
- title (string, min 30 caracteres)
- resumo (string, min 50 caracteres)
- description (string, min 2000 caracteres)
Retorno: redirect para "/" ou página de erro
Códigos HTTP: 302 (redirect sucesso), 200 (erro validação), 500 (erro interno)

**GET /post/:id**
Descrição: Visualizar post específico
Parâmetros: id (number, parâmetro da URL)
Retorno: página HTML com conteúdo do post
Códigos HTTP: 200 (sucesso), 500 (erro interno)

**POST /api/post**
Descrição: Criar múltiplos posts via API
Parâmetros:
- artigos (array de objetos com title, description, resumo)
Retorno: JSON com array dos artigos criados
Códigos HTTP: 200 (sucesso), 500 (erro interno)

**GET /ready**
Descrição: Health check de disponibilidade (readiness probe)
Parâmetros: nenhum
Retorno: "Ok" ou string vazia
Códigos HTTP: 200 (disponível), 500 (indisponível)

**GET /health**
Descrição: Status da aplicação e informações do sistema
Parâmetros: nenhum
Retorno: JSON com state e hostname da máquina
Códigos HTTP: 200 (sucesso), 500 (erro interno)

**PUT /unhealth**
Descrição: Marcar aplicação como não saudável (para testes)
Parâmetros: nenhum
Retorno: "OK"
Códigos HTTP: 200 (sucesso)

**PUT /unreadyfor/:seconds**
Descrição: Marcar aplicação como indisponível por X segundos
Parâmetros: seconds (number, parâmetro da URL)
Retorno: "OK"
Códigos HTTP: 200 (sucesso)

**GET /metrics**
Descrição: Métricas Prometheus para monitoramento
Parâmetros: nenhum
Retorno: métricas em formato Prometheus
Códigos HTTP: 200 (sucesso), 500 (erro interno)

**GET /static/***
Descrição: Servir arquivos estáticos (CSS, JS, imagens)
Parâmetros: caminho do arquivo na URL
Retorno: arquivo estático solicitado
Códigos HTTP: 200 (sucesso), 404 (não encontrado), 500 (erro interno)