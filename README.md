# Speech Recognition API 🎙️

API robusta de reconhecimento de fala desenvolvida com Java e Spring Boot, capaz de transcrever áudios em texto utilizando serviços de inteligência artificial de ponta.

## 📝 Descrição do Projeto

Esta API foi projetada para facilitar a conversão de arquivos de áudio em texto (Speech-to-Text). Ela atua como um middleware inteligente que recebe arquivos multimídia, processa-os através de integrações com APIs externas (como OpenAI Whisper ou Google Speech-to-Text) e retorna a transcrição textual de forma estruturada.

É ideal para sistemas de legendagem automática, análise de chamadas, assistentes virtuais ou qualquer aplicação que necessite processar voz.

---

## 🚀 Tecnologias Utilizadas

- **Java 17+**: Linguagem base para o desenvolvimento.
- **Spring Boot 3**: Framework para criação da API REST.
- **Spring Web**: Para gerenciamento de endpoints.
- **OpenAI Whisper API / Google Speech-to-Text**: Motores de transcrição.
- **Maven**: Gerenciador de dependências.
- **Lombok**: Para redução de código boilerplate.
- **JUnit 5**: Para testes automatizados.

---

## ⚙️ Como funciona a API

O fluxo de processamento segue os passos descritos abaixo:

1. **Recebimento**: O cliente envia um arquivo de áudio via requisição POST `multipart/form-data`.
2. **Validação**: A API valida o formato e tamanho do arquivo.
3. **Processamento**: O arquivo é enviado para o serviço de Speech-to-Text configurado.
4. **Retorno**: O texto transcrito é retornado ao cliente em formato JSON.

![Fluxo de Funcionamento](https://raw.githubusercontent.com/visgl/react-map-gl/master/docs/public/logo.png)
*(Representação visual do fluxo: Áudio → API → Texto)*

---

## 📂 Estrutura do Projeto

A organização das pastas segue as melhores práticas do Spring Boot:

```text
src/main/java/com/exemplo/speechapi/
├── controller/     # Endpoints da API (Ex: SpeechController)
├── service/        # Lógica de negócio e integração com APIs externas
├── model/          # DTOs (Data Transfer Objects) e entidades
├── config/         # Configurações de Bean e segurança
└── exception/      # Tratamento global de erros
```

---

## 🛠️ Como rodar o projeto localmente

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/seu-usuario/speech-recognition-api.git
   cd speech-recognition-api
   ```

2. **Instale as dependências:**
   ```bash
   mvn clean install
   ```

3. **Inicie a aplicação:**
   ```bash
   mvn spring-boot:run
   ```
   A API estará disponível em `http://localhost:8080`.

---

## 🔑 Configurações Necessárias

Para que a API funcione corretamente, você deve configurar as variáveis de ambiente ou o arquivo `application.yml` com suas chaves de API:

```properties
# Exemplo de application.properties
SPEECH_API_KEY=sua_chave_aqui
SPEECH_PROVIDER=openai # ou google
```

Ou via terminal:
```bash
export SPEECH_API_KEY='seu_token_aqui'
```

---

## 🧪 Como testar a API

Você pode testar utilizando o **Postman**, **Insomnia** ou via **cURL**.

### Exemplo com cURL:

```bash
curl --location 'http://localhost:8080/api/v1/transcribe' \
--header 'Authorization: Bearer seu_token' \
--form 'file=@"/caminho/para/seu/audio.mp3"'
```

---

## 📦 Exemplo de Requisição e Resposta

### Requisição
**POST** `/api/v1/transcribe`
**Body**: `multipart/form-data` (chave `file`)

### Resposta (JSON)
```json
{
  "status": "success",
  "transcription": "Olá, este é um exemplo de reconhecimento de fala utilizando Spring Boot.",
  "duration": 4.5,
  "language": "pt-BR"
}
```

---

## ⚠️ Tratamento de Erros

A API utiliza códigos de status HTTP semânticos para indicar o resultado das operações:

| Código | Descrição |
| :--- | :--- |
| `200` | Sucesso na transcrição. |
| `400` | Arquivo inválido ou formato não suportado. |
| `401` | Chave de API ausente ou inválida. |
| `500` | Erro interno ao processar o áudio. |

Exemplo de erro:
```json
{
  "error": "UNSUPPORTED_FORMAT",
  "message": "O formato do arquivo enviado não é suportado. Use .mp3 ou .wav"
}
```

---

##  Melhorias Futuras

- [ ] Implementar suporte para múltiplos idiomas simultâneos.
- [ ] Adicionar persistência em banco de dados para histórico de transcrições.
- [ ] Criar interface web (Frontend) para upload de arquivos.
- [ ] Implementar processamento assíncrono para arquivos longos usando Filas (RabbitMQ/Kafka).

---
Desenvolvido com ❤️ por Kensyto
