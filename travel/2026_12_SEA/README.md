# Viagem Indochina

Guia da viagem de 25/12/2026 a 24/01/2027 por Tailândia, Laos, Camboja e Vietnã: visão geral,
calendário, países e cidades, roteiro dia a dia, principais atrações, voos e transfers, hotéis e
orientações gerais. É um site estático: não tem servidor, login nem etapa de compilação.

Esta pasta contém **somente arquivos públicos**: `index.html`, `creditos.html`, `img/` (fotos em
WebP), `imagens-manifest.json`, `CREDITOS_IMAGENS.md`, este `README.md` e `.nojekyll`. Publique apenas
o conteúdo desta pasta.

## Ver no computador

Abra um terminal **dentro desta pasta** e rode:

```bash
python -m http.server 8000 --bind 127.0.0.1
```

Depois acesse <http://127.0.0.1:8000/>. Para encerrar, use Ctrl+C no terminal. Abrir o `index.html`
com dois cliques também funciona na maioria dos navegadores, mas o servidor local reproduz melhor o
comportamento de um site publicado.

Links diretos úteis: `#dia-12`, `#trecho-04`, `#trecho-11`, `#hotel-chiang-mai`, `#atr-kuang-si`,
`#voos-bagagem`. Cada link abre a aba certa, revela o item, limpa filtros que o escondam e funciona
ao recarregar e com Voltar/Avançar.

## Onde editar os dados

Todo o conteúdo da viagem fica num único bloco, `<script id="dados-viagem">`, dentro do
`index.html`, no objeto `window.VIAGEM`. O bloco é **JSON estrito**: aspas duplas, sem vírgula
depois do último item. Um erro de sintaxe deixa a página em branco.

| Coleção | O que guarda |
|---|---|
| `meta` | título, descrição, avisos (`atencao`), notas de transporte, foto de capa (`capa`), fusos dos aeroportos (`aeroportos`) |
| `dias` | os 31 dias: resumo, períodos, notas, pendências e foto do dia (`foto`) |
| `estadias` | os 9 hotéis, com cada noite e seu status |
| `transportes` | os 11 deslocamentos (`trecho-01` a `trecho-11`) |
| `atracoes`, `atividades` | o que fazer em cada lugar e em que dia |
| `imagens`, `galeria` | registro de fotos e ordem do acervo visual |

**Voos.** Cada trecho aéreo tem `segmentos`: número do voo, companhia, origem e destino com data,
hora local e terminal (`null` quando o comprovante não mostra). Também tem `conexoes`, `evidencia`
(documento, abrangência, situação, pagamento, verificação ao vivo) e `bagagem` (somente o que o
comprovante mostra). As durações são **calculadas com os fusos** de `meta.aeroportos`, nunca
subtraindo relógios de aeroportos diferentes. Ao mudar um horário, recalcule a duração e a conexão.
Os horários seguem a revisão consolidada dos comprovantes enviados pelo grupo. Os comprovantes não
fazem parte do site e não devem ser publicados.

## Fotos e créditos

`V.imagens`, no `index.html`, é a fonte única dos dados de cada foto: arquivo, variantes de
800 px, dimensões, texto alternativo, legenda, ponto de foco, autor, licença, página de origem e
modificações. O `imagens-manifest.json`, o `CREDITOS_IMAGENS.md` e o `creditos.html` são gerados a
partir dele. Para trocar ou acrescentar uma foto:

1. Salve o arquivo em `img/` como WebP (cerca de 1600 px de largura, mais uma variante de 800 px).
2. Crie ou atualize o registro em `V.imagens` com `src`, `width`, `height`, `alt`, `titulo`, `foco` e
   os campos de crédito. Para fotos de terceiros, informe autor, licença, link da licença, página
   de origem e data da verificação.
3. Ligue a foto onde ela aparece: `cidades[].imagem`, `atracoes[].imagens`, `dias[].foto`,
   `meta.capa`, uma parada do transfer (`programa[].imagem`) e a `galeria`.
4. Gere de novo o manifesto e as páginas de créditos com o script de manutenção do projeto de
   trabalho, ou atualize os três arquivos à mão, mantendo-os iguais.

Situação dos direitos: **15 fotos** vêm do Wikimedia Commons e tiveram autor e licença conferidos
na página de cada arquivo (CC BY 2.0/4.0 ou CC BY-SA 3.0/4.0, com atribuição obrigatória). As **28 fotos do acervo anterior e
as 4 fotos enviadas pelo usuário não têm autoria nem direitos documentados**. A coleção não está
declarada liberada para publicação; veja `creditos.html`.

## Pendências reais

- **Voos:** obter o e-ticket ou a confirmação final do VJ914 (08/01). O comprovante enviado é uma
  captura anterior à confirmação. Na conexão de 05/01 em Bangkok Don Mueang, confirmar trânsito,
  imigração e despacho da bagagem. Em 17/01 os horários e terminais em Ho Chi Minh (SGN) não
  constam no comprovante. A bagagem despachada dos voos AirAsia não aparece nos comprovantes, e as
  franquias da Lao Airlines e da VietJet não estão estabelecidas. Só um bilhete Emirates foi
  inspecionado. O status operacional dos voos não foi verificado em fonte ao vivo.
- **Transfer de 14/01:** confirmar no voucher o horário e o local da coleta, a modalidade, a
  capacidade para 10 pessoas com malas e o ingresso das Montanhas de Mármore. Uma foto pública de
  agosto de 2024 descreve a Torre Cham de Phu Dien como fechada à visitação.
- **Traslados, passeios e ingressos** marcados no site como "a definir" ou "a contratar",
  inclusive o Angkor Pass.
- **Fotos:** autoria e direitos das 32 fotos sem documentação.

Versão 13, atualizada em 15/11/2026. Reservas, horários e regras de entrada mudam: valem sempre os
bilhetes, as confirmações e os portais oficiais.
