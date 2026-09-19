# RLhub

Hub pessoal que reúne minhas páginas num lugar só, publicado em
**https://laureanorenan.github.io**

## Estrutura

O hub é um único arquivo HTML, sem build e sem dependências. O menu lateral
carrega cada página numa moldura dentro do próprio hub.

| Seção | Página | Endereço próprio |
| --- | --- | --- |
| Financeiro | Controle de Obras | `/controle-obras/` |
| Investimentos | Calcular preço teto | `/analisador-de-preco/` |

Cada página continua morando no seu próprio repositório e funcionando pelo
endereço direto. O hub não move nem duplica nada — só reúne.

Como tudo fica sob o mesmo domínio (`laureanorenan.github.io`), a moldura é de
mesma origem: o login do Controle de Obras funciona igual, e o hub consegue
acertar o tema da página carregada.

## Navegação

O endereço guarda a página aberta, então dá para favoritar direto:

- `https://laureanorenan.github.io/#/obras`
- `https://laureanorenan.github.io/#/preco-teto`

## Identidade visual

Tokens do design system "Preço Teto": azul-marinho de marca, verde-menta de
destaque, Roboto para texto e Roboto Mono para números, com tema claro e
escuro. A escolha de tema é compartilhada entre o hub e as páginas.

## Adicionar uma página nova

No `index.html`, acrescente uma entrada em `ROTAS` com título, grupo, endereço
e descrição, e um `<li>` no grupo correspondente do menu.
