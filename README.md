# GTA-PC — espelho de Marvisak/VIctory

Este branch (`sync`) guarda só a automação. **O código espelhado está no branch `main`** (e nos demais branches/tags do original).

- Workflow: `.github/workflows/mirror.yml`
- Frequência: a cada 30 minutos, ou manualmente em *Actions → Espelhar Marvisak/VIctory → Run workflow*
- Só age quando há mudança: compara os refs com `git ls-remote` e, se forem iguais, termina sem baixar nada
- Quando há mudança, busca e envia apenas o que é novo (cópia mantida em cache entre execuções)
- Requer o secret `MIRROR_TOKEN` (token fine-grained com acesso só a este repositório: *Contents* e *Workflows* em Read and write)
- Os workflows vindos do original (ex.: `CI`) são desativados automaticamente, e o repositório só permite as actions `actions/cache/restore` e `actions/cache/save`, para não gastar minutos do Actions
