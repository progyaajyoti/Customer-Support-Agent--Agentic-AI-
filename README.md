# Customer-Support-Agent-Agentic-AI

**Agentic Features:**

**Autonomous Workflows:** *Decides whether to answer, fetch data (e.g., order status), refund, or escalate based on intent and sentiment.*       
**Proactive Engagement:** *Suggests solutions before explicit requests (e.g., “I see you’re asking about delivery—here’s your tracking”).*

**Adaptability:** *Updates its knowledge base or response strategy based on user feedback or resolved tickets.*

**AI Components:**

**NLP Model:**
Use DistilBERT (quantized to 4-bit) for intent recognition (e.g., “complaint,” “query”) and sentiment analysis (e.g., “frustrated”).
Why DistilBERT? Smaller than BERT (~200MB), fits in 4GB VRAM, and performs well for dialogue tasks.
**Quantization:** Use bitsandbytes to reduce memory to ~100MB for inference.
**Reinforcement Learning:**
Implement a lightweight RL policy (e.g., Q-learning) to optimize responses (e.g., maximize resolution rate, minimize escalation).
**State:** User query, intent, sentiment.
**Action:** Respond, fetch data, escalate, refund.
**Reward:** +1 for resolved query, -1 for escalation, +0.5 for proactive suggestion.
**Knowledge Base:**
*Store common responses and policies (e.g., refund rules) in a JSON file or SQLite (lightweight, no heavy database needed).
Update dynamically based on resolved tickets.*

**Data:**

Use MultiWOZ dataset (dialogue, ~1GB) or Kaggle’s customer support tickets (~500MB) for training.
Subset to ~100MB to fit your RAM/storage constraints.
**Web Interface (Flask):**
**UI**: A chat window where users type queries and see AI responses, with a log of decisions (e.g., “Detected intent: Query → Action: Fetch tracking”).
**Frontend:**
**HTML**: Simple chat layout with input box and message display.
**CSS:** Basic styling for a clean, professional look (e.g., speech bubbles).
**JavaScript:** Auto-scroll chat and handle Enter key for sending messages.
**Backend:**
*Flask routes to receive user input, process with AI, and return responses.
Serve quantized model and RL policy locally.*
