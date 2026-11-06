# AI-agenter och Orchestration

När du går från enkla chattbotar till autonoma agenter krävs tillståndsstyrda arkitekturer.

---

## 🛠️ Ramverk och mönster

1. **LangGraph (Tillståndsstyrda agentgrafer):**
   * Undvik ostrukturerade agentloopar. Bygg agenter som tillståndsmaskiner (State Machines) med noder och kanter (Graph-based), där varje steg valideras och kan pausas för mänsklig granskning (Human-in-the-loop).
2. **Model Context Protocol (MCP):**
   * Använd Anthropics öppna standard **MCP** för att säkert koppla upp LLM:er mot lokala databaser, filsystem och utvecklingsverktyg utan att behöva skriva skräddarsydda API-integrationer för varje enskild tjänst.
