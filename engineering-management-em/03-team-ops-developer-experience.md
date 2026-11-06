# Team Ops & Developer Experience (DevEx) med DORA-mått

För att mäta hur väl ett engineering-team presterar i världsklass använder vi industristandarden DORA (DevOps Research and Assessment).

---

## 🎯 De 4 DORA-måtten för elit-team

| Mått | Elit-nivå (Mål) | Hur vi uppnår det |
| :--- | :--- | :--- |
| **Deployment Frequency** | Flera gånger per dag | Robust CI/CD-pipeline, trunk-based development |
| **Lead Time for Changes** | $< 1	ext{ timme}$ (från commit till prod) | Små pull requests ($< 250	ext{ rader}$), automatiserade tester |
| **Change Failure Rate** | $0\% - 15\%$ | Staging-miljöer som speglar produktion, automatiska integrationstester |
| **Mean Time to Restore (MTTR)**| $< 1	ext{ timme}$ | Automatiska rullningar bakåt, feature flags för omedelbar avstängning |
