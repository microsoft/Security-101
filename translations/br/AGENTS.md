<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:33:55+00:00",
  "source_file": "AGENTS.md",
  "language_code": "br"
}
-->
# AGENTS.md

## Visão Geral do Projeto

**Security-101** é um currículo de cibersegurança para iniciantes criado pela Microsoft. O projeto é um recurso de aprendizado baseado em documentação que ensina conceitos fundamentais de cibersegurança por meio de módulos estruturados. Ele é independente de fornecedores e foi projetado para ser concluído em pequenas lições (30-60 minutos cada).

**Principais Tecnologias:**
- Markdown para conteúdo
- Docsify para geração de site estático
- GitHub Pages para hospedagem
- Co-op Translator para suporte multilíngue (50+ idiomas)
- GitHub Actions para CI/CD

**Arquitetura:**
- Conteúdo educacional organizado em 8 módulos principais, cada um com sublições
- Site HTML estático com Docsify renderizando conteúdo em Markdown
- Fluxo de trabalho de tradução automatizado usando serviços de IA da Azure
- Sem ferramentas de build ou gerenciadores de pacotes necessários para o conteúdo principal

## Estrutura do Repositório

```
/
├── README.md                    # Main entry point with curriculum overview
├── index.html                   # Docsify site entry point
├── [1-8].[1-4] *.md            # Curriculum modules and lessons
├── CODE_OF_CONDUCT.md          # Community guidelines
├── SECURITY.md                 # Security policy
├── SUPPORT.md                  # Support information
├── LICENSE                     # MIT License
├── images/                     # Image assets for lessons
├── translated_images/          # Translated image assets
├── translations/               # Translated versions (50+ languages)
└── .github/
    ├── workflows/
    │   ├── co-op-translator.yml    # Automated translation workflow
    │   ├── deploy.yaml             # GitHub Pages deployment
    │   └── jekyll-gh-pages.yml     # Jekyll site generation
    └── ISSUE_TEMPLATE/             # Issue templates
```

## Comandos de Configuração

Este é um projeto de documentação sem dependências para instalar. Para trabalhar com o conteúdo:

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Fluxo de Trabalho de Desenvolvimento

### Visualizando o Conteúdo Localmente

O projeto usa Docsify para renderização. Para visualizar alterações:

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Estrutura do Conteúdo

Os módulos são numerados sequencialmente:
- **Módulo 1:** Conceitos básicos de segurança (1.1-1.7)
- **Módulo 2:** Gerenciamento de identidade e acesso (2.1-2.4)
- **Módulo 3:** Segurança de rede (3.1-3.4)
- **Módulo 4:** Operações de segurança (4.1-4.4)
- **Módulo 5:** Segurança de aplicações (5.1-5.3)
- **Módulo 6:** Segurança de infraestrutura (6.1-6.3)
- **Módulo 7:** Segurança de dados (7.1-7.3)
- **Módulo 8:** Segurança de IA (8.1-8.4)

Cada módulo termina com um arquivo de quiz (ex.: "1.7 End of module quiz.md").

### Fazendo Alterações no Conteúdo

1. Edite os arquivos Markdown diretamente no diretório raiz
2. Siga a convenção de nomenclatura existente: `[module].[lesson] [Title].md`
3. Atualize a tabela no README.md ao adicionar/remover módulos
4. Adicione imagens ao diretório `/images/`
5. Referencie imagens usando caminhos relativos: `![Descrição](../../translated_images/filename.8c8067c683396b6f17b14be6dc5b8b323f661a863de696f36ec51e4813657b57.br.png)`

## Fluxo de Trabalho de Tradução

**Tradução Automatizada:**
- As traduções são realizadas automaticamente pela GitHub Action Co-op Translator
- Quando você faz push de alterações para a branch `main`, o fluxo de trabalho traduz o conteúdo para mais de 50 idiomas
- Os arquivos traduzidos são armazenados em `/translations/[language_code]/`
- Os metadados de tradução são preservados no frontmatter YAML

**Idiomas Suportados:** Árabe, Bengali, Búlgaro, Birmanês, Chinês (Simplificado, Tradicional), Croata, Tcheco, Dinamarquês, Holandês, Estoniano, Finlandês, Francês, Alemão, Grego, Hebraico, Hindi, Húngaro, Indonésio, Italiano, Japonês, Coreano, Lituano, Malaio, Marathi, Nepali, Norueguês, Persa, Polonês, Português, Punjabi, Romeno, Russo, Sérvio, Eslovaco, Esloveno, Espanhol, Suaíli, Sueco, Tagalo, Tâmil, Tailandês, Turco, Ucraniano, Urdu, Vietnamita e outros.

**Não edite manualmente os arquivos de tradução** - eles serão sobrescritos pelo fluxo de trabalho automatizado.

## Diretrizes de Estilo de Código

### Convenções de Markdown

- Use a sintaxe padrão do Markdown
- Títulos: Use `#` para o título principal, `##` para seções, `###` para subseções
- Listas: Use `-` ou `*` para listas não ordenadas, `1.` para listas ordenadas
- Links: Use texto descritivo com URLs completos do GitHub para referências cruzadas
- Imagens: Armazene no diretório `/images/`, use texto alternativo descritivo
- Blocos de código: Use três crases com identificador de linguagem quando aplicável

### Diretrizes de Conteúdo

- Mantenha as lições focadas e concisas (tempo de leitura de 30-60 minutos)
- Use linguagem clara e acessível para iniciantes
- Evite instruções específicas de ferramentas de fornecedores (o currículo é independente de fornecedores)
- Inclua objetivos de aprendizado no início de cada módulo
- Link para recursos externos do Microsoft Learn quando apropriado
- Certifique-se de que o conteúdo seja educacional, não promocional

### Nomenclatura de Arquivos

- Use o formato: `[Module].[Lesson] [Title].md`
- Exemplo: `1.1 The CIA triad and other key concepts.md`
- Arquivos de quiz: `[Module].[Last] End of module quiz.md`
- Use espaços nos nomes de arquivos (convenção existente)

## Fluxos de Trabalho do GitHub

### Co-op Translator (co-op-translator.yml)

**Trigger:** Push para a branch `main`  
**Propósito:** Traduz automaticamente arquivos Markdown novos/modificados para mais de 50 idiomas

**Variáveis de Ambiente Necessárias:**
- Credenciais do serviço Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Credenciais do Azure OpenAI (alternativa opcional)
- Credenciais do OpenAI (alternativa opcional)

### Deploy (deploy.yaml)

**Trigger:** Push para a branch `main` quando README.md for alterado  
**Propósito:** Faz deploy do site estático para o GitHub Pages  
**Saída:** Atualiza o site do GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Trigger:** Push para a branch configurada  
**Propósito:** Constrói e faz deploy do site usando Jekyll

## Diretrizes para Pull Requests

### Antes de Submeter

1. **Revisão de Conteúdo:** Certifique-se da precisão e clareza dos conceitos de cibersegurança
2. **Formatação:** Verifique se a formatação do Markdown está correta
3. **Links:** Teste todos os links internos e externos
4. **Imagens:** Certifique-se de que todas as imagens carregam e têm texto alternativo descritivo
5. **Consistência:** Siga a estrutura e estilo de conteúdo existentes

### Formato do Título do PR

Use títulos descritivos:
- `Add: [Descrição do novo conteúdo]`
- `Update: [Módulo/Lição] - [Breve descrição]`
- `Fix: [Descrição do problema]`
- `Docs: [Alterações na documentação]`

### Verificações Necessárias

- Precisão do conteúdo (revisão manual)
- Validação da formatação do Markdown
- Verificação de links
- Conclusão do fluxo de trabalho de tradução (para merges na branch `main`)

### Processo de Revisão

1. Pelo menos uma revisão de mantenedor é necessária
2. Foco na precisão técnica dos conceitos de segurança
3. Verifique acessibilidade e facilidade para iniciantes
4. Certifique-se de que a neutralidade em relação a fornecedores seja mantida

## Tarefas Comuns

### Adicionando uma Nova Lição

```bash
# 1. Create new Markdown file with proper naming
touch "[Module].[Lesson] [Title].md"

# 2. Add content following template structure
# 3. Update README.md module table with new entry
# 4. Add entry to module overview table
# 5. Ensure quiz file numbering is correct

# 6. Commit changes
git add "[Module].[Lesson] [Title].md" README.md
git commit -m "Add: [Module].[Lesson] - [Title]"
git push
```

### Atualizando Conteúdo Existente

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Adicionando Imagens

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.br.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Testes e Validação

### Validação de Conteúdo

Como este é um projeto de documentação, os testes se concentram em:

1. **Renderização de Markdown:** Visualize alterações localmente usando Docsify
2. **Validação de Links:** Clique manualmente em todos os links
3. **Carregamento de Imagens:** Verifique se todas as imagens são exibidas corretamente
4. **Tradução:** Verifique se os arquivos são capturados pelo fluxo de trabalho de tradução (automatizado)
5. **Acessibilidade:** Certifique-se de que a hierarquia de títulos e o texto alternativo estão corretos

### Visualização Local

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Checklist Pré-commit

- [ ] Arquivos Markdown usam a sintaxe correta
- [ ] Todos os links são válidos e usam HTTPS sempre que possível
- [ ] Imagens têm texto alternativo descritivo
- [ ] O conteúdo é acessível para iniciantes e preciso
- [ ] A linguagem neutra em relação a fornecedores é mantida
- [ ] README.md atualizado ao adicionar/remover módulos
- [ ] A nomenclatura de arquivos segue as convenções

## Considerações de Segurança

- **Sem segredos no conteúdo:** Nunca faça commit de chaves de API, senhas ou dados sensíveis
- **Validação de links:** Certifique-se de que todos os links externos são de fontes confiáveis
- **Conteúdo de imagens:** Verifique se as imagens não contêm informações sensíveis
- **Fluxo de trabalho de tradução:** Usa serviços de IA da Azure com autenticação adequada
- **SECURITY.md:** Siga o processo de relatório de vulnerabilidades em SECURITY.md

## Recursos Adicionais

### Cursos Relacionados da Microsoft

Este currículo faz parte de uma coleção maior de recursos educacionais da Microsoft:
- IA Generativa para Iniciantes
- IA para Iniciantes
- Ciência de Dados para Iniciantes
- ML para Iniciantes
- Desenvolvimento Web para Iniciantes
- IoT para Iniciantes

### Caminhos de Aprendizado Externos

Após concluir o Security-101:
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Exam SC-900: Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Contribuindo

1. **Faça um fork do repositório** no GitHub
2. **Crie uma branch de feature** para suas alterações
3. **Faça suas alterações** seguindo as diretrizes acima
4. **Teste localmente** para garantir que tudo renderiza corretamente
5. **Submeta um pull request** com uma descrição clara das alterações
6. **Responda ao feedback** dos mantenedores

## Problemas Comuns e Soluções

### Traduções Não Funcionando

- Certifique-se de que as alterações foram feitas push para a branch `main`
- Verifique a aba de GitHub Actions para o status do fluxo de trabalho
- Confirme se os segredos do fluxo de trabalho de tradução estão configurados
- A tradução acontece automaticamente; não edite os arquivos de tradução manualmente

### Imagens Não Carregando

- Verifique se o caminho da imagem usa barras: `images/filename.png`
- Confirme se o arquivo de imagem foi commitado no repositório
- Certifique-se de que o nome do arquivo da imagem corresponde exatamente (case-sensitive)
- Use caminhos relativos, não URLs absolutas

### Docsify Não Renderizando

- Verifique se `index.html` está presente na raiz
- Confirme se os links CDN do Docsify estão acessíveis
- Certifique-se de que os arquivos Markdown usam sintaxe padrão
- Verifique o console do navegador para erros de JavaScript

### Links Não Funcionando

- Use URLs completas do GitHub para referências cruzadas entre lições
- Formato: `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Teste os links na visualização renderizada, não apenas no Markdown bruto

## Manutenção do Projeto

### Tarefas Regulares

- Revisar e mesclar contribuições da comunidade
- Atualizar conteúdo para garantir precisão conforme o cenário de segurança evolui
- Monitorar o fluxo de trabalho de tradução para erros
- Responder a problemas e discussões
- Manter links externos atualizados

### Controle de Versão

- A branch `main` é protegida e requer revisões de PR
- Todas as alterações passam pelo processo de pull request
- Arquivos de tradução são gerados automaticamente, não edite manualmente
- Use mensagens de commit significativas

## Notas para Agentes de Codificação com IA

- **Este é um projeto de documentação** - foque na qualidade do conteúdo, não no código
- **Não modifique arquivos de tradução** - eles são gerados automaticamente
- **Preserve as convenções de nomenclatura de arquivos** - use espaços nos nomes de arquivos conforme o padrão existente
- **Atualize README.md** ao adicionar/remover módulos para manter a tabela sincronizada
- **Teste localmente** antes de submeter PRs para garantir que o Markdown renderiza corretamente
- **Siga o estilo de conteúdo existente** - mantenha o tom acessível para iniciantes e neutro em relação a fornecedores
- **Sem processo de build necessário** - um servidor HTTP simples é suficiente para desenvolvimento local
- **Respeite a estrutura dos módulos** - cada módulo tem numeração e organização consistentes

---

**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autoritativa. Para informações críticas, recomenda-se a tradução profissional realizada por humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações equivocadas decorrentes do uso desta tradução.