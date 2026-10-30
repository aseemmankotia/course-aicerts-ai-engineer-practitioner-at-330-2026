## Chapter 9: Building and Shipping AI Products: GUIs, APIs, and Deployment — Practice Questions

**Q1.** A data science team needs to show a working demo of their image classification model to business stakeholders in a meeting tomorrow. The demo needs drag-and-drop image upload, no authentication, and must be built in under 2 hours. Which approach BEST meets these requirements?

A) Build a FastAPI endpoint and demonstrate it using curl commands
B) Create a Gradio interface with an Image input component using gr.Interface
C) Containerize the model with Docker and deploy it to Kubernetes
D) Write a Jupyter notebook with print statements showing predictions

<details>
<summary>Answer</summary>

**Correct: B**

Gradio is purpose-built for rapid demo UIs with built-in components like Image, minimal code, and a shareable link — fits the 2-hour, no-auth constraint perfectly.

**Why the others are wrong:**
- FastAPI + curl produces no GUI, unsuitable for a stakeholder meeting
- Docker + Kubernetes is massive overkill for a single internal demo and blows past the 2-hour timeline
- A notebook with print statements isn't an interactive GUI and reads poorly to non-technical stakeholders

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** An AI startup's model needs to serve 500 requests/second with authentication, rate limiting, and a documented contract that other engineering teams can integrate against. Which solution BEST meets these requirements?

A) A FastAPI application with Pydantic request/response models, containerized with Docker
B) A Gradio app launched with share=True for public access
C) A Streamlit dashboard using session state
D) A Jupyter notebook exposed via ngrok

<details>
<summary>Answer</summary>

**Correct: A**

FastAPI provides async handling, automatic OpenAPI docs, and Pydantic validation for a clear integration contract; Docker makes the deployment reproducible and scalable.

**Why the others are wrong:**
- Gradio with share=True is a prototyping convenience, not built for authenticated high-throughput traffic
- Streamlit is designed for dashboards and internal tools, not a documented high-throughput API contract
- A notebook exposed via ngrok is a demo hack, not a production-grade deployment

</details>

---

**Q3.** A marketing analytics team wants an internal multi-page tool with sidebar filters, charts, and a text box for querying an LLM, used daily by 10 non-technical analysts. Which tool is BEST suited?

A) Streamlit
B) Gradio Blocks
C) Raw FastAPI with HTML templates
D) A Postman collection

<details>
<summary>Answer</summary>

**Correct: A**

Streamlit excels at building multi-page dashboards with sidebars, widgets, and charts for internal analytics tools with minimal front-end effort.

**Why the others are wrong:**
- Gradio Blocks is better suited to single-model input/output demos rather than full multi-page dashboards
- Raw FastAPI with HTML templates requires significant extra front-end work to build sidebars and charts
- Postman is an API testing tool, not an end-user GUI

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Which statement correctly differentiates Gradio from Streamlit, as tested on the exam?

A) Gradio is for multi-page data dashboards; Streamlit is only for ML model demos
B) Both tools are functionally identical and the exam treats them interchangeably
C) Gradio requires Docker to run while Streamlit does not
D) Gradio is optimized for quick ML model input/output interfaces (e.g., gr.Interface); Streamlit is optimized for broader data app dashboards with layout control and session state

<details>
<summary>Answer</summary>

**Correct: D**

This is the exact use-case split the exam tests: Gradio for rapid model demos, Streamlit for richer dashboard-style apps.

**Why the others are wrong:**
- This reverses the actual use cases of the two tools
- The exam explicitly tests the use-case difference between them, so they are not interchangeable
- Neither tool requires Docker to run as a plain Python app; Docker is an optional deployment layer for both

</details>

---

**Q5.** What is Docker's PRIMARY role in AI model deployment, as tested on the exam?

A) It trains machine learning models faster using automatic GPU acceleration
B) It replaces the need for a FastAPI or Gradio interface
C) It packages the model, dependencies, and runtime environment into a reproducible, portable container image
D) It automatically version-controls model weights

<details>
<summary>Answer</summary>

**Correct: C**

Docker's core purpose is packaging code, dependencies, and runtime into one portable, reproducible container image for consistent deployment.

**Why the others are wrong:**
- Docker does not accelerate model training by itself
- Docker is a packaging/runtime layer that houses a FastAPI or Gradio app, not a replacement for either
- Model weight versioning is handled by MLOps/model registry tools, not Docker itself

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** You are wrapping a trained model in a FastAPI inference endpoint. Which code correctly defines a POST endpoint that accepts a validated JSON request body and returns a prediction?

A) @app.get("/predict")
def predict(data: dict):
    return model.predict(data)
B) def predict(request):
    return model.predict(request)
C) @app.post("/predict")
def predict(request: PredictRequest):
    result = model.predict(request.features)
    return {"prediction": result}
D) @app.post("/predict")
async model.predict(request):
    return result

<details>
<summary>Answer</summary>

**Correct: C**

Uses the @app.post decorator, a Pydantic model (PredictRequest) for validated JSON input, valid function syntax, and returns a JSON-serializable dict.

**Why the others are wrong:**
- GET is the wrong HTTP verb for sending a prediction payload, and using a raw dict skips validation
- There is no FastAPI decorator, so this function is never registered as a route
- This is invalid Python syntax — 'async model.predict(request)' is not a valid function definition

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which Dockerfile practice is MOST important for ensuring reproducible AI deployments, as emphasized on the exam?

A) Using the `latest` tag for base images to always get the newest updates
B) Installing dependencies inside the running container after deployment via SSH
C) Excluding a requirements.txt file to reduce image size
D) Pinning exact versions of the base image and all dependencies (e.g., python:3.11.8-slim, pinned requirements.txt)

<details>
<summary>Answer</summary>

**Correct: D**

Pinning exact base image and dependency versions guarantees the same environment on every build, which is the core of reproducibility.

**Why the others are wrong:**
- The `latest` tag causes non-deterministic builds over time, breaking reproducibility
- SSH-ing into a running container to install dependencies defeats the purpose of a reproducible, immutable image
- Excluding requirements.txt means dependencies are undeclared and not reproducible

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** In basic MLOps practice, what is the key difference between model versioning and prediction monitoring?

A) They are the same process performed at different times in the pipeline
B) Model versioning tracks which trained model artifact is deployed (e.g., v1.2, v1.3); monitoring tracks live prediction quality, latency, and drift after deployment
C) Model versioning only applies to Docker images, never to model weights
D) Monitoring replaces the need for versioning entirely

<details>
<summary>Answer</summary>

**Correct: B**

Versioning answers 'which model artifact is live,' while monitoring answers 'how is that live model performing right now' — two distinct, complementary MLOps practices.

**Why the others are wrong:**
- They are distinct processes that serve different purposes, not interchangeable
- Versioning applies to the model artifact/weights themselves, not just Docker images
- Monitoring and versioning are complementary; neither substitutes for the other

</details>

---

