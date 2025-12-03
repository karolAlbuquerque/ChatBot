# 🤖 Chatbot Anya Forger - Spy x Family

Projeto Final de IA Aplicada

Este projeto implementa um chatbot inteligente que simula a personalidade da **Anya Forger**, personagem do anime **Spy x Family**. O chatbot mantém uma identidade consistente, falando em terceira pessoa, usando expressões características como "Waku Waku!" e demonstrando os poderes telepáticos da personagem através de análise de padrões nas conversas.

## 📋 Sobre o Projeto

O chatbot foi desenvolvido utilizando técnicas modernas de **Inteligência Artificial** e **Processamento de Linguagem Natural (NLP)**, incluindo:

- **Modelos de Linguagem**: GPT-3.5-turbo da OpenAI
- **Engenharia de Prompts**: System prompts estruturados para manter personalidade consistente
- **Gerenciamento de Contexto**: Sistema de memória que mantém histórico de conversação
- **Análise de Padrões**: Detecção de tópicos de interesse do usuário (simulando "leitura mental")
- **Pré-processamento**: Análise de palavras-chave para reações contextuais

### Características Principais

- ✅ Personalidade consistente da Anya (fala em terceira pessoa, vocabulário infantil)
- ✅ Sistema de memória que mantém contexto das conversas
- ✅ Detecção de palavras empolgantes que ativam "Waku Waku!"
- ✅ Análise de padrões do usuário (simulando poderes telepáticos)
- ✅ Interface web moderna e intuitiva via Gradio
- ✅ Tratamento de erros mantendo a personalidade

## 🚀 Instalação

### Pré-requisitos

- Python 3.7 ou superior
- Conta na OpenAI com API key (obtenha em [https://platform.openai.com/api-keys](https://platform.openai.com/api-keys))
- Google Colab (recomendado) ou ambiente Python local

### Opção 1: Google Colab (Recomendado)

1. Acesse o Google Colab: [https://colab.research.google.com/](https://colab.research.google.com/)
2. Faça upload do arquivo `Chatbot_Anya_Forger (1).ipynb`
3. Execute as células na ordem:
   - A primeira célula instala as dependências automaticamente
   - Configure sua API key quando solicitado
   - Execute as células restantes para inicializar o chatbot

### Opção 2: Ambiente Local

1. **Clone ou baixe este repositório**

```bash
git clone https://github.com/seu-usuario/chatbot-anya-forger.git
cd chatbot-anya-forger
```

2. **Instale as dependências**

```bash
pip install -r requirements.txt
```

Ou instale manualmente:

```bash
pip install openai gradio python-dotenv tiktoken
```

3. **Configure a API Key**

No notebook ou em um arquivo `.env`, configure sua chave da OpenAI:

```python
import os
from getpass import getpass

os.environ['OPENAI_API_KEY'] = getpass('Cole sua API Key aqui: ')
```

Ou crie um arquivo `.env` na raiz do projeto:

```
OPENAI_API_KEY=sua-chave-aqui
```

## 📦 Dependências

O projeto utiliza as seguintes bibliotecas:

- **openai**: Cliente para API da OpenAI (GPT-3.5-turbo)
- **gradio**: Framework para criar interfaces web interativas
- **python-dotenv**: Gerenciamento de variáveis de ambiente (opcional)
- **tiktoken**: Tokenização de texto (usado internamente pela OpenAI)

Todas as dependências estão listadas no arquivo `requirements.txt`.

## 🎮 Como Usar

### Executando o Notebook

1. Abra o arquivo `Chatbot_Anya_Forger (1).ipynb` no Google Colab ou Jupyter Notebook
2. Execute todas as células na ordem
3. Quando a interface Gradio abrir, você verá:
   - Um campo de texto para digitar mensagens
   - Um botão "Enviar ✨" para enviar mensagens
   - Um botão "🔄 Resetar Conversa" para limpar o histórico
   - O histórico de conversa será exibido acima

### Exemplos de Uso

#### Exemplo 1: Saudação Básica
```
Você: Olá Anya! Como você está?
Anya: Anya está muito bem, obrigada! Anya acabou de comer alguns amendoins, hihi. Como você está? Waku Waku!
```

#### Exemplo 2: Tópico Empolgante
```
Você: Anya, eu aprendi algo novo sobre programação hoje!
Anya: Waku Waku! Anya quer saber o que o senhor aprendeu! Anya também quer aprender coisas novas!
```

#### Exemplo 3: Múltiplas Interações (Demonstração de Memória)
```
Você: Qual é seu anime favorito?
Anya: Anya gosta muito de Spy x Family! É o anime da Anya!

Você: Por que você gosta tanto?
Anya: Porque tem o Papai Loid e a Mamãe Yor! E a Anya também está lá! Waku Waku!
```

#### Exemplo 4: "Leitura Mental" (Análise de Padrões)
Após várias perguntas sobre programação:
```
Anya: Anya leu a mente do senhor! O senhor gosta muito de fazer código, né?
```

## 🏗️ Arquitetura do Projeto

### Componentes Principais

1. **Sistema de Prompts (`ANYA_SYSTEM_PROMPT`)**
   - Define as regras fundamentais da personalidade da Anya
   - Garante consistência comportamental
   - Inclui características específicas (terceira pessoa, vocabulário infantil, etc.)

2. **Classe `ConversationMemory`**
   - Gerencia o histórico de conversação (últimas 10 interações)
   - Analisa padrões do usuário para detectar tópicos de interesse
   - Implementa o sistema de "leitura mental"

3. **Função `detect_excitement_triggers()`**
   - Identifica palavras-chave que devem gerar reações empolgadas
   - Ativa respostas com "Waku Waku!" quando apropriado

4. **Classe `AnyaChatbot`**
   - Orquestra todos os componentes
   - Gerencia comunicação com API da OpenAI
   - Integra memória, prompts e detecção de emoções

5. **Interface Gradio**
   - Interface web moderna e responsiva
   - Facilita interação e demonstração do projeto

### Fluxo de Funcionamento

```
Usuário envia mensagem
    ↓
Pré-processamento (detecção de excitement, análise de padrões)
    ↓
Construção de contexto (histórico + prompts dinâmicos)
    ↓
Requisição à API OpenAI (GPT-3.5-turbo)
    ↓
Processamento da resposta
    ↓
Atualização da memória
    ↓
Exibição da resposta na interface
```

## 🔧 Configurações Técnicas

### Parâmetros do Modelo

- **Modelo**: `gpt-3.5-turbo`
- **Temperature**: `0.8` (balanceamento entre criatividade e coerência)
- **Max Tokens**: `300` (respostas concisas, adequadas ao personagem)
- **Histórico**: Últimas 10 interações mantidas em memória

### Personalização

Você pode ajustar os parâmetros na classe `AnyaChatbot`:

```python
chatbot = AnyaChatbot(
    model="gpt-3.5-turbo",  # Pode usar "gpt-4" para melhor qualidade (mais caro)
    api_key="sua-chave"
)
```

E ajustar o histórico máximo:

```python
chatbot.memory.max_history = 15  # Aumentar histórico (mais tokens = mais custo)
```

## 📚 Técnicas de IA Aplicadas

### 1. Processamento de Linguagem Natural (NLP)
- Análise de texto e detecção de palavras-chave
- Normalização de entrada (lowercase para comparações)
- Análise de padrões e tópicos

### 2. Modelos de Linguagem
- Uso de Large Language Model (LLM) - GPT-3.5-turbo
- Geração de texto condicionada a personalidade específica
- Fine-tuning comportamental via prompts

### 3. Engenharia de Prompts
- System prompts estruturados com regras explícitas
- Prompts dinâmicos baseados em contexto
- Ajuste fino de parâmetros (temperature, max_tokens)

### 4. Gerenciamento de Contexto
- Manutenção de histórico de conversação
- Seleção de contexto relevante
- Otimização de tokens para controle de custos

### 5. Análise de Padrões
- Detecção de tópicos de interesse do usuário
- Análise comportamental para personalização
- Sistema de insights baseado em frequência de palavras

## 🐛 Solução de Problemas

### Erro: "API key não encontrada!"
- **Solução**: Certifique-se de configurar a variável de ambiente `OPENAI_API_KEY` antes de inicializar o chatbot

### Erro: "Rate limit exceeded"
- **Solução**: Você atingiu o limite de requisições da API. Aguarde alguns minutos ou verifique seu plano na OpenAI

### Interface Gradio não abre
- **Solução**: Verifique se a porta está disponível. No Colab, o link público é gerado automaticamente

### Respostas não mantêm a personalidade
- **Solução**: Verifique se o `ANYA_SYSTEM_PROMPT` está sendo incluído corretamente. O sistema prompt é essencial para manter a personalidade

## 📝 Estrutura do Projeto

```
ChatBot/
│
├── Chatbot_Anya_Forger (1).ipynb    # Notebook principal com todo o código
├── README.md                         # Este arquivo
├── requirements.txt                  # Dependências do projeto
├── GUIA_APRESENTACAO_PROFESSOR.md   # Guia para apresentação
└── ANALISE_CONFORMIDADE_PROJETO.md  # Análise de conformidade
```

## 🎯 Funcionalidades Implementadas

- ✅ Manutenção de personalidade consistente
- ✅ Sistema de memória e contexto
- ✅ Reações contextuais (Waku Waku!)
- ✅ Análise de padrões do usuário (leitura mental)
- ✅ Interface web interativa
- ✅ Tratamento de erros
- ✅ Reset de conversa

## 🔮 Possíveis Melhorias Futuras

- [ ] Integração com banco de dados para memória persistente
- [ ] Sistema de sentimentos mais sofisticado
- [ ] Adição de mais personagens ou modos de interação
- [ ] Fine-tuning de modelo próprio (se recursos permitirem)
- [ ] Cache de respostas similares para otimização de custos
- [ ] Exportação de conversas em diferentes formatos

## 👥 Autores

Desenvolvido como projeto final da disciplina de **IA Aplicada**.

## 📄 Licença

Este projeto é desenvolvido para fins educacionais.

## 🙏 Agradecimentos

- OpenAI pela API GPT-3.5-turbo
- Gradio pela framework de interface
- Criadores do anime Spy x Family pela inspiração

## 📞 Contato

Para dúvidas ou sugestões sobre o projeto, abra uma issue no repositório.

---

**Waku Waku! Anya está pronta para conversar!** 🥜✨

