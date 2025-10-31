# Sobre o GuiMA - Guia de Museus Acessíveis do Brasil

GuiMA é um trabalho de conclusão de curso (TCC) para o MBA de Jornalismo de Dados do IDP, realizado em 2025, que busca reunir e apresentar as informações de acessibilidade dos museus existentes no Brasil.

Foi desenvolvido por [Ícaro Ferracini](https://www.linkedin.com/in/icaroferracini/), com orientação da professora [Deborah Foroni](https://www.linkedin.com/in/deborah-foroni/), e pode ser [acessado nesse link](https://icaroferracini.github.io/Guia-de-Museus-Acessiveis/03%20-%20Visualizacao/index.html).

## Descrição resumida do tema de investigação

As barreiras para pessoas com deficiência visitarem um museu iniciam ainda na fase de planejamento, pois encontrar informações claras sobre acessibilidade de um local pode ser impossível.

Essa indisponibilidade, além de excluir parte do público, impede que milhões de brasileiros exerçam plenamente seu direito à cultura. Este projeto busca transformar esse cenário, oferecendo dados claros e acessíveis sobre a infraestrutura de acessibilidade dos museus brasileiros.

## Justificativa

No Brasil, [18,6 milhões de pessoas vivem com algum tipo de deficiência](https://www.gov.br/mdh/pt-br/assuntos/noticias/2023/julho/brasil-tem-18-6-milhoes-de-pessoas-com-deficiencia-indica-pesquisa-divulgada-pelo-ibge-e-mdhc) – quase 9% da população ([IBGE, 2023](https://agenciadenoticias.ibge.gov.br/agencia-noticias/2012-agencia-de-noticias/noticias/37317-pessoas-com-deficiencia-tem-menor-acesso-a-educacao-ao-trabalho-e-a-renda)).

Apesar da Lei Brasileira de Inclusão da Pessoa com Deficiência ([Lei nº 13.146/2015, art. 42](https://www2.camara.leg.br/legin/fed/lei/2015/lei-13146-6-julho-2015-781174-normaatualizada-pl.html)) garantir o direito de acesso à cultura, dos 4.005 museus registrados oficialmente no portal [MuseusBR](http://museus.cultura.gov.br/), segundo um levantamento realizado em janeiro de 2025, apenas 37,7% indicavam possuir recursos ou infraestrutura para acessibilidade.

Nesse cenário, o projeto **GuiMA (Guia de Museus Acessíveis)** se propõe a ampliar essa discussão com uma melhor exposição das informações de acessibilidade nos Museus, ampliando o trabalho já existente do [Instituto Brasileiro de Museus - Ibram](https://www.gov.br/museus/pt-br/assuntos/os-museus/museus-do-brasil/museus-do-brasil) no acesso à informação, tornando mais fácil ao público a consulta das instituições e trazendo uma nova perspectiva aos dados disponíveis, fortalecendo a transparência de informações e criando novas oportunidades de diálogo sobre o tema.

---

# Metodologia

## Fonte de dados

Todos os dados exibidos neste projeto são do site [MuseusBR](http://museus.cultura.gov.br/). Segundo o Instituto Brasileiro de Museus - Ibram:

> "A fonte mais atualizada para conhecer os museus brasileiros é a plataforma [MuseusBR](http://museus.cultura.gov.br/). Criado pela [Portaria Ibram nº 215, de 4 de março de 2021](https://www.gov.br/museus/pt-br/assuntos/legislacao-e-normas/portarias/portaria-ibram-no-215-de-4-de-marco-de-2021), [MuseusBR](http://museus.cultura.gov.br/) é o sistema nacional de identificação de museus e plataforma para mapeamento colaborativo, gestão e compartilhamento de informações sobre os museus brasileiros."

> "A plataforma tem como princípios a utilização de software livre, a colaboração, a descentralização, o uso de dados abertos e a transparência."

As informações foram obtidas de duas formas: pela **base disponibilizada oficialmente no site** e por meio de **raspagem de dados**, coletando informações na própria plataforma do [MuseusBR](http://museus.cultura.gov.br/).

É importante ressaltar que os dados são autodeclarados pelos museus na plataforma e que não foi possível realizar verificação sobre os recursos de acessibilidade informados pelas instituições. A última coleta de dados foi realizada em outubro de 2025, e as informações podem ter sido atualizadas pelos museus posteriormente.

### Bibliotecas Python utilizadas

Para a raspagem, análise e tratamento das informações, foram utilizadas bibliotecas como:

- **Pandas**: Manipulação de dados (tabelas, planilhas, CSV etc.)
- **Requests**: Faz requisições HTTP (acessar sites, APIs etc.)
- **BeautifulSoup**: Extrai dados de páginas HTML (web scraping)
- **TQDM**: Mostrar barras de progresso nos loops
- **Numpy**: Análise, cálculo numérico e operações com arrays
- **Matplotlib**: Visualização de dados
- **Geopy**: Uso do **Nominatim** para obter as coordenadas de localização com base em um endereço

## Obtenção dos dados: Base de dados oficial do MuseusBR e raspagem de dados

O próprio site [MuseusBR](http://museus.cultura.gov.br/) disponibiliza em seu painel analítico uma planilha com os dados completos, disponível nesse link: https://encurtador.com.br/cnxNR.

Essa planilha foi utilizada como base das informações para a raspagem de dados, com objetivo de complementar as informações fornecidas pela planilha.

A raspagem de dados foi realizada utilizando a linguagem Python no mês de outubro de 2025, acessando as páginas públicas do [MuseusBR](http://museus.cultura.gov.br/) de acordo com o link que estava registrado na planilha disponibilizada pela instituição. Foram acessadas 4.047 páginas individuais de museus, obtendo as informações apresentadas em cada uma das páginas, como:

1. Gestão
2. Contrato de Gestão
3. Caracterização
4. Acervo
5. Público, Acessibilidade e Serviços
6. Biblioteca e Arquivo Histórico
7. Atividades Educativas e Culturais
8. Endereço de visitação
9. Tratamento dos dados

Com posse da planilha disponibilizada e dos dados coletados pela raspagem realizada, iniciou-se a etapa de tratamento de dados utilizando a linguagem Python.

Esse tratamento de dados consistiu em processos como:

- Organizar as informações coletadas: juntar a base disponibilizada com as informações obtidas pela raspagem de dados
- Revisar os dados das bases: comparar as informações e identificar os tratamentos necessários para início do projeto
- Remover informações duplicadas: eliminar colunas iguais resultante da junção das bases e valores redundantes das colunas da raspagem
- Reestruturar dados obtidos do site: reclassificar algumas informações como os recursos de acessibilidade para que fosse possível criar uma classificação
- Complementar informações faltantes: pesquisar e incluir dados de endereço de 69 museus (1,7% do total) utilizando a biblioteca Nominatim e serviços de geocodificação
- Ajustar e corrigir termos e palavras: normalização de diversos termos como "rampa", "rampas", "Rampa", "Rampas", "RAMPA", "Rampa de acesso" para melhor funcionamento dos filtros e apresentação

## Apresentação dos dados

Após todo o tratamento das informações foi iniciada a apresentação desses dados, em 2 formatos:

### Mapa de museus acessíveis

A primeira apresentação, pensando em um público amplo, deveria ser em um formato que permitisse explorar os dados de forma geoespacial, navegando em um mapa para conhecer as instituições que podemos visitar.

Além dessa navegação, era fundamental pontuar as questões de acessibilidade no cadastro dos museus. Observando os dados cadastrados no [MuseusBR](http://museus.cultura.gov.br/), existem três temas dentro do menu "Público, Acessibilidade e Serviços":

1. Pessoas com dificuldade de locomoção
2. Pessoas com deficiências auditivas e/ou visuais
3. Infraestrutura para atendimento a turistas estrangeiros

Utilizando essas dimensões como base, foi criada a seguinte classificação, chamada "Nível de acessibilidade":

1. "**Acessível**": É o museu que possui ao menos um recurso ou infraestrutura **em todas as três dimensões**
2. "**Parcialmente Acessível**": É a instituição que possui ao menos **um recurso ou infraestrutura em alguma das dimensões, mas não em todas** elas
3. "**Sem acessibilidade**": Considerado quando todas as três dimensões estão marcadas como "**Não possui**", "**Não disponível**" ou "**Não se aplica**"
4. "**Sem informação sobre acessibilidade**": Classificação exibida quando as dimensões estão como "**Não informado**" ou "**Não há dados**"

No mapa, pensando em otimizar a experiência das pessoas durante a consulta, quando o museu está classificado como "Sem acessibilidade" ou "Sem informação sobre acessibilidade" é suprimida a parte "Recursos de Acessibilidade".

De forma complementar a navegação no mapa, foram incluídos os seguintes filtros para auxiliar a busca pelos museus:

1. Buscar por nome
2. Estado
3. Nível de acessibilidade
4. Recursos de acessibilidade
5. Temática
6. Funcionamento do museu
7. Visita com guia
8. Entrada gratuita

Essas funcionalidades auxiliam a encontrar e explorar os museus existentes.

#### Bibliotecas JavaScript utilizadas

Para carregar e exibir os dados de forma dinâmica no site, foram utilizadas bibliotecas JavaScript de código aberto.

A biblioteca **PapaParse** foi responsável por ler arquivos CSV diretamente no navegador, permitindo que a base de dados dos museus fosse carregada de forma rápida. Isso facilitou a alimentação automática dos filtros e do mapa, garantindo maior leveza ao site.

Já a biblioteca **Leaflet** foi empregada para criar o mapa interativo que apresenta os museus de todo o Brasil. Por ser uma solução gratuita, leve e personalizável, o **Leaflet** possibilitou adicionar marcadores customizados, alternar entre modo claro e escuro e permitir a navegação geoespacial de forma intuitiva e acessível, mesmo com um grande volume de pontos exibidos simultaneamente.

### Visualização de Dados

Outra forma de contribuir para a discussão do tema foi trazer uma visualização dos dados utilizados para montar o mapa.

Complementando a visão do mapa e com objetivo de dar mais visibilidade aos temas de cultura e acessibilidade, foram explorados dados como:

1. Porcentagem de museus com acessibilidade no Brasil
2. Acessibilidade dos museus por estado
3. Principais recursos e infraestrutura de acessibilidade
4. Museus sem recursos ou sem informação
5. Situação de funcionamento dos museus cadastrados
6. Temáticas dos Museus no Brasil
7. Visitas Guiadas nos Museus Brasileiros
8. Cobrança de Entrada nos Museus Brasileiros
9. Presença Digital dos Museus Brasileiros

Tanto a segmentação quanto a organização mais visual em gráficos permite olhar sobre os dados e informações por outras perspectivas, contribuindo para um olhar mais amplo sobre os assuntos.

#### Decisões de visualização

Todas as visualizações de dados apresentadas foram pensadas para funcionar também em telas grandes (resoluções maiores que 1024px) quanto em telas de celulares e tablets.

A escolha das visualizações levou em conta quesitos como:

- Clareza da informação apresentada, minimizando erros de interpretação
- Facilidade no consumo da informação, reduzindo o esforço para obter o dado
- Interação com os dados, permitindo o aprofundamento no tema apresentado, quando aplicável

Para isso foram escolhidos desenhos como:

- Gráficos de barras horizontais para facilitar a leitura de rótulos longos e comparação com outras informações
- Gráficos de barras empilhadas, para uma visão geral seguido de informações detalhadas sobre sua divisão
- Tabelas ordenáveis para permitir diferentes análises exploratórias e facilitar comparações

---

# Acessibilidade no projeto

Para a realização do projeto era evidente a necessidade de uma atenção com a acessibilidade das informações portanto, foram trabalhados recursos voltados para auxiliar as pessoas a consumirem o conteúdo deste trabalho, tais como:

- **Navegação via teclado**: possibilitando o uso sem o mouse no computador
- **Informações acessíveis via leitores de tela**: para que pessoas cegas ou com baixa visão possam consumir as informações
- **Modo de contraste claro e escuro**: adaptando o site para pessoas neurodivergentes ou para ambientes específicos, conforme a preferência ou necessidade
- **Ajuste no tamanho do texto**: possibilidade de aumentar ou diminuir o tamanho da fonte em todo o site
- **Cores com contraste adequado**: garantindo um contraste mínimo para melhor visualização das informações

Essas funcionalidades adicionadas ainda podem e devem ser melhoradas para uma melhor experiência para todo o público.

---

# Considerações éticas

Todos os dados utilizados são públicos e disponibilizados pelo [MuseusBR](http://museus.cultura.gov.br/).

O projeto tem caráter informativo e não substitui a consulta direta aos museus para confirmação de recursos específicos de acessibilidade. Todos os museus apresentados possuem o link direto para sua respectiva página oficial na plataforma [MuseusBR](http://museus.cultura.gov.br/).

A classificação de acessibilidade proposta foi desenvolvida somente a partir das categorias disponíveis na plataforma e a construção do projeto foi realizada com base nas diretrizes de acessibilidade da [WCAG (Web Content Accessibility Guidelines)](https://www.w3.org/Translations/WCAG20-pt-br/WCAG20-pt-br-20141024/).

Reconhece-se que uma validação com especialistas em acessibilidade e, especialmente, com pessoas com deficiência para testar tanto o conteúdo quanto o formato de apresentação, agregaria robustez metodológica e legitimidade ao projeto.

## Uso de inteligência artificial

Foram utilizados os modelos de inteligência artificial **ChatGPT-5** e **Claude Sonet 4.5** (das empresas **OpenAI** e **Anthropic**, respectivamente) para criação, revisão e teste do código utilizado para raspagem de dados, análise e construção do site e de suas visualizações de dados.

---

# Trabalhos futuros e possibilidades de expansão

Este projeto representa uma primeira etapa na democratização do acesso a informações sobre acessibilidade em museus brasileiros. Para aprimoramentos futuros, sugere-se:

- **Atualização periódica dos dados**: Implementar coleta automatizada trimestral ou semestral para manter as informações atualizadas
- **Validação com usuários**: Realizar testes de usabilidade com pessoas com deficiência para validar a classificação e a experiência de uso
- **Sistema de feedback**: Permitir que visitantes reportem inconsistências ou atualizações sobre a acessibilidade dos museus
- **Expansão para outros equipamentos culturais**: Possibilidade de aplicar a mesma metodologia para teatros, cinemas, bibliotecas e centros culturais

---

# Licença para uso

Todo o projeto é distribuído com a licença [Creative Commons Attribution Share Alike 4.0 International](https://choosealicense.com/licenses/cc-by-sa-4.0/).
