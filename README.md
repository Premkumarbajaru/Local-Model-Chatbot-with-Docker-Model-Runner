---

# 🐳 Local Model Chatbot with Docker Model Runner

This project demonstrates how to interact with a locally running language model using [Docker Model Runner](https://docs.docker.com/genai/overview/) and OpenAI-compatible APIs. Two example scripts are included: a **streaming** version and a **non-streaming** version.

---

## 🚀 Prerequisites

* [Docker](https://www.docker.com/products/docker-desktop/) installed
* Docker Desktop with **Model Runner** support enabled

Check versions:

```bash
docker --version
docker model version
```

Enable Model Runner:

```bash
docker desktop enable model-runner --tcp 12434
```

Check runner status:

```bash
docker model status
```

---

## 📦 Model Setup

Pull the desired model:

```bash
docker model pull ai/smollm2
```

Verify model:

```bash
docker model list
docker model inspect ai/smollm2
```

Run model:

```bash
docker model run ai/smollm2 "Give me a fact about human"
```

---

## 📂 Project Structure

```
.
├── docker.py       # Basic one-time completion
├── streaming.py    # Real-time streamed completion
└── README.md
```

---

## 🧠 Scripts Overview

### 🔹 docker.py

A simple chat completion request using the model.

```bash
python docker.py
```

**Output:** One-time response from the model.

### 🔹 streaming.py

A real-time response stream (like chatGPT typing effect).

```bash
python streaming.py
```

**Output:** Printed word-by-word response streamed from the model.

---

## 🔐 Configuration

Both scripts connect to the Docker Model Runner using the local endpoint:

```python
base_url = "http://localhost:12434/engines/v1"
api_key = "docker"
```

Make sure the port `12434` is open and Docker Model Runner is enabled with:

```bash
docker desktop enable model-runner --tcp 12434
```

---

## 🛠 Additional Commands

Useful `docker model` CLI utilities:

| Command   | Description                          |
| --------- | ------------------------------------ |
| `pull`    | Download a model from Docker Hub     |
| `run`     | Execute the model with a prompt      |
| `list`    | Show available local models          |
| `logs`    | View Docker Model Runner logs        |
| `status`  | Check if the Model Runner is active  |
| `inspect` | Detailed info about a specific model |
| `rm`      | Remove a model from local system     |
| `tag`     | Add a tag to your model              |
| `push`    | Upload your own model to Docker Hub  |

---

## ✅ Example Output

> Prompt: “Share a happy story with me”

**docker.py:**

```
Once upon a time, a little girl found a stray puppy...
```

**streaming.py:**

```
Once upon a time, a little girl found a...
```

---

## 📄 License

MIT © 2025 – Prem Kumar

---
