# app/

Ovdje živi tvoja aplikacija. Placeholder (`main.py`) je minimalni FastAPI servis s `/` i `/health` endpointima — dovoljan da CI pipeline od prvog dana ima što testirati.

**Do 3. tjedna** zamijeni ga aplikacijom koju si odabrao s popisa projekata. Uvjeti:

- **3 komponente: API + baza + Redis** (worker, message queue i slično nisu uvjet),
- **`/health`** endpoint koji provjerava vezu prema bazi i Redisu,
- barem nekoliko testova koji se pokreću s `make test`.

Jezik i framework biraš sam. Ako mijenjaš jezik, prilagodi `Makefile` i CI workflow.

Svaki servis dobiva svoju podmapu kad ih bude više, npr.:

```
app/
  api/
  worker/
```

**4. tjedan:** ovdje dodaješ `Dockerfile`.
