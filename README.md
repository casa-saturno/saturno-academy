# Site Saturno Academy · Turma Fundadora 2026/2027

Publicado em **https://saturnoacademy.com** (GitHub Pages, branch `main`, arquivo `CNAME`; www e casa-saturno.github.io/saturno-academy redirecionam para ele; HTTPS forçado). DNS no Cloudflare: 4 A + 4 AAAA na raiz para os IPs do GitHub Pages e CNAME www → casa-saturno.github.io, todos em modo "DNS only". Para atualizar o site: editar, `git commit`, `git push`; o deploy leva 1–3 minutos.

Página única de vendas (`index.html`) com a jornada da proposta comercial apresentada na inauguração (23/10/2026), alinhada ao contrato v4.5 (versão de 23/10/2026) e ao handoff do projeto.

**Estratégia (26/10):** o site é para quem não foi ao evento e conhece pouco a Academy. Ele encanta e leva à ficha de interesse; **os valores não aparecem no site** e são enviados pelo comercial no WhatsApp. Os 33 leads da inauguração são abordados um a um pelo comercial, com urgência. O vídeo da apresentação (`assets/apresentacao.mp4`, 720p) abre a página logo após o herói.

## Rodar localmente
```bash
python3 -m http.server 8765
```
Abrir http://localhost:8765

## Configuração (objeto `CFG` no fim do `index.html`)
Tudo o que muda fica em um lugar e é injetado nos `<span data-cfg="...">`:
- `WHATSAPP_NUMBER`: 5521966503704 (comercial).
- `INSTAGRAM_URL`: @saturno.academy. `EMAIL`: contato@casasaturno.com.br (canal oficial do contrato).
- `DEADLINE` / `deadlineLabel`: hoje "sexta-feira, 30 de outubro" (pedido do Matheus). **O contrato fala em adesão até 31/10/2026 (cláusulas 4.2 e 6.5).** Se o prazo for estendido, ajustar aqui e no contrato.
- Preços do contrato ficam no `CFG` como referência, mas **não são exibidos**. Em uso: vagas 50, desistência sem multa até 05/01/2027, aviso de não início até 15/12/2026, prazo da condição de fundador.

## O que o site faz
- Jornada: vídeo da apresentação → problema → ecossistema → prova (time, cases, crescimento do elenco, turnê) → pilares e método → programa Ano 1 (calendário, 4 eixos, 1º semestre, mínimos garantidos, Artista & Manager) → ecossistema/acesso/palco → "a conta que ninguém faz" → seleção → fundadores → investimento sem valores (3 formas de pagar, incluído/não incluído, segurança, countdown, CTA para a ficha) → **resumo de 1 tela para enviar a quem decide** (botão de compartilhar) → FAQ → formulário → rodapé com dados da empresa e privacidade.
- Ficha de interesse sem backend e sem documentos: nome do responsável, WhatsApp, idade do artista, bairro/cidade, o que quer saber primeiro, como conheceu, consentimento LGPD. Ao enviar, abre o WhatsApp do comercial com a mensagem pronta pedindo os valores.
- "Enviar este resumo" usa o compartilhamento nativo do celular; no desktop, abre o WhatsApp Web com o texto.

## Regras seguidas (do contrato e do handoff)
- Sem promessa de contratação, casting, gravação comercial, fama ou resultado; participações do ecossistema tratadas como oportunidades.
- Prometido só o que está no contrato: 2+ encontros presenciais/semana e 2 fonogramas coletivos/semestre; uso dos fonogramas só em portfólio e redes.
- Benefícios de fundador conforme cláusula 4.3 (abono, Ano 1 em 12 parcelas sem out–dez/2027, parede, preferência na renovação).
- Removidos da proposta: "Saturno Kids", "Domingos no palco", "12 músicas / 9 ensaios em 3 anos", "2 meses adicionais", "Certificação 360°" como promessa.
- Sem valores no site, a comparação parcelado × à vista (CDC) passa a ser feita pelo comercial ao apresentar os planos.

## Medição e modo da oferta (27/10/2026)

Implementa o handoff do chat de tráfego (arquivo local `claude/handoff-medicao-e-oferta-pos-3010.md`, fora do repositório). Tudo configurável no objeto `SA`, no `<head>` do `index.html`:

- `PIXEL_ID` (Meta Pixel 1036113599501859) e `GA4_ID` (G-DTTTNXSLPN). Só carregam depois do aceite no banner de cookies (`sa_consent` no `localStorage`; aceite vale 365 dias, recusa 30). `CONSENT_BANNER: false` carrega sem perguntar.
- `MODO_OFERTA`: `'auto'` (padrão) vira `'vagas'` a partir de `VAGAS_DESDE` (31/10/2026 00:00, horário de Brasília); `'contador'` ou `'vagas'` forçam. Pré-visualização: `?modo=vagas` ou `?modo=contador` na URL.
  - Modo contador: faixa com data, contador no topo e na seção Investimento, "admitidos até 30/10", linha "Prazo" no resumo.
  - Modo vagas: contador some; textos passam a "enquanto houver vaga / quando a turma fechar", sem data e sem número de vagas restantes; FAQ ganha "Até quando posso entrar?". Elementos marcados com `.so-contador` / `.so-vagas`.
- Eventos: `ViewContent`/`video_start` no primeiro play; `Contact`/`whatsapp_click` nos links de WhatsApp (`data-sa`: `flutuante`, `rodape`, `cta-resumo`); `Lead`/`generate_lead` ao enviar a ficha (só faixa etária e interesse, nunca dado pessoal).
- Origem: UTMs ficam 30 dias em `sa_origem`; sem UTM, deduz pelo referrer. A mensagem do WhatsApp termina com `Origem: source/medium/campaign/content/term` (`/nome-do-botão` nos links). Taxonomia de UTM e links prontos no handoff.
- `privacidade.html`: política de privacidade (ficha, cookies, direitos, menores). Link no rodapé e no banner; `?cookies=1` reabre o banner.
- Meta tag `facebook-domain-verification` no `<head>`; falta clicar em "Verificar domínio" no Business Manager.

Pendências do handoff: texto final da política a confirmar; linha do plano à vista no modo vagas ficou neutra ("Pix ou TED na adesão") até o ajuste do contrato; teste com Meta Pixel Helper e GA4 Tempo real no site publicado.

## A confirmar antes de publicar
- Prazo: 30/10 (comunicação) vs 31/10 (contrato). Em 31/10 o site passa sozinho ao modo vagas (ver seção de medição).
- Time: o PDF da proposta apresentado em 23/10 mostra seis pessoas (Igor, Omena, Tati, Kysha, Umberto, Juninho); o handoff cita cinco. O site segue o PDF.
- Números de turnê (+70 mil ingressos, 23 estados, +60 shows) e da loja: vieram preenchidos no PDF de 23/10; o handoff pede confirmação.
- Crescimento do elenco (Fidelisx 40 mil → 668 mil etc.): do handoff, marcado como "confirmar números".
- Política de desconto para irmãos/grupo e de bolsa: não publicadas.
- Pergunta "Preciso já ser artista?": sem resposta definida, fora do FAQ.

## Fontes
- `~/Desktop/saturno-academy/Saturno Academy/`: contrato v4.5, handoff, cartilha, discovery de pagamento.
- `~/Downloads/Contrato Saturno Academy - fulano.pdf`: contrato gerado pela Clicksign (mesma versão de 23/10).
- Proposta Comercial (PDF, 38 páginas, versão apresentada em 23/10): textos e imagens (`assets/`, 23 imagens em WebP, 1,9 MB).
- Planilha de leads e Q&A da inauguração: objeções e perguntas que viraram FAQ e resumo. Nenhum dado pessoal foi usado no site.
