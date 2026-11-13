# LinguaFlow 🌍

> Extensão para Google Chrome voltada ao aprendizado de idiomas, com tradução contextual, leitura, pronúncia, vocabulário e, futuramente, um tutor de inteligência artificial executado localmente com WebGPU.

**Status:** Em desenvolvimento  
**Plataforma:** Google Chrome — Manifest V3  
**Idioma nativo:** Português (Brasil)  
**Idiomas de aprendizado:** Alemão, Inglês, Francês, Italiano e Espanhol.

---

## 1. Visão do projeto

O LinguaFlow será uma extensão de aprendizado de idiomas que permitirá ao usuário estudar enquanto navega pela internet.

A proposta é integrar ferramentas de tradução e aprendizado diretamente ao navegador, evitando depender de serviços externos pagos ou de um servidor próprio.

### Objetivos principais

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

### Princípios técnicos

- Não depender de backend próprio.
- Priorizar processamento local.
- Não exigir cadastro ou autenticação inicialmente.
- Armazenar dados do usuário localmente.
- Manter a aplicação modular e expansível.
- Evitar acoplamento entre interface e provedores de IA.
- Priorizar privacidade e funcionamento offline sempre que possível.

---

## 2. Tecnologias

### Base da aplicação

| Tecnologia | Responsabilidade |
|---|---|
| React | Interface |
| TypeScript | Tipagem e segurança |
| Vite | Build e desenvolvimento |
| CRXJS | Integração com Chrome Extensions |
| Tailwind CSS | Estilização |
| Chrome Extension API | Recursos do navegador |

### Armazenamento

| Tecnologia | Responsabilidade |
|---|---|
| chrome.storage.local | Configurações e preferências |
| chrome.storage.sync | Pequenas configurações sincronizáveis |
| IndexedDB | Vocabulário, histórico, progresso e dados maiores |

### Tecnologias planejadas para IA

| Tecnologia | Responsabilidade |
|---|---|
| WebGPU | Aceleração por GPU |
| WebLLM | Execução local de modelos de linguagem |
| Transformers.js | Execução local de modelos especializados |
| ONNX Runtime Web | Inferência de modelos ONNX |
| Web Workers | Processamento sem bloquear a interface |
| SpeechSynthesis | Reprodução de pronúncia |
| Whisper / Transformers.js | Possível reconhecimento de fala |

*As tecnologias de IA serão avaliadas e integradas somente nas etapas futuras.*

---

# 3. Estrutura do projeto

Estrutura planejada para a aplicação. Ela poderá ser ajustada conforme as necessidades reais do desenvolvimento.

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
│   │   ├── routes/
│   │   └── providers/
│   │
│   ├── sidepanel/
│   │   ├── index.html
│   │   └── main.tsx
│   │
│   ├── popup/
│   │   ├── index.html
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
│   │   │   ├── components/
│   │   │   ├── hooks/
│   │   │   └── types/
│   │   │
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
│   │   │
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
├── manifest.config.ts
├── vite.config.ts
├── tsconfig.json
├── package.json
└── README.md
```

### Responsabilidade de cada área

- `app/`: inicialização e organização da aplicação.
- `sidepanel/`: interface principal da extensão.
- `popup/`: acesso rápido às funcionalidades.
- `background/`: eventos, mensagens e integrações com o navegador.
- `content/`: interação com páginas visitadas pelo usuário.
- `components/`: componentes reutilizáveis.
- `features/`: funcionalidades independentes do LinguaFlow.
- `services/`: regras de negócio e comunicação com provedores.
- `workers/`: processamento pesado em segundo plano.
- `shared/`: tipos, constantes e utilitários compartilhados.

---

# 4. Roadmap de desenvolvimento

## Fase 1 — Preparação e configuração

Objetivo: criar a base da extensão e preparar o ambiente.

- [ ] Criar o projeto com React e TypeScript.
- [ ] Configurar Vite.
- [ ] Configurar CRXJS.
- [ ] Configurar Manifest V3.
- [ ] Instalar e configurar Tailwind CSS.
- [ ] Criar a primeira estrutura de pastas.
- [ ] Configurar os ícones da extensão.
- [ ] Criar uma primeira tela de teste.
- [ ] Executar o projeto localmente.
- [ ] Carregar a extensão no Chrome através de `chrome://extensions`.
- [ ] Verificar o funcionamento do Hot Reload.
- [ ] Configurar ESLint e Prettier.

**Critério de conclusão:** extensão carregando corretamente no Chrome, com interface React funcionando.

## Fase 2 — Interface e experiência do usuário

Objetivo: construir a experiência visual antes de integrar os mecanismos de tradução.

- [ ] Definir identidade visual do LinguaFlow.
- [ ] Criar layout principal do Side Panel.
- [ ] Criar navegação entre funcionalidades.
- [ ] Criar seletor de idioma de origem.
- [ ] Criar seletor de idioma de destino.
- [ ] Criar tela de tradução.
- [ ] Criar área de texto de entrada.
- [ ] Criar área de resultado.
- [ ] Criar botão para inverter idiomas.
- [ ] Criar tela de vocabulário.
- [ ] Criar tela de histórico.
- [ ] Criar tela de flashcards.
- [ ] Criar tela de progresso.
- [ ] Criar tela de configurações.
- [ ] Implementar tema claro e escuro.
- [ ] Implementar estados de carregamento, erro e vazio.
- [ ] Tornar a interface responsiva ao espaço disponível no Side Panel.

**Critério de conclusão:** todas as telas principais funcionando com dados fictícios, sem depender ainda de tradução real.

## Fase 3 — Funcionalidades da extensão Chrome

Objetivo: conectar a interface com o navegador.

- [ ] Implementar comunicação entre Side Panel e Background.
- [ ] Implementar comunicação entre Content Script e Background.
- [ ] Capturar texto selecionado em páginas.
- [ ] Criar menu de contexto para traduzir texto selecionado.
- [ ] Enviar texto selecionado para o Side Panel.
- [ ] Implementar leitura de conteúdo de páginas.
- [ ] Definir permissões mínimas necessárias no Manifest.
- [ ] Tratar páginas nas quais a extensão não pode executar Content Scripts.
- [ ] Testar em diferentes sites.

**Critério de conclusão:** conseguir selecionar um texto em qualquer página compatível e enviá-lo para a extensão.

## Fase 4 — Sistema de tradução

Objetivo: desenvolver a primeira funcionalidade realmente útil do LinguaFlow.

- [ ] Definir uma interface comum para provedores de tradução.
- [ ] Implementar serviço de tradução.
- [ ] Pesquisar modelos de tradução executáveis localmente.
- [ ] Avaliar NLLB-200.
- [ ] Avaliar TranslateGemma.
- [ ] Avaliar outras alternativas compatíveis com navegador.
- [ ] Testar traduções entre português e os cinco idiomas.
- [ ] Testar traduções entre idiomas estrangeiros.
- [ ] Comparar qualidade e velocidade.
- [ ] Implementar identificação automática do idioma, se viável.
- [ ] Implementar tradução bidirecional.
- [ ] Implementar tratamento de erros.
- [ ] Criar cache de traduções quando apropriado.
- [ ] Criar interface para carregamento e disponibilidade do modelo.

**Critério de conclusão:** traduzir textos reais sem depender de um backend próprio.

## Fase 5 — Pronúncia e leitura

Objetivo: permitir que o usuário escute e pratique os idiomas.

- [ ] Integrar SpeechSynthesis.
- [ ] Listar vozes disponíveis no navegador.
- [ ] Selecionar voz conforme o idioma.
- [ ] Reproduzir palavras individualmente.
- [ ] Reproduzir frases completas.
- [ ] Implementar controle de velocidade.
- [ ] Implementar pausa e retomada.
- [ ] Criar leitura de textos selecionados.
- [ ] Avaliar alternativas locais de reconhecimento de fala.
- [ ] Testar disponibilidade e qualidade das vozes nos diferentes idiomas.

**Critério de conclusão:** conseguir ouvir palavras e frases com a voz correspondente ao idioma selecionado.

## Fase 6 — Vocabulário, histórico e flashcards

Objetivo: transformar traduções em material de estudo.

- [ ] Definir estrutura dos dados de vocabulário.
- [ ] Implementar armazenamento com IndexedDB.
- [ ] Salvar palavras e expressões.
- [ ] Salvar tradução e idioma de origem.
- [ ] Permitir adicionar observações.
- [ ] Permitir editar palavras salvas.
- [ ] Permitir excluir palavras.
- [ ] Implementar histórico de traduções.
- [ ] Permitir pesquisar no histórico.
- [ ] Criar sistema de flashcards.
- [ ] Implementar revisão de palavras.
- [ ] Registrar acertos e erros.
- [ ] Criar sistema básico de repetição espaçada.
- [ ] Implementar estatísticas de aprendizado.

**Critério de conclusão:** o usuário consegue criar seu próprio vocabulário e revisar palavras sem perder os dados ao fechar o navegador.

## Fase 7 — Inteligência Artificial e WebGPU

Objetivo: desenvolver um tutor de idiomas executado localmente, sem depender de uma API de IA externa.

### 7.1 — Estudo e validação técnica

- [ ] Estudar funcionamento do WebGPU.
- [ ] Verificar disponibilidade de `navigator.gpu`.
- [ ] Testar WebGPU no Chrome.
- [ ] Verificar compatibilidade com a GPU e os drivers.
- [ ] Testar execução de operações básicas na GPU.
- [ ] Estudar Web Workers.
- [ ] Estudar inferência local no navegador.
- [ ] Comparar WebLLM e Transformers.js.
- [ ] Avaliar consumo de RAM e VRAM.
- [ ] Medir velocidade de inferência.

### 7.2 — Gerenciamento de modelos

- [ ] Criar sistema de seleção de modelos.
- [ ] Criar interface de download.
- [ ] Exibir progresso de download.
- [ ] Armazenar modelos em cache.
- [ ] Detectar modelos já baixados.
- [ ] Permitir excluir modelos.
- [ ] Exibir informações de espaço ocupado.
- [ ] Implementar carregamento e descarregamento.
- [ ] Tratar falhas de memória e incompatibilidade.
- [ ] Implementar alternativa de execução em WASM quando viável.

### 7.3 — Tutor inteligente

- [ ] Criar interface de conversação.
- [ ] Definir níveis de dificuldade.
- [ ] Permitir escolher o idioma da conversa.
- [ ] Implementar contexto de conversação.
- [ ] Criar instruções para o tutor atuar como professor.
- [ ] Implementar correção de erros gramaticais.
- [ ] Explicar os erros na língua nativa.
- [ ] Sugerir formas mais naturais de expressão.
- [ ] Criar exercícios a partir das conversas.
- [ ] Integrar o vocabulário salvo ao tutor.
- [ ] Permitir simulações de situações cotidianas.
- [ ] Salvar conversas localmente.

**Critério de conclusão:** conversar com um tutor de IA no navegador, com geração de respostas local e sem API externa.

## Fase 8 — Reconhecimento de fala

Objetivo: permitir que o usuário pratique conversação também por voz.

- [ ] Pesquisar modelos locais de reconhecimento de fala.
- [ ] Avaliar Whisper com Transformers.js.
- [ ] Testar reconhecimento dos idiomas suportados.
- [ ] Implementar captura de áudio mediante permissão.
- [ ] Converter áudio em texto.
- [ ] Integrar texto reconhecido ao tutor.
- [ ] Comparar fala reconhecida com a frase esperada.
- [ ] Avaliar feedback de pronúncia.
- [ ] Tratar permissões e erros de microfone.

**Critério de conclusão:** usuário consegue falar com o tutor e receber respostas e correções.

## Fase 9 — Testes, otimização e publicação

Objetivo: preparar o LinguaFlow para uso real e publicação.

- [ ] Testar funcionalidades individualmente.
- [ ] Testar comunicação entre os componentes da extensão.
- [ ] Testar persistência dos dados.
- [ ] Testar funcionamento após reiniciar o Chrome.
- [ ] Testar funcionamento offline quando os recursos estiverem disponíveis localmente.
- [ ] Otimizar consumo de memória.
- [ ] Otimizar carregamento dos modelos.
- [ ] Verificar permissões solicitadas.
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

# 5. Decisões arquiteturais importantes

### Sem backend próprio

O projeto deverá funcionar sem uma API hospedada por mim.

A extensão será responsável por executar as funcionalidades e armazenar os dados localmente.

### Separação entre interface e mecanismos de IA

A interface não deve depender diretamente de uma biblioteca específica.

Por exemplo, o sistema de tradução deve utilizar um contrato semelhante a:

```ts
export interface TranslationProvider {
  translate(
    text: string,
    source: string,
    target: string
  ): Promise<string>;
}
```

Assim, será possível trocar NLLB por TranslateGemma ou outro modelo sem precisar reescrever a interface.

### IA local

Os modelos poderão ser baixados sob demanda e armazenados em cache.

O processamento será feito no dispositivo do usuário. O primeiro download exigirá internet, e o funcionamento posterior dependerá da disponibilidade dos arquivos em cache.

### Processamento em segundo plano

Modelos de IA não devem bloquear a interface.

Sempre que necessário, utilizar Web Workers para executar operações pesadas.

### Privacidade

- Não coletar textos de páginas sem uma ação ou permissão adequada do usuário.
- Não enviar conversas ou traduções para servidores externos sem consentimento.
- Não armazenar dados desnecessários.
- Explicar claramente as permissões solicitadas.

---

# 6. Idiomas suportados

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

# 7. Registro de progresso

Use esta seção para registrar o andamento geral do projeto.

| Fase | Status |
|---|---|
| 1. Preparação | ⬜ Não iniciado |
| 2. Interface | ⬜ Não iniciado |
| 3. Chrome API | ⬜ Não iniciado |
| 4. Tradução | ⬜ Não iniciado |
| 5. Pronúncia | ⬜ Não iniciado |
| 6. Vocabulário | ⬜ Não iniciado |
| 7. IA e WebGPU | ⬜ Não iniciado |
| 8. Reconhecimento de fala | ⬜ Não iniciado |
| 9. Publicação | ⬜ Não iniciado |

## Registro de decisões e problemas

Utilize esta área para documentar decisões técnicas importantes, problemas encontrados e soluções implementadas.

### Decisões

- 

### Problemas encontrados

- 

### Próximas tarefas

- 

---

# 8. Referências técnicas

- [Chrome Extensions Documentation](https://developer.chrome.com/docs/extensions/)
- [CRXJS](https://crxjs.dev/)
- [React](https://react.dev/)
- [TypeScript](https://www.typescriptlang.org/docs/)
- [Vite](https://vite.dev/)
- [WebGPU Documentation](https://developer.mozilla.org/en-US/docs/Web/API/WebGPU_API)
- [WebLLM](https://github.com/mlc-ai/web-llm)
- [Transformers.js](https://huggingface.co/docs/transformers.js/)
- [ONNX Runtime Web](https://onnxruntime.ai/docs/get-started/with-javascript/web.html)

---

**Meta final:** criar uma extensão de aprendizado de idiomas completa, modular, privada e capaz de executar modelos de inteligência artificial diretamente no navegador, aproveitando os recursos de hardware do próprio usuário.