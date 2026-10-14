# PEr08 — RAG-ассистент (ProxyAPI)

Учебный проект: RAG через ProxyAPI (OpenAI-совместимый провайдер).

## Стек
Python 3.11, openai 1.x, ChromaDB, SQLite, RAGAS 0.4.0, langchain 0.3.x.

## Что делает
- Загружает assistant_api/data/docs.txt → чанки (абзацы/предложения, overlap 100).
- Эмбеддинги text-embedding-3-small (1536 dim) → ChromaDB.
- Поиск top_k=3 → gpt-4o-mini → ответ.
- SQLite-кэш (api_rag_cache.db): повторные вопросы из кэша.
- RAGAS 0.4.0: Faithfulness 1.0, Context Precision 1.0 (на 5 вопросах).

## Установка
python3.11 -m venv venv
./venv/bin/pip install -r requirements.txt
Создать .env:
  OPENAI_API_KEY=<key>
  OPENAI_BASE_URL=https://api.proxyapi.ru/openai/v1
  OPENAI_API_BASE=https://api.proxyapi.ru/openai/v1

## Запуск
cd assistant_api && ../venv/bin/python app.py
Команды: exit, stats, clear.

## Оценка
cd assistant_api && ../venv/bin/python evaluate_ragas.py

## Скриншоты
session_app.txt, session_ragas.txt — в корне проекта.
