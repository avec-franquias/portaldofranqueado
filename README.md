# Portal do Franqueado + Extrator de Leads no GitHub

Esta versão funciona sem extensão no Chrome e sem servidor 24h ligado.

## Arquitetura

- `docs/index.html`: Portal publicado pelo GitHub Pages.
- `config/queries.json`: lista de regiões/nichos monitorados.
- `collector/collect.mjs`: coleta central executada pelo GitHub Actions.
- `.github/workflows/update-leads.yml`: executa a coleta automaticamente a cada 6 horas e também permite execução manual.
- `docs/extrator-data/latest.json`: base que o Portal lê.

## Configuração no GitHub

1. Em **Settings > Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/docs`.
2. Em **Settings > Actions > General > Workflow permissions**, selecione **Read and write permissions**.
3. Edite `config/queries.json` com os nichos/cidades/bairros que deseja monitorar.
4. Abra **Actions > Atualizar leads > Run workflow** para fazer a primeira coleta.

## Como os usuários usam

Os usuários não instalam nada. Eles abrem o Portal e consultam regiões cadastradas em `config/queries.json`. A base é renovada automaticamente pelo GitHub Actions.

## Limitação

GitHub Pages é estático. A atualização ocorre automaticamente a cada 6 horas ou manualmente no GitHub. Para buscas arbitrárias instantâneas por qualquer usuário, seria necessário um pequeno backend.

## Observação operacional

A coleta depende da interface pública do Google Maps e pode exigir manutenção quando o site alterar sua estrutura.