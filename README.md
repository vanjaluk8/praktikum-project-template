# Praktikum — DevOps i infrastruktura · projekt

Ovo je tvoj osobni repozitorij za cijeli semestar. Sve vježbe i projekt nadograđuju **isti repo**: počinješ s malom aplikacijom, a završavaš s potpuno automatiziranim deploymentom na Kubernetes, s monitoringom i security provjerama.

> **Aplikacija nije predmet ocjene — infrastruktura jest.** Kod aplikacije smije biti jednostavan ili generiran uz AI. Boduju se Dockerfile, pipeline, deployment, monitoring i sigurnost.

---

## Brzi start

Potrebno: Git, Docker Desktop, kubectl, kind, Helm, Argo CD CLI, Ansible, Trivy i Python 3.12. Na Windowsu sve radiš **unutar WSL2** (Ubuntu), a Docker Desktop mora imati uključenu WSL integraciju. Upute za instalaciju su u materijalima kolegija.

1. Napravi svoj repo iz ovog predloška (`Use this template` → **Private**) i dodaj nastavnika kao collaboratora.
2. Kloniraj ga i provjeri okruženje:

```bash
make check        # jesu li svi alati instalirani
make cluster-up   # podigni lokalni kind cluster
make cluster-down # ugasi ga kad završiš
```

---

## Struktura

| Mapa | Što ide unutra | Tjedan |
| --- | --- | --- |
| `app/` | tvoja multi-service aplikacija (placeholder API možeš zamijeniti) | 1–3 |
| `app/Dockerfile`, `compose.yaml` | kontejnerizacija | 4–5 |
| `.github/workflows/` | CI/CD pipeline | 6–7 |
| `infra/ansible/` | configuration management | 9 |
| `k8s/` | Kubernetes manifesti | 10 |
| `helm/` | Helm chart aplikacije | 8/11 |
| `argocd/` | Argo CD `Application` za GitOps | 11 |
| `monitoring/` | Prometheus pravila, Grafana dashboard | 12 |
| `docs/` | AI log, postmortem, bilješke | cijeli semestar |
| `kind/` | konfiguracija lokalnog clustera | 1 |
| `scripts/` | pomoćne skripte | — |

---

## Pravila rada

- **Svaki lab zadatak = jedan pull request** s labelom `lab-XX` (npr. `lab-06`). Ne mergeaj sam na `main` bez PR-a.
- Poruke commitova piši po [Conventional Commits](https://www.conventionalcommits.org/): `feat:`, `fix:`, `ci:`, `docs:`, `chore:`…
- **Checkpointi** su git tagovi: `checkpoint-1` (7. tjedan) i `checkpoint-2` (13. tjedan). Ocjenjuje se stanje taga u trenutku roka.
- **Nikad ne commitaj secrete** (lozinke, tokene, `.env`). Koristi GitHub Secrets i Kubernetes Secrets.
- **AI alati su dopušteni** — ali svaki put dopiši zapis u [`docs/ai-log.md`](docs/ai-log.md). Na obrani moraš objasniti svaku liniju koju si predao.

---

## Checklist projekta

Kopiraj u issue ili ga ažuriraj ovdje kako napreduješ.

### Checkpoint 1 (7. tjedan)
- [ ] Aplikacija s najmanje 3 komponente (npr. API + baza + cache/worker)
- [ ] `Dockerfile` s multi-stage buildom, image manji od 300 MB
- [ ] `compose.yaml` — cijeli stack se diže s `docker compose up`
- [ ] CI pipeline: lint + testovi + build imagea na svaki PR
- [ ] Push imagea u GHCR na merge u `main`
- [ ] Branch protection na `main` (obavezan PR + zeleni CI)

### Checkpoint 2 (13. tjedan)
- [ ] Ansible playbook koji priprema okruženje
- [ ] Aplikacija radi na kind clusteru (Deployments, Services, ConfigMaps, Secrets)
- [ ] Helm chart s `values.yaml` za barem dva okruženja
- [ ] Argo CD sinkronizira cluster iz ovog repozitorija (GitOps)
- [ ] Prometheus metrike + Grafana dashboard + barem jedan alert
- [ ] Trivy image scanning i secret scanning u pipelineu

### Završna predaja (15. tjedan)
- [ ] Postmortem simuliranog incidenta u [`docs/postmortem.md`](docs/postmortem.md)
- [ ] Ažuriran [`docs/ai-log.md`](docs/ai-log.md)
- [ ] Ovaj README opisuje kako pokrenuti projekt od nule
- [ ] Demo pipelinea pripremljen za obranu

---

## Moj projekt

> Ispuni u 1. tjednu.

- **Ime i prezime:**
- **Aplikacija:**
- **Komponente:**
- **Stack (jezik, baza…):**
