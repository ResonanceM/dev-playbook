# AI Product Playbook: Enhetsekonomi, Latency & Evals

Att bygga AI-produkter ställer helt andra krav på produktstyrning eftersom utdata är probabilistisk och kostnaderna styrs av tokenförbrukning.

---

## 💰 Beräkning av LLM-enhetsekonomi

$$	ext{Kostnad per anrop} = (	ext{Input Tokens} 	imes 	ext{Pris}_{	ext{input}}) + (	ext{Output Tokens} 	imes 	ext{Pris}_{	ext{output}})$$

* **Strategi:** Använd modellfiltrering (Model Routing). Låt en billig och snabb modell (t.ex. Llama 3 8B eller GPT-4o-mini) hantera enklare klassificeringar och routing, och eskalera endast till tunga resonemangsmodeller (GPT-4o / Claude 3.5 Sonnet) när komplexiteten kräver det.

---

## 🛡️ AI Product Evals (Utvärdering)
Innan du skeppar en ny systemprompt eller byter modell måste du köra **Evals**:
* Bygg en testdataset med minst 100–200 typiska användarfrågor med tillhörande facit.
* Mät förändringen i träffsäkerhet (accuracy) och latens innan ändringen tillåts gå till produktion.
