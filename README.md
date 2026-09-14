# viagens-no-tempo

A collection of static microsites ("viagens no tempo" / time-travel exhibits) built on top of [Arquivo.pt](https://arquivo.pt) web archive content. Each microsite showcases the historical evolution of a specific website, institution, or theme using pages preserved by Arquivo.pt.

## Structure

Each top-level directory is a self-contained, independently deployable microsite:

```
<microsite>/
  index.html
  styles.css
  fonts/
  <images and other assets>
```

Current microsites include:

| Directory | Microsite |
|---|---|
| `25anosmctes` | 25 anos do MCTES |
| `30anospublico` | Viagem no tempo com o PÚBLICO |
| `50anos25abril` | Memórias do 25 de Abril na Internet |
| `alentejo` | Alentejo na Internet |
| `apimprensa` | Associação Portuguesa de Imprensa |
| `bad50anos` | Website da BAD |
| `bon20anos` | Comemorações do V Centenário da Primeira Circum-Navegação |
| `ccb30anos` | CCB 30 anos |
| `ee2019` | European Elections 2019 |
| `feiradolivro` | Feira do Livro de Lisboa |
| `festivaisdearte` | Festivais e eventos de arte |
| `geocities` | Geocities |
| `indielisboa20anos` | IndieLisboa 20 Anos |
| `internetmemory` | Internet Memory |
| `israblog` | — |
| `jornadasfccn` | Jornadas FCCN |
| `magalhaes500` | — |
| `novasbe` | NOVA School of Business & Economics |
| `presidentes` | Presidentes da República |
| `radiocomercial` | Rádio Comercial: 40 anos |
| `resawdev` | Resawdev |

There is no build step or dependency manager — pages are plain HTML/CSS/JS served as-is.

## Adding a new microsite

1. Create a new top-level directory named after the microsite.
2. Add `index.html`, `styles.css`, and any assets it needs (each microsite bundles its own copy of fonts/images rather than sharing a common asset pool).
3. Add an Apache alias for the new directory in `arquivo-operation` (`infrastructure-commons/group_vars/all/all.yml`, `httpd_arquivo_viagens_directories`) so it's served under `arquivo.pt/viagens-no-tempo/<microsite>`.

## Branches

- `master` — deployed to production.
- `development` — deployed to dev/stage environments for testing before merging to `master`.

## Deployment

This repository is deployed via a plain `git checkout` (no Docker image, no build artifact) by the [`arquivo-operation`](https://github.com/arquivo/arquivo-operation) role `roles/viagens-no-tempo`, as a dependency of the `broker_server` role. The deployed branch is controlled by the `viagens_no_tempo_version` variable (`HEAD` in production, `development` in dev/stage).

## License

GPL-3.0 — see [LICENSE](LICENSE).
