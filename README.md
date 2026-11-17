# NASAA — Controle de produção

App web (HTML + JavaScript puro, sem build) publicado no GitHub Pages em **https://nasaa.gutgestao.com.br**, com banco no Supabase (projeto **PROJETOS**, schema **`nasaa`**). Mesmo padrão dos apps KLINIK e YAZFIT.

Substitui o web app do Google Apps Script ligado à planilha do NASAA.

## Perfis
| Perfil | Pode |
|---|---|
| admin | tudo, inclusive liberar usuários |
| pcp | novo pedido, artigos e rotas, cadastro da equipe |
| producao | tablets: iniciar, pausar, apontar, finalizar, incluir setor |

## Acesso
1. A pessoa abre o app e toca em **Criar conta** (e-mail + senha) e confirma pelo e-mail.
2. O admin libera em **Usuários**, pelo e-mail, escolhendo os perfis.

## Estrutura
```
index.html     página única (telas, estilos e lógica)
js/config.js   URL e chave pública do Supabase
CNAME          domínio nasaa.gutgestao.com.br
```
As regras ficam no banco (funções `nasaa.*` com checagem de perfil): `dados`, `sync`, `criar_pedido`, `salvar_artigo`, `salvar_funcionario`, `sessoes_filtro`, `artigo`, `eu`, `liberar_usuario`.

## Publicação
Branch `main` publicada pelo GitHub Pages a partir da raiz. DNS no Cloudflare: registro **CNAME** `nasaa` → `facsimprojetos-cloud.github.io`.
