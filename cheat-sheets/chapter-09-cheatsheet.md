# Chapter 9 Cheat Sheet: GUIs, APIs, and Deployment

## Tool Selection Matrix
| Need | Best Tool | Why |
|---|---|---|
| One-off exploratory check | Jupyter Notebook | No deployment, fastest iteration, for the builder only |
| Quick shareable model demo | Gradio (`gr.Interface` / `gr.Blocks`) | Built-in Image/Text/Audio components, minimal code, shareable link |
| Internal multi-page dashboard | Streamlit | Sidebars, charts, widgets, session state, layout control |
| Production, authenticated, scaled | FastAPI + Docker | Async, Pydantic validation, OpenAPI docs, portable container |

## Gradio vs Streamlit
| Feature | Gradio | Streamlit |
|---|---|---|
| Best for | Single model input→output demo | Multi-page data app / dashboard |
| Core object | `gr.Interface`, `gr.Blocks` | `st.sidebar`, `st.session_state` |
| Sharing | `share=True` for temp public link | Deploy to Streamlit Cloud or server |
| Exam trigger words | "quick demo", "drag-and-drop" | "dashboard", "filters", "internal tool" |

## FastAPI Inference Endpoint Pattern
```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class PredictRequest(BaseModel):
    features: list[float]

@app.post("/predict")
def predict(request: PredictRequest):
    result = model.predict(request.features)
    return {"prediction": result}
```
- Use **POST**, not GET, for any endpoint accepting a payload.
- Pydantic model = automatic validation + auto-generated docs at `/docs`.

## Docker Essentials for AI Deployment
| Do | Don't |
|---|---|
| Pin base image version: `FROM python:3.11.8-slim` | Use `FROM python:latest` |
| Pin dependency versions in `requirements.txt` | Install deps via SSH after container runs |
| Copy only what's needed (`COPY requirements.txt .` first for layer caching) | Bake secrets/API keys into the image |
| One process per container (serve the FastAPI app) | Mix unrelated services in one container |

**Docker's role:** packages code + dependencies + runtime into one reproducible, portable image. It does not train models and does not replace the GUI/API layer — it hosts them.

## Basic MLOps Checklist
- **Versioning:** tag deployed model artifacts (v1.2, v1.3) — tracks *what* is live.
- **Monitoring:** track latency, prediction distribution, and drift — tracks *how it's performing* live.
- **Logging:** store input/output pairs for later audit and retraining.

## UX Considerations for AI Products
- **Latency feedback:** spinner/progress bar/streaming tokens during inference — never leave users waiting silently.
- **Error states:** clearly show failures, low-confidence results, or out-of-scope inputs.
- **Explainability:** surface confidence scores, sources, or reasoning for non-technical trust.

## Communicating to Non-Technical Stakeholders
- Lead with the business outcome, not the architecture.
- Always state model limitations (accuracy range, failure modes) alongside results.
- Avoid jargon like "inference latency" — say "response time."

## Exam Traps
- Picking Docker/Kubernetes for a one-off internal demo (overkill).
- Using GET instead of POST for a payload-carrying inference endpoint.
- Using `latest` tag in Dockerfiles, breaking reproducibility.
- Confusing Gradio (demo) with Streamlit (dashboard) use cases.
