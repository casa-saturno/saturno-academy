# Domínio do site · saturnoacademy.com (ATIVO desde 26/10/2026)

Registrado no Cloudflare Registrar. DNS no Cloudflare: 4 A + 4 AAAA (raiz → GitHub Pages) e CNAME www → casa-saturno.github.io, todos "DNS only". `CNAME` no repositório = `saturnoacademy.com`; Enforce HTTPS ativo. Pendentes recomendados: renovação automática ligada no Cloudflare; confirmar o e-mail de verificação do registrante (ICANN) em até 15 dias; opcionalmente registrar academysaturno.com.br como proteção.

---

# Domínio do site · saturnoacademy.com.br

## Situação (26/10/2026)
- `saturnoacademy.com.br` e `saturno-academy.com.br`: **já registrados** em 12/11/2023 em nome de Jefferson Fernando Figueiredo, pelo registrador HSTDOMAINS (Hostinger). DNS em `ns1/ns2.dns-parking.com` (página de estacionamento da Hostinger). **Vencem em 12/11/2026: renovar.**
- `casasaturno.com.br`: registrado em nome de Tatiana Costa Rodrigues (site atual na Wix).
- `saturnoacademy.com` e `saturnoacademy.net`: livres. `saturno.academy`: registrado por terceiro (Amazon Registrar, dez/2025).

## Passo a passo (quem tem acesso à conta Hostinger do Jefferson)
1. **Renovar** `saturnoacademy.com.br` (vence 12/11/2026). Opcional: renovar também `saturno-academy.com.br` e apontá-lo para o mesmo site.
2. hPanel → Domínios → saturnoacademy.com.br → **DNS / Nameservers**. Manter os nameservers da Hostinger e editar a zona DNS:
   - **Apagar** o registro `A` de estacionamento (hoje aponta para `2.57.91.91`) e qualquer `CNAME` em `www`.
   - **Criar 4 registros A** para `@` (raiz):
     `185.199.108.153` · `185.199.109.153` · `185.199.110.153` · `185.199.111.153`
   - **Criar 4 registros AAAA** para `@`:
     `2606:50c0:8000::153` · `2606:50c0:8001::153` · `2606:50c0:8002::153` · `2606:50c0:8003::153`
   - **Criar 1 registro CNAME**: nome `www` → valor `casa-saturno.github.io`
   - TTL: o padrão (3600) serve.
3. Avisar o Matheus/Claude. Do lado do GitHub, será feito:
   - arquivo `CNAME` na raiz do repositório com `saturnoacademy.com.br`;
   - verificação do DNS em Settings → Pages e ativação de **Enforce HTTPS** (certificado Let's Encrypt automático, pode levar até 1 h após a propagação).
4. Resultado: `https://saturnoacademy.com.br` serve o site; `www.saturnoacademy.com.br` e `casa-saturno.github.io/saturno-academy` redirecionam para ele.

## Recomendações
- **Titularidade:** o domínio está em nome de pessoa física. Para proteger a marca, transferir a titularidade no Registro.br para a empresa (O.T. Produções Artísticas Ltda, CNPJ 33.931.690/0001-51, ou Casa Saturno Produções Artísticas Ltda). Processo "alteração de titularidade" no painel do Registro.br, feito pelo titular atual.
- **Proteção:** registrar `saturnoacademy.com` (livre, ~US$ 10/ano) e redirecionar para o .com.br, para não cair em mão de terceiros com o tráfego pago.
- **Não** adicionar o arquivo `CNAME` no repositório antes de o DNS estar configurado: isso faria o endereço github.io redirecionar para um domínio ainda sem apontamento.

## Como conferir a propagação
```bash
dig +short saturnoacademy.com.br A
dig +short www.saturnoacademy.com.br CNAME
```
Esperado: os quatro IPs 185.199.108–111.153 e `casa-saturno.github.io.`

---

# Opção escolhida: registrar um domínio novo (26/10/2026)

## Nomes livres em 26/10/2026
| Nome | Onde registrar | Custo aprox. | Observação |
|---|---|---|---|
| **saturnoacademy.com** | Cloudflare Registrar, Namecheap, Hostinger, GoDaddy | US$ 10–12/ano (~R$ 60–70) | Mais limpo para anúncio e fácil de falar; sem exigência de CNPJ |
| **academysaturno.com.br** | Registro.br | R$ 40/ano | Inversão do nome; .com.br passa confiança no Brasil |
| saturnoacademy.net.br | Registro.br | R$ 40/ano | Menos usual |
| saturnoacademy.art.br | Registro.br | R$ 40/ano | Terminação aberta, combina com arte, pouco conhecida |
| saturnoacademyoficial.com.br | Registro.br | R$ 40/ano | Longo |
| saturnoacademy.rio / .app / .art / .school | registradores internacionais | US$ 15–40/ano | Terminações novas; .app obriga HTTPS (ok no Pages) |

Ocupados: saturnoacademy.com.br e saturno-academy.com.br (Jefferson), saturno.academy (terceiro), turmafundadora.com.br. `.edu.br` e `.rio.br` têm restrições de elegibilidade.

Recomendação: **saturnoacademy.com** como endereço principal e, se quiser proteger a marca no Brasil, **academysaturno.com.br** redirecionando para ele.

## Como registrar um .com (ex.: saturnoacademy.com)
Sugestão de registrador: **Cloudflare Registrar** (preço de custo, sem renovação cara, DNS gratuito). Alternativas em reais: Hostinger ou GoDaddy.
1. Criar conta em dash.cloudflare.com com o e-mail da empresa (de preferência contato@casasaturno.com.br ou outro e-mail institucional, não pessoal).
2. Menu **Domain Registration → Register Domains** → buscar `saturnoacademy.com` → adicionar ao carrinho.
3. Dados do titular: usar a empresa (O.T. Produções Artísticas Ltda) e o e-mail institucional. Ativar renovação automática.
4. Pagar com cartão internacional (cobrança em dólar).
5. Depois do registro, em **DNS → Records**, criar (todos com proxy **desligado**, nuvem cinza "DNS only"):
   - `A` `@` → `185.199.108.153`
   - `A` `@` → `185.199.109.153`
   - `A` `@` → `185.199.110.153`
   - `A` `@` → `185.199.111.153`
   - `AAAA` `@` → `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
   - `CNAME` `www` → `casa-saturno.github.io`
6. Avisar o Matheus/Claude: do lado do GitHub, entra o arquivo `CNAME` com o domínio e o **Enforce HTTPS**.

## Como registrar um .com.br (ex.: academysaturno.com.br)
1. Acessar registro.br → **Criar conta** com o **CNPJ da empresa** (O.T. Produções Artísticas Ltda, 33.931.690/0001-51) e e-mail institucional. O cadastro pede os dados da empresa e um contato administrativo (pode ser o Matheus).
2. Buscar o domínio → **Registrar** → escolher o período (1 a 10 anos; R$ 40/ano) → pagar por Pix, boleto ou cartão. O domínio ativa após a confirmação do pagamento (Pix é imediato).
3. No painel do Registro.br, abrir o domínio → **DNS → Alterar servidores DNS → Utilizar os servidores DNS do Registro.br** (hospedagem de DNS gratuita) → **Modo avançado** → criar os mesmos registros A, AAAA e CNAME da lista acima.
4. Avisar o Matheus/Claude para o `CNAME` e o HTTPS no GitHub.

## Depois do apontamento (lado GitHub, feito pelo Claude)
- Arquivo `CNAME` na raiz do repositório com o domínio principal.
- Settings → Pages: verificação de DNS e **Enforce HTTPS** (certificado automático em até ~1 h).
- Os endereços secundários (www, .com.br de proteção) passam a redirecionar para o principal.
