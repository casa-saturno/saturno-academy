# Site Saturno Academy · Turma Fundadora 2026/2027 (protótipo)

Página única de vendas (`index.html`) com a jornada da proposta comercial apresentada na inauguração (23/10/2026), alinhada ao contrato v4.5 (versão de 23/10/2026) e ao handoff do projeto. Objetivo: ser a peça que a mãe manda para quem decide com ela e levar à conversa no WhatsApp.

## Rodar localmente
```bash
python3 -m http.server 8765
```
Abrir http://localhost:8765

## Configuração (objeto `CFG` no fim do `index.html`)
Tudo o que muda fica em um lugar e é injetado nos `<span data-cfg="...">`:
- `WHATSAPP_NUMBER` **(a confirmar)**: número do comercial, só dígitos, com 55 + DDD. Hoje placeholder.
- `INSTAGRAM_URL`: @saturno.academy. `EMAIL`: contato@casasaturno.com.br (canal oficial do contrato).
- `DEADLINE` / `deadlineLabel`: hoje "sexta-feira, 30 de outubro" (pedido do Matheus). **O contrato fala em adesão até 31/10/2026 (cláusulas 4.2 e 6.5).** Se o prazo for estendido, ajustar aqui e no contrato.
- Preços: tabela 4.600 (55.200), fundador 3.600 (43.200), à vista 38.400, abono 1.000, vagas 50, desistência sem multa até 05/01/2027, aviso de não início até 15/12/2026.

## O que o site faz
- Jornada: problema → ecossistema → prova (time, cases, crescimento do elenco, turnê) → pilares e método → programa Ano 1 (calendário, 4 eixos, 1º semestre, mínimos garantidos, Artista & Manager) → ecossistema/acesso/palco → "a conta que ninguém faz" → seleção → fundadores → investimento (3 planos, abono, incluído/não incluído, segurança, countdown) → **resumo de 1 tela para enviar a quem decide** (botão de compartilhar) → FAQ → formulário → rodapé com dados da empresa e privacidade.
- Formulário sem backend e sem documentos: nome do responsável, WhatsApp, idade do artista, bairro/cidade, plano, como conheceu, consentimento LGPD. Ao enviar, abre o WhatsApp do comercial com a mensagem pronta.
- "Enviar este resumo" usa o compartilhamento nativo do celular; no desktop, abre o WhatsApp Web com o texto.

## Regras seguidas (do contrato e do handoff)
- Sem promessa de contratação, casting, gravação comercial, fama ou resultado; participações do ecossistema tratadas como oportunidades.
- Prometido só o que está no contrato: 2+ encontros presenciais/semana e 2 fonogramas coletivos/semestre; uso dos fonogramas só em portfólio e redes.
- Benefícios de fundador conforme cláusula 4.3 (abono, Ano 1 em 12 parcelas sem out–dez/2027, parede, preferência na renovação).
- Removidos da proposta: "Saturno Kids", "Domingos no palco", "12 músicas / 9 ensaios em 3 anos", "2 meses adicionais", "Certificação 360°" como promessa.
- Comparação parcelado × à vista exibida (CDC): 43.200 vs 38.400, diferença de 4.800 (12,5%).

## A confirmar antes de publicar
- Número do WhatsApp comercial.
- Prazo: 30/10 (comunicação) vs 31/10 (contrato).
- Time: o PDF da proposta apresentado em 23/10 mostra seis pessoas (Igor, Omena, Tati, Kysha, Umberto, Juninho); o handoff cita cinco. O site segue o PDF.
- Números de turnê (+70 mil ingressos, 23 estados, +60 shows) e da loja: vieram preenchidos no PDF de 23/10; o handoff pede confirmação.
- Crescimento do elenco (Fidelisx 40 mil → 668 mil etc.): do handoff, marcado como "confirmar números".
- Política de desconto para irmãos/grupo e de bolsa: não publicadas.
- Pergunta "Preciso já ser artista?": sem resposta definida, fora do FAQ.

## Fontes
- `~/Desktop/saturno-academy/Saturno Academy/`: contrato v4.5, handoff, cartilha, discovery de pagamento.
- `~/Downloads/Contrato Saturno Academy - fulano.pdf`: contrato gerado pela Clicksign (mesma versão de 23/10).
- Proposta Comercial (PDF, 38 páginas, versão apresentada em 23/10): textos e imagens (`assets/`, ~26 MB; converter para WebP em produção).
- Planilha de leads e Q&A da inauguração: objeções e perguntas que viraram FAQ e resumo. Nenhum dado pessoal foi usado no site.
