# ArbTrading
Estratégia de Arbitragem e Day Trading
O Dashboard ArbTrading SCC foi projetado para auxiliar traders a identificar e capitalizar em ineficiências do mercado e movimentos rápidos de preços de criptomoedas.

🌐 Exchanges Integradas (8 no total):
Binance: Maior exchange global, alta liquidez, API estável
Bybit: Popular para derivativos, crescendo em spot
OKX: Top 3 global, excelente liquidez
KuCoin: Boa variedade de altcoins, API confiável
MEXC: Foco em novos projetos, listagens rápidas
Gate.io: Grande variedade de pares, boa para arbitragem
Huobi: Exchange estabelecida, forte presença asiática
Kraken: Regulamentada nos EUA, alta segurança
📊 O que as APIs Públicas Fornecem:
Ticker 24hr: Preço atual, volume, variação percentual
Order Book (limitado): Primeiras ordens de compra/venda
Trades Recentes: Histórico de transações executadas
Klines/Candles: Dados históricos OHLCV
🎯 Estratégias de Arbitragem Multi-Exchange:
Com 8 exchanges integradas, as oportunidades de arbitragem aumentam exponencialmente:

Arbitragem Simples: Comprar na exchange mais barata e vender na mais cara
Arbitragem Triangular: Explorar diferenças entre 3 ou mais exchanges
Arbitragem de Liquidez: Aproveitar diferenças temporárias em exchanges com menor volume
Flash Arbitrage: Oportunidades rápidas durante alta volatilidade
💡 Dicas para Maximizar Lucros:
Fees: Considere as taxas de trading de cada exchange (0.05% - 0.1%)
Velocidade: Arbitragem requer execução rápida (segundos importam)
Liquidez: Verifique o volume antes de executar grandes trades
Limites: Algumas exchanges têm limites de saque diários
KYC: Verifique os requisitos de cada exchange
🎯 Oportunidades de Arbitragem Spot:
Comparamos os preços de uma mesma criptomoeda entre as exchanges Binance, MEXC e Gate.io. Uma diferença percentual significativa pode indicar uma oportunidade de comprar barato em uma exchange e vender caro em outra. A lógica atual busca um spread de preço acima de 0.5%.

🚀 Sinais de PUMP (Volume e Momentum):
Monitoramos o volume de negociação e a variação percentual de 24 horas. Sinais como "Volume Spike" (alto volume + alta variação) e "Strong Momentum" (alta variação sustentada) são indicados para identificar movimentos explosivos de preço. A lógica atual considera variação de 24h acima de 10% e volume acima de 1 milhão para "Volume Spike", e variação acima de 15% para "Strong Momentum".

⚖️ Score de Oportunidade:
Cada oportunidade detectada contribui para um Score geral da criptomoeda. Scores mais altos indicam uma confluência de múltiplos sinais de interesse.

🔓 Limitações das APIs Públicas:
Rate Limits: Número limitado de requisições por minuto
Sem Execução: Não é possível criar ordens automaticamente
Dados Limitados: Sem acesso a saldos ou histórico pessoal
Funding Rates: Requerem APIs de futuros (públicas mas separadas)
🔐 Futuras Melhorias com APIs Privadas:
Em versões futuras, com autenticação via API Keys, seria possível:

Executar trades automaticamente ao detectar arbitragem
Monitorar saldos e P&L em tempo real
Implementar stop-loss e take-profit automáticos
Acessar histórico completo de trades pessoais
Disclaimer: Trading de criptomoedas envolve riscos substanciais. 
Este dashboard é uma ferramenta de análise e não deve ser considerado como aconselhamento financeiro.
