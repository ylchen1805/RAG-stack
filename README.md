# RAG-Stack

Using docker deploy ollama and litellm for my personal RAG.

## 1. Set up
  1.1 Install `docker`, `nvidia container toolkit`  
  1.2 Copy the `.env.example` to `.env` and change it.
```shell
cp .env.example .env
```
  1.3 Start container
```shell
docker compose up -d
```  
  1.4 Downloa Qwen
```shell
docker exec -it ollama ollama pull qwen2.5:14b
```
  1.5 TEST Ollama
```shell
curl http://localhost:11434/api/generate -d '{
  "model": "qwen2.5:14b",
  "prompt": "請用繁體中文介紹RAG"
}'
```
  1.6 TEST LiteLLM API
```shell
curl http://localhost:4000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer sk-local-123456" \
  -d '{
    "model": "qwen-local",
    "messages": [
      {"role": "user", "content": "請用繁體中文介紹RAG"}
    ]
  }'
```
