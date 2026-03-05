# HacktheFuture – Automotive Supply Chain Risk Agent

An AI-powered supply chain risk agent for automotive manufacturers. It assesses disruptions, recommends mitigation options, quantifies business impact in CAD, and helps with escalation and supplier communication.

## Features

- **Risk assessment** – Evaluates supply chain disruptions and their impact
- **Business impact (CAD)** – Revenue at risk, margin at risk, service level drop, downtime cost, SLA penalty, expedite premium
- **With vs without agent** – Compares scenarios to show revenue loss prevented, service level protection, cost optimization, and operational continuity improvement
- **Signal handling** – Processes disruption signals (delays, quality issues, etc.)
- **Mitigation options** – Suggests actions with trade-offs
- **Approval boundaries** – Indicates when human approval is required
- **Similar past cases** – References historical disruption data

## Setup

### Prerequisites

- Python 3.10+
- [Google AI API key](https://aistudio.google.com/apikey) (for Gemini)

### Installation

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/HacktheFuture.git
cd HacktheFuture

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Copy environment template and add your API key
cp .env.example multi_tool_agent/.env
# Edit multi_tool_agent/.env and set GOOGLE_API_KEY=your-api-key
```

### Running the agent

```bash
source .venv/bin/activate
export SSL_CERT_FILE=$(python -m certifi)  # Optional: for SSL on some systems
adk web
```

Then open the web UI (typically http://localhost:8000 or as shown in the terminal).

### Scripts

- **Initialize baseline data**: `python scripts/init_baseline.py`
- **Reset demo data**: `python scripts/reset_demo_data.py`

### Configuration

Edit `data/business_parameters.json` to adjust cost assumptions (selling price, margin, unit cost, SLA penalty, downtime cost, etc.) used for business impact calculations.

## Project structure

```
HacktheFuture/
├── multi_tool_agent/       # Agent definition, tools, risk & metrics engines
│   ├── agent.py
│   ├── tools.py
│   ├── risk_engine.py
│   ├── metrics_engine.py   # Revenue, margin, SLA, expedite cost calculations
│   ├── perception.py
│   └── signal_simulator.py
├── data/                   # JSON data (shipments, inventory, suppliers, etc.)
│   ├── business_parameters.json  # Cost assumptions (CAD) for impact calculations
│   └── baseline/           # Snapshot for reset_demo_data
├── scripts/                # Utility scripts
└── requirements.txt
```

## License

MIT
