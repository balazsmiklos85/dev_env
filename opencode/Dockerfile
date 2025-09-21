FROM node:latest

RUN npm install -g opencode-ai @ai-sdk/openai-compatible

USER node
RUN mkdir -p ~/.config/opencode
RUN echo '{\
  "$schema": "https://opencode.ai/config.json",\
  "provider": {\
    "ollama": {\
      "npm": "@ai-sdk/openai-compatible",\
      "name": "LM Studio",\
      "options": {\
        "baseURL": "http://192.168.0.87:1234/v1"\
      },\
      "models": {\
        "openai/gpt-oss-120b": {\
          "name": "GPT OSS 120B"\
        },\
        "qwen/qwen3-coder-30b": {\
          "name": "Qwen3 Coder 30B"\
        },\
        "mistralai/devstral-small-2505": {\
          "name": "Devstral Small"\
        }\
      }\
    }\
  }\
}' > ~/.config/opencode/opencode.json

CMD ["/usr/bin/bash"]
