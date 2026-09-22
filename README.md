# RLhub

Hub pessoal que reúne minhas páginas num lugar só, publicado em
**https://laureanorenan.github.io**

## Estrutura

O hub é um único arquivo HTML, sem build e sem dependências. Um trilho de
ícones à esquerda (que vira uma doca embaixo no celular) dá acesso às páginas,
e cada uma carrega numa moldura dentro do próprio hub.

| Seção | Página | Endereço próprio |
| --- | --- | --- |
| Financeiro | Controle de Obras | `/controle-obras/` |
| Financeiro | Receitas/Despesas | `/financeiro/` |
| Investimentos | Calcular preço teto | `/analisador-de-preco/` |

Cada página continua morando no seu próprio repositório e funcionando pelo
endereço direto. O hub não move nem duplica nada — só reúne.

Como tudo fica sob o mesmo domínio (`laureanorenan.github.io`), a moldura é de
mesma origem: o login funciona igual, e o hub consegue acertar o tema da página
carregada.

## Painel

Abrindo o hub sem rota, aparece o painel: saudação, busca e um mosaico de
widgets — um por página, em tamanhos diferentes. O widget grande é o da página
marcada com `tamanho: "grande"` no `ROTAS`.

Cada widget pode mostrar um número vindo do Supabase. Para isso, registre uma
função em `PROVEDORES`, no próprio `index.html`:

```js
PROVEDORES["financeiro"] = async function (sb) {
  var r = await sb.from("fin_lancamentos").select("valor").gte("data", "2026-09-01");
  var saldo = (r.data || []).reduce(function (s, l) { return s + Number(l.valor); }, 0);
  return { valor: moeda(saldo), legenda: "saldo do mês", tom: saldo < 0 ? "neg" : "pos" };
};
```

Sem função registrada, o widget mostra só o atalho "Abrir" — nada quebra.

## Navegação

O endereço guarda a página aberta, então dá para favoritar direto:

- `https://laureanorenan.github.io/#/obras`
- `https://laureanorenan.github.io/#/financeiro`
- `https://laureanorenan.github.io/#/preco-teto`

## Identidade visual

Segue o design system RLhub: fundo `#F7F8FA`, cartões brancos com borda fina
`#E6E9EE` (sem sombra), texto grafite `#1D232B` / `#6B7280`, azul profundo
`#2457A7` só para ações e navegação, verde `#198754` para evolução, vermelho
`#B42318` para queda e âmbar `#C88719` para avisos. Manrope nos títulos e Inter
no texto e nos números (algarismos tabulares). Ganho e perda sempre com seta,
nunca só a cor. O tema escuro é derivado da mesma paleta; a escolha de tema é
compartilhada entre o hub e as páginas pela chave `pt_tema`.

## Adicionar uma página nova

No `index.html`, acrescente uma entrada em `ROTAS` com título, grupo, endereço,
ícone (`ICONES`), tamanho do widget e descrição. O trilho e o painel se montam
sozinhos a partir daí.
