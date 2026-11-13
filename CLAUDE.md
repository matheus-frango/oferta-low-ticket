# Oferta low ticket

Projeto para criar, lançar e otimizar uma oferta low ticket com tráfego pago no Meta Ads. O trabalho é dividido entre agentes em `.claude/agents/`.

## Fluxo

Todo pedido começa no **gerente-oferta**. Ele divide, delega, confere e só entrega o que passou no controle de qualidade.

```
Pedido do Matheus
  └─ gerente-oferta
       1. pesquisador          → mercado, público, concorrentes
       2. arquiteto-oferta     → promessa, entregáveis, bônus, garantia, ancoragem
       3. precificador         → ticket, CPA teto, margem, break-even
       4. copywriter-pagina    → página de vendas mobile-first
          copywriter-anuncio   → 30 hooks + corpos de anúncio
       5. roteirista-criativo  → roteiros de vídeo curto (gancho de 3s)
       6. editor-video         → corte, legenda, exportação (ffmpeg-skill)
       7. testador             → página e checkout como cliente
          dev-seguranca        → segredos, webhooks, validação
       8. gestor-trafego       → estrutura no Meta Ads (tudo pausado)
       ── OK do Matheus ──     → ativação
       9. analista             → CPA, ROAS, onde cortar
          (volta para 2–5 conforme o gargalo)
  └─ controle de qualidade → entrega
```

Dependências: pesquisa → oferta → preço → copy → criativo → testes → campanha. Uma etapa só começa com a anterior aprovada.

## Controle de qualidade

O gerente-oferta reprova e devolve quando houver:
- número, métrica, depoimento ou resultado sem fonte;
- entrega que não responde ao pedido;
- promessa que o produto não sustenta ou que viole política do Meta;
- contradição com a oferta ou o preço aprovados;
- suposição onde deveria haver pergunta.

## Regras para todos os agentes

- Não inventar números. Sem dado, perguntar ou rotular como CENÁRIO/FALTANDO.
- Perguntar quando faltar informação.
- Nada vai ao ar sem OK explícito do Matheus: campanha, página, checkout, publicação, compra real.
- gestor-trafego cria tudo pausado e nunca ativa nem aumenta orçamento sem OK na mesma mensagem.
- Antes de instalar dependência, perguntar.

## Integrações

MCPs em `.mcp.json`: `stripe`, `meta-ads`, `elevenlabs`. Skills de marketing e vídeo em `.claude/skills/`.
