# Plan vježbi

Što radimo svaki tjedan i što ti predaješ. Kako se predaje i boduje piše u [`ocekivanja.md`](ocekivanja.md), a predavanja (teorija) po tjednima u [silabusu](silabus.md#4-sadržaj-kolegija).

Na vježbama nastavnik uživo gradi istu stvar na oglednoj aplikaciji `praktikum-demo-app` (URL shortener). Stanje nakon svake vježbe označeno je tagom `week-XX`, pa ako si izostao ili zapeo, pogledaj točno ono što smo napravili na satu — naredbe su u [git šalabahteru](git-cheatsheet.md#7-ogledna-aplikacija-praktikum-demo-app).

| Tj. | Tema | Gdje u tvom repou | Predaja | Primjer u demo-appu |
| --- | --- | --- | --- | --- |
| 1 | [Uvod u DevOps](#1-tjedan--uvod-u-devops) | [`kind/`](../kind/), [`scripts/`](../scripts/) | setup | `week-01` |
| 2 | [Linux za ops](#2-tjedan--linux-za-ops) | [`scripts/`](../scripts/) | `lab-02` | `week-02` |
| 3 | [Git i suradnja](#3-tjedan--git-i-suradnja) | [`app/`](../app/) | `lab-03` | `week-03` |
| 4 | [Kontejneri I](#4-tjedan--kontejneri-i) | [`app/`](../app/) | `lab-04` | `week-04` |
| 5 | [Kontejneri II](#5-tjedan--kontejneri-ii) | root (`compose.yaml`) | `lab-05` | `week-05` |
| 6 | [Continuous Integration](#6-tjedan--continuous-integration) | [`.github/workflows/`](../.github/workflows/) | `lab-06` | `week-06` |
| 7 | [Continuous Delivery](#7-tjedan--continuous-delivery) | [`.github/workflows/`](../.github/workflows/) | `lab-07` + `checkpoint-1` | `week-07` |
| 8 | [Infrastructure as Code](#8-tjedan--infrastructure-as-code) | `infra/` | `lab-08` | `week-08` |
| 9 | [Configuration management](#9-tjedan--configuration-management) | [`infra/ansible/`](../infra/ansible/) | `lab-09` | `week-09` |
| 10 | [Kubernetes I](#10-tjedan--kubernetes-i) | [`k8s/`](../k8s/) | `lab-10` | `week-10` |
| 11 | [Kubernetes II](#11-tjedan--kubernetes-ii) | [`helm/`](../helm/), [`argocd/`](../argocd/) | `lab-11` | `week-11` |
| 12 | [Observability](#12-tjedan--observability) | [`monitoring/`](../monitoring/), [`app/`](../app/) | `lab-12` | `week-12` |
| 13 | [DevSecOps](#13-tjedan--devsecops) | [`.github/workflows/`](../.github/workflows/) | `lab-13` + `checkpoint-2` | `week-13` |
| 14 | [AI u DevOps praksi](#14-tjedan--ai-u-devops-praksi) | [`docs/`](./) | `lab-14` | `week-14` |
| 15 | [Obrane](#15-tjedan--obrane) | cijeli repo | obrana | `final` |

Svaki lab je pull request s labelom `lab-XX`, **do početka sljedećeg termina**. Checkpointi su tagovi `checkpoint-1` (7. tjedan) i `checkpoint-2` (13. tjedan) na tvom repou; što se na njima ocjenjuje piše u checklisti u [`README.md`](../README.md#checklist-projekta).

---

### 1. tjedan — Uvod u DevOps

- **Na vježbama:** instalacija WSL2 i alata, repo iz predloška, `make check`, `make cluster-up`; pregled kako će projekt izgledati na kraju semestra.
- **Materijali:** [`kind/README.md`](../kind/README.md) — konfiguracija lokalnog clustera objašnjena linija po liniju i česti problemi; [`github-education.md`](github-education.md); [`git-cheatsheet.md`](git-cheatsheet.md#1-jednokratno-postavljanje-1-tjedan).
- **Zadatak:** setup checklist (ne boduje se, ali bez njega ne možeš predati nijedan lab):
  - [ ] privatni repo `praktikum-<prezime>` iz predloška, nastavnik dodan kao collaborator, poveznica predana na e-učenju
  - [ ] `make check` prolazi i `make cluster-up` diže cluster
  - [ ] ispunjena sekcija **Moj projekt** u [`README.md`](../README.md#moj-projekt)

### 2. tjedan — Linux za ops

- **Na vježbama:** bash skripta koja provjerava `/health` svih servisa i javlja grešku; cron; troubleshooting servisa kroz logove.
- **Lekcija:** [`week-02-healthcheck.md`](week-02-healthcheck.md).
- **Zadatak `lab-02`:** vlastita bash skripta za automatizaciju u `scripts/`.
- **Rok za odabir aplikacije** s [popisa projekata](popis-projekata.md) je kraj ovog tjedna.

### 3. tjedan — Git i suradnja

- **Na vježbama:** placeholder API zamjenjujemo pravom aplikacijom preko grane i pull requesta; code review i branch protection na `main`.
- **Zadatak `lab-03`:** tvoja aplikacija (API + baza + Redis), `/health` koji provjerava obje veze, testovi, branch protection.

### 4. tjedan — Kontejneri I

- **Na vježbama:** Dockerfile za API — prvo naivni, pa multi-stage i non-root; usporedba veličine imagea.
- **Zadatak `lab-04`:** `app/Dockerfile` s imageom manjim od 300 MB koji ne radi kao root.

### 5. tjedan — Kontejneri II

- **Na vježbama:** `compose.yaml` za cijeli stack — healthcheck, `depends_on`, volumeni, `.env`.
- **Zadatak `lab-05`:** cijeli stack se diže s `docker compose up`.

### 6. tjedan — Continuous Integration

- **Na vježbama:** GitHub Actions — lint, testovi, build imagea; namjerno slomljen test da se vidi crveni pipeline.
- **Gdje:** [`.github/workflows/ci.yml`](../.github/workflows/ci.yml).
- **Zadatak `lab-06`:** build imagea u CI-ju na svaki PR. Od ovog tjedna PR mora imati zeleni CI.

### 7. tjedan — Continuous Delivery

- **Na vježbama:** push imagea u GHCR na merge u `main`, tagovi `sha` i `latest`, `permissions`.
- **Zadatak `lab-07`:** push u GHCR + tag **`checkpoint-1`** na svom repou.

### 8. tjedan — Infrastructure as Code

- Sadržaj će biti objavljen naknadno (Terraform/OpenTofu ili Helm).
- **Zadatak `lab-08`.**

### 9. tjedan — Configuration management

- **Na vježbama:** Ansible playbook koji instalira ovisnosti i diže stack; drugo pokretanje daje `changed=0`.
- **Zadatak `lab-09`:** idempotentan playbook u `infra/ansible/`.

### 10. tjedan — Kubernetes I

- **Na vježbama:** manifesti — Deployment, Service, ConfigMap, Secret, probe, resources; debugging s `kubectl describe` i `kubectl logs`.
- **Zadatak `lab-10`:** aplikacija radi na kind clusteru.

### 11. tjedan — Kubernetes II

- **Na vježbama:** Helm chart iz manifesta, Argo CD `Application`; commit u `helm/` i automatski sync; ručna izmjena na clusteru kao primjer drifta.
- **Zadatak `lab-11`:** Helm chart + Argo CD GitOps. Ingress koristi portove iz [`kind/kind-config.yaml`](../kind/kind-config.yaml).

### 12. tjedan — Observability

- **Na vježbama:** `/metrics` u API-ju, Prometheus, Grafana dashboard, alert na error rate; simulirani val 500-ica.
- **Zadatak `lab-12`:** dashboard, alert i zapisan SLO.

### 13. tjedan — DevSecOps

- **Na vježbama:** Trivy i gitleaks u pipelineu; namjerno ranjiv base image i procurjeli token da pipeline padne.
- **Zadatak `lab-13`:** security u pipelineu + tag **`checkpoint-2`** na svom repou.

### 14. tjedan — AI u DevOps praksi

- **Na vježbama:** simulirani incident (npr. Redis pada), troubleshooting uz AI uživo, zajedno pišemo postmortem.
- **Zadatak `lab-14`:** postmortem incidenta na svojoj aplikaciji u [`postmortem.md`](postmortem.md).

### 15. tjedan — Obrane

- Završna predaja dan prije obrana i obrana od ~15 minuta: demo pipelinea od commita do deploya, pitanja o tvom kodu i iz AI loga. Detalji u [`ocekivanja.md`](ocekivanja.md#5-obrana).
