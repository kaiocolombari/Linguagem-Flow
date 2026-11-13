# LinguaFlow 🌍

> Extensão para Google Chrome voltada ao aprendizado de idiomas, com tradução contextual, leitura, pronúncia, vocabulário, flashcards e futuramente um tutor de inteligência artificial executado localmente com WebGPU.

**Status:** Em desenvolvimento  
**Plataforma:** Google Chrome — Manifest V3  
**Interface principal:** Side Panel  
**Idioma nativo:** Português (Brasil)  
**Idiomas de aprendizado:** Alemão, Inglês, Francês, Italiano e Espanhol.

---

# 1. Visão geral

O LinguaFlow será uma extensão de aprendizado de idiomas que permitirá ao usuário estudar enquanto navega pela internet.

A proposta é integrar ferramentas de tradução e aprendizado diretamente ao navegador, evitando depender de serviços externos pagos ou de um servidor próprio.

## Objetivos principais

- [ ] Traduzir textos selecionados em páginas da internet.
- [ ] Traduzir textos inseridos manualmente.
- [ ] Permitir tradução nos dois sentidos.
- [ ] Reproduzir a pronúncia de palavras e frases.
- [ ] Ler e interpretar textos de páginas da internet.
- [ ] Salvar palavras e expressões no vocabulário pessoal.
- [ ] Manter histórico de traduções.
- [ ] Criar flashcards para revisão.
- [ ] Acompanhar o progresso de aprendizado.
- [ ] Desenvolver futuramente um tutor de conversação com IA local.

## Princípios técnicos

- Não depender de backend próprio.
- Priorizar processamento local.
- Não exigir cadastro ou autenticação inicialmente.
- Armazenar dados do usuário localmente.
- Manter a aplicação modular e expansível.
- Evitar acoplamento entre interface e provedores de IA.
- Priorizar privacidade e funcionamento offline sempre que possível.

---

# 2. Stack tecnológica

## Base da aplicação

| Tecnologia | Responsabilidade |
|---|---|
| React | Interface |
| TypeScript | Tipagem e segurança |
| Vite | Build e desenvolvimento |
| CRXJS | Integração com Chrome Extensions |
| React Router DOM | Navegação entre páginas |
| Tailwind CSS | Estilização |
| Chrome Extension API | Recursos do navegador |

## Armazenamento

| Tecnologia | Responsabilidade |
|---|---|
| chrome.storage.local | Configurações e preferências |
| chrome.storage.sync | Pequenas configurações sincronizáveis |
| IndexedDB | Vocabulário, histórico, progresso e dados maiores |

## Tecnologias planejadas para IA

| Tecnologia | Responsabilidade |
|---|---|
| WebGPU | Aceleração por GPU |
| WebLLM | Execução local de modelos de linguagem |
| Transformers.js | Execução local de modelos especializados |
| ONNX Runtime Web | Inferência de modelos ONNX |
| Web Workers | Processamento sem bloquear a interface |
| SpeechSynthesis | Reprodução de pronúncia |
| Whisper / Transformers.js | Possível reconhecimento de fala |

---

# 3. Organização do projeto

Estrutura planejada. Ela poderá ser ajustada conforme o template gerado pelo CRXJS e as necessidades reais do desenvolvimento.

```text
lingua-flow/
│
├── public/
│   ├── icons/
│   └── assets/
│
├── src/
│   │
│   ├── app/
│   │   ├── App.tsx
│   │   ├── router.tsx
│   │   ├── layouts/
│   │   │   └── MainLayout.tsx
│   │   └── providers/
│   │
│   ├── sidepanel/
│   │   └── main.tsx
│   │
│   ├── popup/
│   │   └── main.tsx
│   │
│   ├── background/
│   │   └── index.ts
│   │
│   ├── content/
│   │   ├── index.ts
│   │   ├── selection.ts
│   │   └── page-reader.ts
│   │
│   ├── components/
│   │   ├── ui/
│   │   ├── layout/
│   │   └── language-selector/
│   │
│   ├── features/
│   │   ├── translator/
│   │   ├── vocabulary/
│   │   ├── flashcards/
│   │   ├── history/
│   │   ├── pronunciation/
│   │   ├── page-reader/
│   │   ├── progress/
│   │   └── ai-tutor/
│   │
│   ├── services/
│   │   ├── translation/
│   │   │   ├── providers/
│   │   │   └── translation.service.ts
│   │   ├── speech/
│   │   ├── storage/
│   │   └── ai/
│   │
│   ├── workers/
│   │   └── ai.worker.ts
│   │
│   ├── shared/
│   │   ├── types/
│   │   ├── constants/
│   │   ├── utils/
│   │   └── config/
│   │
│   └── styles/
│       └── global.css
│
├── public/
├── sidepanel.html
├── manifest.config.ts
├── vite.config.ts
├── tsconfig.json
├── package.json
└── README.md
```

### Responsabilidade das pastas

- `app/`: inicialização, roteamento e organização da aplicação.
- `sidepanel/`: ponto de entrada da interface principal.
- `popup/`: possível interface de acesso rápido.
- `background/`: eventos, mensagens e integrações com o navegador.
- `content/`: interação com páginas visitadas pelo usuário.
- `components/`: componentes reutilizáveis.
- `features/`: funcionalidades independentes.
- `services/`: regras de negócio e comunicação com provedores.
- `workers/`: processamento pesado em segundo plano.
- `shared/`: tipos, constantes e utilitários compartilhados.

---

# 4. Fase 1 — Configuração do projeto

**Objetivo:** preparar o ambiente e conseguir executar o LinguaFlow como uma extensão real do Chrome.

## 4.1 — Criação do projeto

- [x] Criar projeto utilizando CRXJS.
- [x] Selecionar React.
- [x] Selecionar TypeScript.
- [x] Definir nome `lingua-flow`.
- [x] Instalar dependências.
- [x] Verificar execução inicial do Vite.
- [x] Instalar React Router DOM.
- [ ] Instalar Tailwind CSS.
- [ ] Configurar ESLint.
- [ ] Configurar Prettier.

## 4.2 — Configurações da extensão

- [x] Entender a estrutura do Manifest V3.
- [x] Configurar nome, descrição e versão.
- [x] Configurar ícones da extensão.
- [x] Configurar permissões necessárias.
- [x] Configurar `side_panel`.
- [x] Configurar página principal do Side Panel.
- [x] Configurar Background Service Worker.
- [x] Configurar abertura do Side Panel ao clicar no ícone.
- [x] Configurar entradas do Vite para o Side Panel.
- [x] Verificar compatibilidade entre Vite e CRXJS.
- [x] Configurar o ambiente de desenvolvimento.
- [x] Carregar a pasta `dist` em `chrome://extensions`.
- [x] Testar atualizações automáticas durante o desenvolvimento.

## 4.3 — Testes iniciais

- [x] Abrir o Side Panel pelo ícone da extensão.
- [x] Verificar se a interface carrega corretamente.
- [x] Verificar se o React está funcionando.
- [ ] Verificar se o Tailwind está funcionando.
- [x] Verificar o funcionamento do Hot Reload.
- [x] Testar console e inspeção de erros.
- [x] Testar recarga da extensão.

**Critério de conclusão:** extensão carregando corretamente no Chrome, com React funcionando dentro do Side Panel.

---

# 5. Fase 2 — Arquitetura e navegação

**Objetivo:** organizar a aplicação antes de implementar suas funcionalidades.

## 5.1 — Estrutura

- [ ] Criar pastas `app`, `features`, `components`, `services` e `shared`.
- [ ] Criar estrutura inicial das funcionalidades.
- [ ] Separar componentes visuais das regras de negócio.
- [ ] Criar arquivo central de tipos compartilhados.
- [ ] Definir convenções de nomenclatura.
- [ ] Definir organização dos imports.

## 5.2 — React Router

- [ ] Configurar React Router DOM.
- [ ] Implementar `createHashRouter`.
- [ ] Criar `MainLayout`.
- [ ] Criar navegação lateral ou inferior.
- [ ] Criar `Outlet` para renderização das páginas.
- [ ] Implementar `NavLink` para navegação.
- [ ] Criar rotas das funcionalidades.
- [ ] Criar rota de página não encontrada.
- [ ] Testar navegação sem recarregar a extensão.

### Rotas planejadas

| Rota | Página |
|---|---|
| `/` | Tradutor |
| `/vocabulary` | Vocabulário |
| `/flashcards` | Flashcards |
| `/history` | Histórico |
| `/progress` | Progresso |
| `/tutor` | Tutor IA |
| `/settings` | Configurações |

**Critério de conclusão:** todas as páginas acessíveis pelo menu, utilizando um layout compartilhado.

---

# 6. Fase 3 — Frontend e experiência visual

**Objetivo:** construir toda a interface antes de implementar as regras de negócio.

## 6.1 — Design System

- [ ] Definir identidade visual.
- [ ] Definir paleta de cores.
- [ ] Definir tipografia.
- [ ] Definir espaçamentos.
- [ ] Definir bordas e arredondamentos.
- [ ] Criar componentes de botão.
- [ ] Criar componentes de input.
- [ ] Criar componentes de seleção.
- [ ] Criar componentes de modal.
- [ ] Criar componentes de tooltip.
- [ ] Criar componentes de carregamento.
- [ ] Criar componentes de feedback e notificações.
- [ ] Implementar tema claro.
- [ ] Implementar tema escuro.
- [ ] Implementar responsividade para diferentes larguras do Side Panel.

## 6.2 — Layout principal

- [ ] Criar cabeçalho.
- [ ] Criar navegação principal.
- [ ] Criar área de conteúdo.
- [ ] Criar navegação entre funcionalidades.
- [ ] Criar identificação visual da página atual.
- [ ] Criar área de configurações rápidas, se necessário.

## 6.3 — Telas

### Tradutor

- [ ] Criar seletor de idioma de origem.
- [ ] Criar seletor de idioma de destino.
- [ ] Criar botão para inverter idiomas.
- [ ] Criar campo de texto de entrada.
- [ ] Criar área de resultado.
- [ ] Criar botão de tradução.
- [ ] Criar botão para copiar resultado.
- [ ] Criar botão de pronúncia.
- [ ] Criar botão para salvar palavra ou frase.
- [ ] Criar estados de carregamento e erro.

### Vocabulário

- [ ] Criar listagem de palavras.
- [ ] Criar campo de pesquisa.
- [ ] Criar filtros por idioma.
- [ ] Criar visualização detalhada.
- [ ] Criar formulário de edição.
- [ ] Criar opção de exclusão.

### Flashcards

- [ ] Criar componente de cartão.
- [ ] Criar animação de inversão.
- [ ] Criar botões de avaliação.
- [ ] Criar tela de sessão de revisão.
- [ ] Criar indicador de progresso.

### Histórico

- [ ] Criar listagem de traduções.
- [ ] Criar pesquisa.
- [ ] Criar filtros.
- [ ] Criar visualização de detalhes.

### Progresso

- [ ] Criar indicadores de palavras aprendidas.
- [ ] Criar gráficos de evolução.
- [ ] Criar estatísticas de revisão.
- [ ] Criar indicadores de frequência de estudo.

### Tutor IA

- [ ] Criar interface de chat.
- [ ] Criar área de mensagens.
- [ ] Criar campo de entrada.
- [ ] Criar botão de envio.
- [ ] Criar indicadores de processamento.
- [ ] Criar visualização de correções.
- [ ] Criar seletor de idioma e nível.

### Configurações

- [ ] Criar seleção de idioma nativo.
- [ ] Criar seleção de idiomas de aprendizado.
- [ ] Criar configurações de pronúncia.
- [ ] Criar configurações de aparência.
- [ ] Criar gerenciamento de modelos futuramente.

**Critério de conclusão:** todas as telas principais construídas e navegáveis, inicialmente com dados fictícios.

---

# 7. Fase 4 — Lógica e arquitetura de dados

**Objetivo:** implementar as regras de negócio que dão funcionamento à interface.

## 7.1 — Tipos e modelos

- [ ] Criar tipo `Language`.
- [ ] Criar tipo `Translation`.
- [ ] Criar tipo `VocabularyEntry`.
- [ ] Criar tipo `Flashcard`.
- [ ] Criar tipo `TranslationHistory`.
- [ ] Criar tipo `UserProgress`.
- [ ] Criar tipo `AppSettings`.
- [ ] Definir relacionamentos entre os dados.
- [ ] Definir identificadores únicos.
- [ ] Definir datas de criação e atualização.

## 7.2 — Armazenamento local

- [ ] Estudar Chrome Storage API.
- [ ] Estudar IndexedDB.
- [ ] Definir quais dados ficam em cada armazenamento.
- [ ] Criar serviço de configurações.
- [ ] Criar serviço de vocabulário.
- [ ] Criar serviço de histórico.
- [ ] Criar serviço de flashcards.
- [ ] Criar serviço de progresso.
- [ ] Implementar operações CRUD.
- [ ] Implementar validação dos dados.
- [ ] Implementar tratamento de erros.
- [ ] Testar persistência após fechar o Chrome.

## 7.3 — Integração entre frontend e lógica

- [ ] Conectar formulário do tradutor ao serviço de tradução.
- [ ] Conectar vocabulário ao armazenamento.
- [ ] Conectar histórico ao armazenamento.
- [ ] Conectar flashcards aos dados salvos.
- [ ] Conectar gráficos às estatísticas.
- [ ] Implementar estados de carregamento.
- [ ] Implementar tratamento de erros.
- [ ] Evitar duplicação de regras de negócio nos componentes.

**Critério de conclusão:** funcionalidades principais operando com dados persistentes, mesmo antes da integração com modelos de IA.

---

# 8. Fase 5 — Integração com Chrome

**Objetivo:** permitir que o LinguaFlow interaja com as páginas visitadas.

## 8.1 — Comunicação interna

- [ ] Estudar mensagens da Chrome Runtime API.
- [ ] Implementar comunicação entre Side Panel e Background.
- [ ] Implementar comunicação entre Content Script e Background.
- [ ] Definir padrões de mensagens.
- [ ] Criar tipos para mensagens.
- [ ] Implementar tratamento de falhas de comunicação.

## 8.2 — Seleção de texto

- [ ] Criar Content Script.
- [ ] Capturar texto selecionado.
- [ ] Criar menu de contexto.
- [ ] Implementar ação de tradução no menu.
- [ ] Enviar texto selecionado para o Side Panel.
- [ ] Exibir texto recebido na interface.
- [ ] Tratar seleção vazia.
- [ ] Testar em diferentes sites.

## 8.3 — Leitura de páginas

- [ ] Implementar captura do conteúdo textual.
- [ ] Filtrar elementos desnecessários.
- [ ] Evitar capturar campos de senha ou dados sensíveis.
- [ ] Criar opção para ler página inteira.
- [ ] Criar opção para ler apenas trecho selecionado.
- [ ] Implementar comunicação com a interface.
- [ ] Tratar páginas incompatíveis.

**Critério de conclusão:** selecionar um texto em uma página e enviá-lo para o LinguaFlow.

---

# 9. Fase 6 — Sistema de tradução

**Objetivo:** implementar tradução real sem depender de backend próprio.

## 9.1 — Arquitetura

- [ ] Criar interface `TranslationProvider`.
- [ ] Criar serviço central de tradução.
- [ ] Separar interface dos provedores.
- [ ] Implementar validação de idiomas.
- [ ] Implementar identificação de idioma, se viável.
- [ ] Implementar tratamento de textos muito grandes.
- [ ] Implementar cache de traduções.

Exemplo de contrato:

```ts
export interface TranslationProvider {
  translate(
    text: string,
    source: string,
    target: string
  ): Promise<string>;
}
```

## 9.2 — Pesquisa e testes de modelos

- [ ] Estudar NLLB-200.
- [ ] Estudar TranslateGemma.
- [ ] Avaliar outras alternativas executáveis no navegador.
- [ ] Verificar cobertura dos idiomas desejados.
- [ ] Testar português para inglês.
- [ ] Testar inglês para português.
- [ ] Testar português para alemão.
- [ ] Testar português para francês.
- [ ] Testar português para italiano.
- [ ] Testar português para espanhol.
- [ ] Testar tradução entre idiomas estrangeiros.
- [ ] Comparar qualidade.
- [ ] Comparar velocidade.
- [ ] Comparar consumo de memória.

## 9.3 — Integração

- [ ] Implementar primeiro provedor.
- [ ] Integrar serviço com frontend.
- [ ] Implementar tradução bidirecional.
- [ ] Integrar tradução de textos selecionados.
- [ ] Integrar histórico.
- [ ] Integrar salvamento no vocabulário.
- [ ] Implementar feedback de processamento.
- [ ] Implementar erros de carregamento e tradução.

**Critério de conclusão:** traduzir textos reais localmente nos idiomas suportados.

---

# 10. Fase 7 — Pronúncia e leitura

**Objetivo:** permitir que o usuário escute e pratique os idiomas.

- [ ] Estudar SpeechSynthesis API.
- [ ] Listar vozes disponíveis.
- [ ] Selecionar voz conforme o idioma.
- [ ] Reproduzir palavras individualmente.
- [ ] Reproduzir frases completas.
- [ ] Implementar controle de velocidade.
- [ ] Implementar pausa e retomada.
- [ ] Integrar pronúncia ao tradutor.
- [ ] Integrar pronúncia ao vocabulário.
- [ ] Integrar pronúncia aos flashcards.
- [ ] Implementar leitura de textos selecionados.
- [ ] Testar disponibilidade e qualidade das vozes.

**Critério de conclusão:** reproduzir palavras e frases com uma voz adequada ao idioma selecionado.

---

# 11. Fase 8 — Vocabulário, histórico e aprendizado

**Objetivo:** transformar traduções em material de estudo.

## 11.1 — Vocabulário

- [ ] Salvar palavras e expressões.
- [ ] Salvar tradução.
- [ ] Salvar idioma de origem e destino.
- [ ] Permitir adicionar observações.
- [ ] Permitir editar palavras.
- [ ] Permitir excluir palavras.
- [ ] Pesquisar palavras.
- [ ] Filtrar por idioma.

## 11.2 — Flashcards

- [ ] Criar sistema de revisão.
- [ ] Exibir palavra e tradução.
- [ ] Implementar inversão do cartão.
- [ ] Registrar acertos e erros.
- [ ] Criar sistema de repetição espaçada.
- [ ] Definir intervalo de revisão.
- [ ] Priorizar palavras com maior dificuldade.
- [ ] Registrar sessões de estudo.

## 11.3 — Histórico

- [ ] Salvar traduções realizadas.
- [ ] Pesquisar traduções antigas.
- [ ] Filtrar por idioma.
- [ ] Permitir excluir registros.
- [ ] Permitir transformar tradução em vocabulário.

## 11.4 — Progresso

- [ ] Contabilizar palavras aprendidas.
- [ ] Contabilizar revisões.
- [ ] Registrar frequência de estudo.
- [ ] Criar gráficos de evolução.
- [ ] Criar indicadores de desempenho.

**Critério de conclusão:** o usuário consegue organizar, revisar e acompanhar seu aprendizado.

---

# 12. Fase 9 — Inteligência Artificial e WebGPU

**Objetivo:** desenvolver um tutor de idiomas executado localmente, sem depender de uma API externa.

## 12.1 — Estudo e validação técnica

- [ ] Estudar funcionamento do WebGPU.
- [ ] Verificar disponibilidade de `navigator.gpu`.
- [ ] Testar WebGPU no Chrome.
- [ ] Verificar compatibilidade com GPU e drivers.
- [ ] Testar operações básicas na GPU.
- [ ] Estudar Web Workers.
- [ ] Estudar inferência local no navegador.
- [ ] Comparar WebLLM e Transformers.js.
- [ ] Avaliar consumo de RAM e VRAM.
- [ ] Medir velocidade de inferência.
- [ ] Avaliar alternativas de execução em WASM.

## 12.2 — Gerenciamento de modelos

- [ ] Criar sistema de seleção de modelos.
- [ ] Criar interface de download.
- [ ] Exibir progresso de download.
- [ ] Armazenar modelos em cache.
- [ ] Detectar modelos já baixados.
- [ ] Permitir excluir modelos.
- [ ] Exibir espaço ocupado.
- [ ] Implementar carregamento e descarregamento.
- [ ] Tratar incompatibilidade de hardware.
- [ ] Tratar falta de memória.
- [ ] Implementar fallback quando viável.

## 12.3 — Tutor inteligente

- [ ] Criar interface de conversação funcional.
- [ ] Definir níveis de dificuldade.
- [ ] Permitir escolher idioma da conversa.
- [ ] Implementar contexto de conversação.
- [ ] Criar instruções para o tutor atuar como professor.
- [ ] Implementar correção gramatical.
- [ ] Explicar erros na língua nativa.
- [ ] Sugerir formas mais naturais de expressão.
- [ ] Criar exercícios a partir das conversas.
- [ ] Integrar vocabulário salvo ao tutor.
- [ ] Criar simulações de situações cotidianas.
- [ ] Salvar conversas localmente.

**Critério de conclusão:** conversar com um tutor de IA no navegador, com geração de respostas local.

---

# 13. Fase 10 — Reconhecimento de fala

**Objetivo:** permitir que o usuário pratique conversação também por voz.

- [ ] Pesquisar modelos locais de reconhecimento de fala.
- [ ] Avaliar Whisper com Transformers.js.
- [ ] Testar reconhecimento dos idiomas suportados.
- [ ] Implementar captura de áudio mediante permissão.
- [ ] Converter áudio em texto.
- [ ] Integrar texto reconhecido ao tutor.
- [ ] Comparar fala reconhecida com frase esperada.
- [ ] Avaliar feedback de pronúncia.
- [ ] Tratar permissões e erros de microfone.

**Critério de conclusão:** usuário consegue falar com o tutor e receber respostas e correções.

---

# 14. Fase 11 — Testes, otimização e publicação

**Objetivo:** preparar o LinguaFlow para uso real e publicação.

## 14.1 — Testes

- [ ] Testar funcionalidades individualmente.
- [ ] Testar componentes React.
- [ ] Testar serviços e regras de negócio.
- [ ] Testar comunicação entre os componentes da extensão.
- [ ] Testar persistência dos dados.
- [ ] Testar funcionamento após reiniciar o Chrome.
- [ ] Testar funcionamento offline quando os recursos estiverem disponíveis localmente.
- [ ] Testar diferentes larguras do Side Panel.
- [ ] Testar erros de carregamento dos modelos.

## 14.2 — Otimização

- [ ] Otimizar consumo de memória.
- [ ] Otimizar carregamento dos modelos.
- [ ] Evitar renderizações desnecessárias.
- [ ] Implementar carregamento sob demanda.
- [ ] Otimizar armazenamento local.
- [ ] Verificar compatibilidade com diferentes máquinas.

## 14.3 — Publicação

- [ ] Revisar permissões solicitadas.
- [ ] Revisar privacidade e segurança.
- [ ] Verificar políticas da Chrome Web Store.
- [ ] Criar página de apresentação.
- [ ] Criar ícones e imagens promocionais.
- [ ] Criar política de privacidade.
- [ ] Gerar build de produção.
- [ ] Testar pacote final.
- [ ] Publicar na Chrome Web Store.

**Critério de conclusão:** extensão estável, documentada e pronta para distribuição.

---

# 15. Decisões arquiteturais importantes

## Sem backend próprio

O projeto deverá funcionar sem uma API hospedada pelo desenvolvedor.

A extensão será responsável por executar as funcionalidades e armazenar os dados localmente.

## Separação entre frontend e lógica

Os componentes React devem cuidar principalmente da apresentação e interação com o usuário.

As regras de negócio devem ficar em serviços ou módulos próprios.

Exemplo:

```text
TranslatorPage
      |
      v
translation.service.ts
      |
      v
TranslationProvider
      |
      v
Modelo de tradução
```

Isso permite trocar o mecanismo de tradução sem reconstruir a interface.

## IA local

Os modelos poderão ser baixados sob demanda e armazenados em cache.

O processamento será feito no dispositivo do usuário. O primeiro download exigirá internet, e o funcionamento posterior dependerá da disponibilidade dos arquivos em cache.

## Processamento em segundo plano

Modelos de IA não devem bloquear a interface.

Sempre que necessário, utilizar Web Workers para executar operações pesadas.

## Privacidade

- Não coletar textos de páginas sem uma ação ou permissão adequada do usuário.
- Não enviar conversas ou traduções para servidores externos sem consentimento.
- Não armazenar dados desnecessários.
- Explicar claramente as permissões solicitadas.

---

# 16. Idiomas suportados

| Idioma | Código |
|---|---|
| Português (Brasil) | `pt-BR` |
| Inglês | `en` |
| Alemão | `de` |
| Francês | `fr` |
| Italiano | `it` |
| Espanhol | `es` |

A implementação deverá considerar que nem todos os modelos suportam todos os pares de idiomas com a mesma qualidade.

---

# 17. Acompanhamento geral

Atualize os status conforme avançar.

| Fase | Status |
|---|---|
| 1. Configuração | ⬜ Não iniciado |
| 2. Arquitetura e navegação | ⬜ Não iniciado |
| 3. Frontend | ⬜ Não iniciado |
| 4. Lógica e dados | ⬜ Não iniciado |
| 5. Integração Chrome | ⬜ Não iniciado |
| 6. Tradução | ⬜ Não iniciado |
| 7. Pronúncia | ⬜ Não iniciado |
| 8. Vocabulário e aprendizado | ⬜ Não iniciado |
| 9. IA e WebGPU | ⬜ Não iniciado |
| 10. Reconhecimento de fala | ⬜ Não iniciado |
| 11. Testes e publicação | ⬜ Não iniciado |

Legenda:

- ⬜ Não iniciado
- 🟡 Em andamento
- 🟢 Concluído
- 🔴 Bloqueado

---

# 18. Registro de desenvolvimento

Utilize esta seção para documentar decisões técnicas, problemas encontrados e soluções implementadas.

## Decisões técnicas

- 

## Problemas encontrados

- 

## Soluções implementadas

- 

## Próximas tarefas

- 

## Alterações futuras de arquitetura

- 

---

# 19. Referências técnicas

### Desenvolvimento

- [Chrome Extensions Documentation](https://developer.chrome.com/docs/extensions/)
- [CRXJS](https://crxjs.dev/)
- [React](https://react.dev/)
- [React Router](https://reactrouter.com/)
- [TypeScript](https://www.typescriptlang.org/docs/)
- [Vite](https://vite.dev/)
- [Tailwind CSS](https://tailwindcss.com/docs)

### IA e processamento local

- [WebGPU Documentation](https://developer.mozilla.org/en-US/docs/Web/API/WebGPU_API)
- [WebLLM](https://github.com/mlc-ai/web-llm)
- [Transformers.js](https://huggingface.co/docs/transformers.js/)
- [ONNX Runtime Web](https://onnxruntime.ai/docs/get-started/with-javascript/web.html)

---

**Meta final:** criar uma extensão de aprendizado de idiomas completa, modular, privada e capaz de executar modelos de inteligência artificial diretamente no navegador, aproveitando os recursos de hardware do próprio usuário.