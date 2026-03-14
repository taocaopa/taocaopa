# AI Health Copilot Architecture

## System Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              USER INTERFACE LAYER                            │
├─────────────────────────────────────────────────────────────────────────────┤
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│  │  WhatsApp    │  │  Telegram    │  │  Mobile App  │  │  Web Portal  │   │
│  │  (Primary)   │  │  (Future)    │  │  (Future)    │  │  (Future)    │   │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘   │
└─────────┼──────────────────┼──────────────────┼──────────────────┼──────────┘
          │                  │                  │                  │
          └──────────────────┴──────────┬───────┴──────────────────┘
                                        │
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                           AI HEALTH COPILOT CORE                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │                    Natural Language Interface                        │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐              │  │
│  │  │   Speech     │  │    Text      │  │  Context     │              │  │
│  │  │ Recognition  │  │  Processing  │  │  Management  │              │  │
│  │  └──────────────┘  └──────────────┘  └──────────────┘              │  │
│  └──────────────────────────────┬─────────────────────────────────────┘  │
│                                 │                                          │
│  ┌──────────────────────────────┴─────────────────────────────────────┐  │
│  │                      Intent Recognition Engine                      │  │
│  │     (Classification → Entity Extraction → Confidence Scoring)      │  │
│  └──────────────────────────────┬─────────────────────────────────────┘  │
│                                 │                                          │
│  ┌──────────────────────────────┴─────────────────────────────────────┐  │
│  │                     Response Generation Engine                      │  │
│  │         (Template Selection → Data Fusion → Output Format)         │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                                                              │
└───────────────────────────────────┬─────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                          AGENT ORCHESTRATOR                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│     ┌─────────────────────────────────────────────────────────────────┐    │
│     │                    Task Router & Scheduler                       │    │
│     │     (Intent Matching → Agent Selection → Execution Order)        │    │
│     └──────────────────────────────┬──────────────────────────────────┘    │
│                                    │                                         │
│     ┌──────────────┬───────────────┼───────────────┬──────────────┐        │
│     │              │               │               │              │        │
│     ▼              ▼               ▼               ▼              ▼        │
│  ┌────────┐   ┌────────┐    ┌────────────┐   ┌────────┐   ┌──────────┐   │
│  │Medical │   │Nutrition│   │ Lifestyle  │   │ Sleep  │   │  Risk    │   │
│  │Knowledge│  │ Agent  │    │   Agent    │   │ Agent  │   │ Prediction│   │
│  │ Agent  │   │        │    │            │   │        │   │  Agent   │   │
│  └────┬───┘   └────┬───┘    └─────┬──────┘   └───┬────┘   └────┬─────┘   │
│       │            │              │              │             │         │
│       └────────────┴──────────────┴──────────────┴─────────────┘         │
│                                    │                                      │
│     ┌──────────────────────────────┴──────────────────────────────────┐  │
│     │                    Collaboration Results                         │  │
│     │         (Data Aggregation → Conflict Resolution → Consensus)     │  │
│     └──────────────────────────────┬──────────────────────────────────┘  │
│                                    │                                       │
└────────────────────────────────────┼───────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                      KNOWLEDGE INTELLIGENCE LAYER                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌───────────────────────────────────────────────────────────────────────┐ │
│  │                     Retrieval-Augmented Generation (RAG)               │ │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐               │ │
│  │  │   Document   │  │   Vector     │  │   Semantic   │               │ │
│  │  │   Ingestion  │  │   Database   │  │   Search     │               │ │
│  │  └──────────────┘  └──────────────┘  └──────────────┘               │ │
│  └─────────────────────────────────────────────────────────────────────┘ │
│                                                                              │
│  ┌──────────────┬───────────────┬───────────────┬──────────────────────┐  │
│  │              │               │               │                      │  │
│  ▼              ▼               ▼               ▼                      │  │
│ ┌────────┐  ┌────────┐   ┌────────────┐  ┌──────────┐                 │  │
│ │Medical │  │Clinical│   │Biomedical  │  │Personal  │                 │  │
│ │Literature│ │Guidelines│ │ Databases │  │Health    │                 │  │
│ │        │  │        │   │            │  │Records   │                 │  │
│ └────────┘  └────────┘   └────────────┘  └──────────┘                 │  │
│                                                                              │
│  Sources: PubMed, Cochrane, WHO, CDC, ClinicalTrials.gov, User Data     │  │
│                                                                              │
└───────────────────────────────────┬─────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         PERSONALIZED INSIGHTS ENGINE                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐  │
│  │                    Health Analytics & Visualization                  │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐             │  │
│  │  │   Trend      │  │    Risk      │  │  Personalized│             │  │
│  │  │   Analysis   │  │ Assessment   │  │Reports       │             │  │
│  │  └──────────────┘  └──────────────┘  └──────────────┘             │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐  │
│  │                    Recommendation Engine                             │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐             │  │
│  │  │ Evidence-Based│  │ Personalized │  │   Actionable │             │  │
│  │  │ Synthesis    │  │   Planning   │  │   Steps      │             │  │
│  │  └──────────────┘  └──────────────┘  └──────────────┘             │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                            OUTPUT & ACTIONS                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  • Personalized Health Recommendations                                      │
│  • Early Warning Alerts                                                     │
│  • Lifestyle Optimization Plans                                             │
│  • Educational Content                                                      │
│  • Progress Tracking & Visualization                                        │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

## Data Flow

```
User Query
    │
    ▼
┌─────────────────────────────────────┐
│ Intent Recognition                  │
│ "Record my weight 70kg"             │
│ ↓                                   │
│ Intent: record_weight               │
│ Entities: {weight: 70, unit: kg}    │
└──────────────┬──────────────────────┘
               │
               ▼
┌─────────────────────────────────────┐
│ Agent Orchestrator                  │
│ ↓                                   │
│ Route to: HealthDataAgent           │
└──────────────┬──────────────────────┘
               │
               ▼
┌─────────────────────────────────────┐
│ Health Data Agent                   │
│ ↓                                   │
│ Validate: 0 < weight < 500 kg ✓     │
│ Store: Append to weight_logs.json   │
└──────────────┬──────────────────────┘
               │
               ▼
┌─────────────────────────────────────┐
│ Knowledge Layer (if needed)         │
│ ↓                                   │
│ Query: BMI calculation rules        │
│ BMI = 70 / (1.75^2) = 22.86         │
└──────────────┬──────────────────────┘
               │
               ▼
┌─────────────────────────────────────┐
│ Response Generation                 │
│ ↓                                   │
│ "✅ Recorded! Weight: 70kg          │
│  BMI: 22.86 (Normal range)          │
│  Trend: -0.5kg from last week 📉"   │
└──────────────┬──────────────────────┘
               │
               ▼
           User
```

## Technology Stack

### Core Framework
- **NanoBot** - Lightweight AI Agent framework
- **Python 3.8+** - Primary language

### AI/ML
- **OpenRouter** - LLM API gateway (GPT-4, Claude, etc.)
- **LangChain** - LLM orchestration (future)
- **Sentence Transformers** - Embeddings for RAG (future)

### Data
- **JSON** - Local data storage
- **Pandas** - Data analysis
- **Matplotlib** - Visualization

### Infrastructure
- **Docker** - Containerization
- **GitHub Actions** - CI/CD
- **WhatsApp Business API** - Primary channel

## Design Principles

1. **Privacy First** - All health data stored locally
2. **Modular Design** - Skills are independent and composable
3. **Extensible** - Easy to add new health tracking modules
4. **Human-in-the-Loop** - AI assists, humans decide
5. **Evidence-Based** - Recommendations grounded in medical literature

## Security & Privacy

- 🔒 End-to-end encryption for data at rest
- 🔐 No cloud storage of personal health data
- 🛡️ Role-based access control
- 📋 HIPAA/GDPR compliance considerations

---

*Architecture Version: 1.0.0*  
*Last Updated: March 2026*
