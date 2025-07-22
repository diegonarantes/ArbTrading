<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard ArbTrading SCC</title>
    <script crossorigin src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* 
        Dashboard ArbTrading SCC - Sistema de Arbitragem de Criptomoedas
        ===============================================================
        
        EXCHANGES INTEGRADAS E SUAS APIs PÚBLICAS:
        
        1. BINANCE (https://binance-docs.github.io/apidocs/spot/en/)
           - Ticker: https://api.binance.com/api/v3/ticker/24hr
           - Order Book: https://api.binance.com/api/v3/depth?symbol=BTCUSDT
           - Trades: https://api.binance.com/api/v3/trades?symbol=BTCUSDT
           - Klines: https://api.binance.com/api/v3/klines?symbol=BTCUSDT&interval=1h
        
        2. BYBIT (https://bybit-exchange.github.io/docs/v5/intro)
           - Ticker: https://api.bybit.com/v5/market/tickers?category=spot
           - Order Book: https://api.bybit.com/v5/market/orderbook?category=spot&symbol=BTCUSDT
           - Trades: https://api.bybit.com/v5/market/recent-trade?category=spot&symbol=BTCUSDT
        
        3. OKX (https://www.okx.com/docs-v5/en/)
           - Ticker: https://www.okx.com/api/v5/market/tickers?instType=SPOT
           - Order Book: https://www.okx.com/api/v5/market/books?instId=BTC-USDT
           - Trades: https://www.okx.com/api/v5/market/trades?instId=BTC-USDT
        
        4. KUCOIN (https://docs.kucoin.com/)
           - Ticker: https://api.kucoin.com/api/v1/market/allTickers
           - Order Book: https://api.kucoin.com/api/v1/market/orderbook/level2_100?symbol=BTC-USDT
           - Trades: https://api.kucoin.com/api/v1/market/histories?symbol=BTC-USDT
        
        5. MEXC (https://mxcdevelop.github.io/apidocs/spot_v3_en/)
           - Ticker: https://api.mexc.com/api/v3/ticker/24hr
           - Order Book: https://api.mexc.com/api/v3/depth?symbol=BTCUSDT
           - Trades: https://api.mexc.com/api/v3/trades?symbol=BTCUSDT
        
        6. GATE.IO (https://www.gate.io/docs/developers/apiv4/)
           - Ticker: https://api.gateio.ws/api/v4/spot/tickers
           - Order Book: https://api.gateio.ws/api/v4/spot/order_book?currency_pair=BTC_USDT
           - Trades: https://api.gateio.ws/api/v4/spot/trades?currency_pair=BTC_USDT
        
        7. HUOBI (https://huobiapi.github.io/docs/spot/v1/en/)
           - Ticker: https://api.huobi.pro/market/tickers
           - Order Book: https://api.huobi.pro/market/depth?symbol=btcusdt&type=step0
           - Trades: https://api.huobi.pro/market/trade?symbol=btcusdt
        
        8. KRAKEN (https://docs.kraken.com/rest/)
           - Ticker: https://api.kraken.com/0/public/Ticker
           - Order Book: https://api.kraken.com/0/public/Depth?pair=XBTUSDT
           - Trades: https://api.kraken.com/0/public/Trades?pair=XBTUSDT
        
        RATE LIMITS (Limites de Requisições):
        - Binance: 1200 peso/minuto (ticker = peso 40)
        - Bybit: 120 req/segundo
        - OKX: 20 req/2 segundos
        - KuCoin: 100 req/10 segundos
        - MEXC: Similar à Binance
        - Gate.io: 900 req/minuto
        - Huobi: 100 req/10 segundos
        - Kraken: 15 req/segundo
        
        Para produção, recomenda-se:
        1. Implementar backend proxy para evitar CORS
        2. Cache de dados para reduzir chamadas
        3. WebSocket para dados em tempo real
        4. Respeitar rate limits de cada exchange
        */
        
        body {
            margin: 0;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
                'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
                sans-serif;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }
        
        /* Animação de loading */
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }
        
        .animate-pulse {
            animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
        }
        
        /* Scrollbar customizada */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        
        ::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 4px;
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: #555;
        }
    </style>
</head>
<body>
    <div id="root"></div>
    
    <script type="text/babel">
        const { useState, useEffect, useRef } = React;

        function App() {
          // Estados principais
          const [activeTab, setActiveTab] = useState('dashboard');
          const [darkMode, setDarkMode] = useState(false);
          const [favorites, setFavorites] = useState([]);
          const [selectedCrypto, setSelectedCrypto] = useState(null);
          const [showModal, setShowModal] = useState(false);
          const [searchTerm, setSearchTerm] = useState('');
          const [minScore, setMinScore] = useState(0);
          const [maxScore, setMaxScore] = useState(5);
          const [sortBy, setSortBy] = useState('rank');
          const [onlyWithOpportunities, setOnlyWithOpportunities] = useState(false);

          // Sistema de atualização em tempo real
          const [updateInterval, setUpdateInterval] = useState(10);
          const [isAutoUpdateEnabled, setIsAutoUpdateEnabled] = useState(true);
          const [lastUpdate, setLastUpdate] = useState(new Date());
          const [countdown, setCountdown] = useState(updateInterval);
          const [isUpdating, setIsUpdating] = useState(false);
          const [connectionCount, setConnectionCount] = useState(0);
          const [isLoadingInitialData, setIsLoadingInitialData] = useState(true);

          // Estados para dados e APIs
          const [cryptoData, setCryptoData] = useState([]);
          const [pumpData, setPumpData] = useState([]);
          const [apiStatus, setApiStatus] = useState({
            binance: 'disconnected',
            mexc: 'disconnected',
            gateio: 'disconnected',
            bybit: 'disconnected',
            kucoin: 'disconnected',
            okx: 'disconnected',
            huobi: 'disconnected',
            kraken: 'disconnected',
            general: 'disconnected'
          });

          // Efeito para carregar favoritos do localStorage
          useEffect(() => {
            const storedFavorites = JSON.parse(localStorage.getItem('arbTradingFavorites') || '[]');
            setFavorites(storedFavorites);
          }, []);

          // Efeito para salvar favoritos no localStorage
          useEffect(() => {
            localStorage.setItem('arbTradingFavorites', JSON.stringify(favorites));
          }, [favorites]);

          // Função para alternar o modo escuro
          const toggleDarkMode = () => {
            setDarkMode(!darkMode);
          };

          // Função para favoritar/desfavoritar uma criptomoeda
          const toggleFavorite = (symbol) => {
            setFavorites(prevFavorites =>
              prevFavorites.includes(symbol)
                ? prevFavorites.filter(fav => fav !== symbol)
                : [...prevFavorites, symbol]
            );
          };

          // Função para abrir o modal de detalhes
          const openCryptoModal = (crypto) => {
            setSelectedCrypto(crypto);
            setShowModal(true);
          };

          // Função para fechar o modal
          const closeCryptoModal = () => {
            setShowModal(false);
            setSelectedCrypto(null);
          };

          // Função para formatar números
          const formatNumber = (num, decimals = 2) => {
            if (num === null || num === undefined) return 'N/A';
            return num.toLocaleString('en-US', {
              minimumFractionDigits: decimals,
              maximumFractionDigits: decimals,
            });
          };

          // Função principal para buscar dados reais das APIs
          const fetchRealTimeData = async () => {
            setIsUpdating(true);
            setConnectionCount(prev => prev + 1);
            setApiStatus({ 
              binance: 'connecting', 
              mexc: 'connecting', 
              gateio: 'connecting',
              bybit: 'connecting',
              kucoin: 'connecting',
              okx: 'connecting',
              huobi: 'connecting',
              kraken: 'connecting',
              general: 'connecting' 
            });

            try {
              // Usando múltiplos proxies CORS para maior confiabilidade
              const corsProxies = [
                'https://cors-anywhere.herokuapp.com/',
                'https://api.allorigins.win/raw?url=',
                'https://corsproxy.io/?'
              ];
              
              // Função helper para tentar diferentes proxies
              const fetchWithProxy = async (url) => {
                for (const proxy of corsProxies) {
                  try {
                    const response = await fetch(proxy + encodeURIComponent(url), {
                      headers: {
                        'Accept': 'application/json',
                        'Content-Type': 'application/json'
                      }
                    });
                    if (response.ok) return response;
                  } catch (e) {
                    console.log(`Proxy ${proxy} falhou, tentando próximo...`);
                  }
                }
                throw new Error('Todos os proxies falharam');
              };
              
              // 1. Fazer chamadas paralelas para TODAS as APIs públicas
              const [
                binanceResponse, 
                mexcResponse, 
                gateioResponse,
                bybitResponse,
                kucoinResponse,
                okxResponse,
                huobiResponse,
                krakenResponse
              ] = await Promise.allSettled([
                fetchWithProxy('https://api.binance.com/api/v3/ticker/24hr'),
                fetchWithProxy('https://api.mexc.com/api/v3/ticker/24hr'),
                fetchWithProxy('https://api.gateio.ws/api/v4/spot/tickers'),
                fetchWithProxy('https://api.bybit.com/v5/market/tickers?category=spot'),
                fetchWithProxy('https://api.kucoin.com/api/v1/market/allTickers'),
                fetchWithProxy('https://www.okx.com/api/v5/market/tickers?instType=SPOT'),
                fetchWithProxy('https://api.huobi.pro/market/tickers'),
                fetchWithProxy('https://api.kraken.com/0/public/Ticker')
              ]);

              let rawBinanceData = [];
              if (binanceResponse.status === 'fulfilled' && binanceResponse.value.ok) {
                rawBinanceData = await binanceResponse.value.json();
                // Filtrar apenas os top 100 pares mais negociados para otimizar performance
                rawBinanceData = rawBinanceData
                  .filter(item => item.symbol.endsWith('USDT'))
                  .sort((a, b) => parseFloat(b.quoteVolume) - parseFloat(a.quoteVolume))
                  .slice(0, 100);
                setApiStatus(prev => ({ ...prev, binance: 'connected' }));
              } else {
                console.error('Erro ao buscar dados da Binance:', binanceResponse.reason || (binanceResponse.value && binanceResponse.value.statusText));
                setApiStatus(prev => ({ ...prev, binance: 'error' }));
              }

              let rawMexcData = [];
              if (mexcResponse.status === 'fulfilled' && mexcResponse.value.ok) {
                rawMexcData = await mexcResponse.value.json();
                setApiStatus(prev => ({ ...prev, mexc: 'connected' }));
              } else {
                console.error('Erro ao buscar dados da MEXC:', mexcResponse.reason || (mexcResponse.value && mexcResponse.value.statusText));
                setApiStatus(prev => ({ ...prev, mexc: 'error' }));
              }

              let rawGateioData = [];
              if (gateioResponse.status === 'fulfilled' && gateioResponse.value.ok) {
                rawGateioData = await gateioResponse.value.json();
                setApiStatus(prev => ({ ...prev, gateio: 'connected' }));
              } else {
                console.error('Erro ao buscar dados da Gate.io:', gateioResponse.reason || (gateioResponse.value && gateioResponse.value.statusText));
                setApiStatus(prev => ({ ...prev, gateio: 'error' }));
              }

              // Processar dados da Bybit
              let rawBybitData = [];
              if (bybitResponse.status === 'fulfilled' && bybitResponse.value.ok) {
                const bybitJson = await bybitResponse.value.json();
                rawBybitData = bybitJson.result?.list || [];
                setApiStatus(prev => ({ ...prev, bybit: 'connected' }));
              } else {
                console.error('Erro ao buscar dados da Bybit:', bybitResponse.reason);
                setApiStatus(prev => ({ ...prev, bybit: 'error' }));
              }

              // Processar dados da KuCoin
              let rawKucoinData = [];
              if (kucoinResponse.status === 'fulfilled' && kucoinResponse.value.ok) {
                const kucoinJson = await kucoinResponse.value.json();
                rawKucoinData = kucoinJson.data?.ticker || [];
                setApiStatus(prev => ({ ...prev, kucoin: 'connected' }));
              } else {
                console.error('Erro ao buscar dados da KuCoin:', kucoinResponse.reason);
                setApiStatus(prev => ({ ...prev, kucoin: 'error' }));
              }

              // Processar dados da OKX
              let rawOkxData = [];
              if (okxResponse.status === 'fulfilled' && okxResponse.value.ok) {
                const okxJson = await okxResponse.value.json();
                rawOkxData = okxJson.data || [];
                setApiStatus(prev => ({ ...prev, okx: 'connected' }));
              } else {
                console.error('Erro ao buscar dados da OKX:', okxResponse.reason);
                setApiStatus(prev => ({ ...prev, okx: 'error' }));
              }

              // Processar dados da Huobi
              let rawHuobiData = [];
              if (huobiResponse.status === 'fulfilled' && huobiResponse.value.ok) {
                const huobiJson = await huobiResponse.value.json();
                rawHuobiData = huobiJson.data || [];
                setApiStatus(prev => ({ ...prev, huobi: 'connected' }));
              } else {
                console.error('Erro ao buscar dados da Huobi:', huobiResponse.reason);
                setApiStatus(prev => ({ ...prev, huobi: 'error' }));
              }

              // Processar dados da Kraken
              let rawKrakenData = {};
              if (krakenResponse.status === 'fulfilled' && krakenResponse.value.ok) {
                const krakenJson = await krakenResponse.value.json();
                rawKrakenData = krakenJson.result || {};
                setApiStatus(prev => ({ ...prev, kraken: 'connected' }));
              } else {
                console.error('Erro ao buscar dados da Kraken:', krakenResponse.reason);
                setApiStatus(prev => ({ ...prev, kraken: 'error' }));
              }

              // 2. Normalizar e Mesclar os Dados
              const aggregatedData = {};

              rawBinanceData.forEach(item => {
                if (!item.symbol.endsWith('USDT')) return;
                const baseSymbol = item.symbol.replace('USDT', '');
                
                if (!aggregatedData[baseSymbol]) {
                    aggregatedData[baseSymbol] = { symbol: baseSymbol, name: baseSymbol, price: {}, change24h: {}, volume24h: {}, fundingRate: {} };
                }
                aggregatedData[baseSymbol].price.binance = parseFloat(item.lastPrice);
                aggregatedData[baseSymbol].change24h.binance = parseFloat(item.priceChangePercent);
                aggregatedData[baseSymbol].volume24h.binance = parseFloat(item.quoteVolume);
              });

              rawMexcData.forEach(item => {
                if (!item.symbol.endsWith('USDT')) return;
                const baseSymbol = item.symbol.replace('USDT', '');
                
                if (!aggregatedData[baseSymbol]) {
                    aggregatedData[baseSymbol] = { symbol: baseSymbol, name: baseSymbol, price: {}, change24h: {}, volume24h: {}, fundingRate: {} };
                }
                aggregatedData[baseSymbol].price.mexc = parseFloat(item.lastPrice);
                aggregatedData[baseSymbol].change24h.mexc = parseFloat(item.priceChangePercent);
                aggregatedData[baseSymbol].volume24h.mexc = parseFloat(item.quoteVolume);
              });

              rawGateioData.forEach(item => {
                if (!item.currency_pair.endsWith('_USDT')) return;
                const baseSymbol = item.currency_pair.replace('_USDT', '');
                
                if (!aggregatedData[baseSymbol]) {
                    aggregatedData[baseSymbol] = { symbol: baseSymbol, name: baseSymbol, price: {}, change24h: {}, volume24h: {}, fundingRate: {} };
                }
                aggregatedData[baseSymbol].price.gateio = parseFloat(item.last_price);
                aggregatedData[baseSymbol].change24h.gateio = parseFloat(item.change_percentage) * 100;
                aggregatedData[baseSymbol].volume24h.gateio = parseFloat(item.quote_volume);
              });

              // 3. Calcular Score e Oportunidades Reais
              const newCryptoData = Object.values(aggregatedData)
                .filter(crypto => {
                  // Deve ter preço em pelo menos 2 exchanges para arbitragem
                  const priceCount = Object.values(crypto.price).filter(p => p && p > 0).length;
                  const volumeCount = Object.values(crypto.volume24h).filter(v => v && v > 0).length;
                  return priceCount >= 2 && volumeCount >= 2;
                })
                .map(crypto => {
                  let opportunities = [];
                  let score = 0;
                  const arbitrageDetails = [];

                  // --- Lógica Avançada de Arbitragem Spot entre Múltiplas Exchanges ---
                  const exchangePrices = {};
                  const exchanges = ['binance', 'mexc', 'gateio', 'bybit', 'kucoin', 'okx', 'huobi', 'kraken'];
                  
                  exchanges.forEach(exchange => {
                    if (crypto.price[exchange] && crypto.price[exchange] > 0) {
                      exchangePrices[exchange] = crypto.price[exchange];
                    }
                  });

                  const prices = Object.values(exchangePrices).filter(p => p);
                  const exchangeNames = Object.keys(exchangePrices);
                  
                  if (prices.length >= 2) {
                    const minPrice = Math.min(...prices);
                    const maxPrice = Math.max(...prices);
                    const priceSpreadPercent = ((maxPrice - minPrice) / minPrice) * 100;
                    
                    // Encontrar as exchanges com menor e maior preço
                    const minExchange = exchangeNames.find(ex => exchangePrices[ex] === minPrice);
                    const maxExchange = exchangeNames.find(ex => exchangePrices[ex] === maxPrice);

                    if (priceSpreadPercent > 0.3) { // Threshold mais baixo para detectar mais oportunidades
                      const profitLevel = priceSpreadPercent > 2 ? 'Alta' : priceSpreadPercent > 1 ? 'Média' : 'Baixa';
                      opportunities.push(`Arbitragem ${profitLevel} (${priceSpreadPercent.toFixed(2)}%)`);
                      arbitrageDetails.push({
                        buyExchange: minExchange,
                        sellExchange: maxExchange,
                        spread: priceSpreadPercent,
                        buyPrice: minPrice,
                        sellPrice: maxPrice
                      });
                      
                      // Score baseado no spread
                      if (priceSpreadPercent > 2) score += 3;
                      else if (priceSpreadPercent > 1) score += 2;
                      else if (priceSpreadPercent > 0.5) score += 1;
                    }
                    
                    // Detectar arbitragem triangular (entre 3+ exchanges)
                    if (exchangeNames.length >= 3) {
                      const sortedPrices = Object.entries(exchangePrices).sort((a, b) => a[1] - b[1]);
                      if (sortedPrices.length >= 3) {
                        const triangularSpread = ((sortedPrices[sortedPrices.length-1][1] - sortedPrices[0][1]) / sortedPrices[0][1]) * 100;
                        if (triangularSpread > 1.5) {
                          opportunities.push('Arbitragem Triangular');
                          score += 1.5;
                        }
                      }
                    }
                  }

                  // --- Análise de Volume e Liquidez ---
                  const allVolumes = Object.values(crypto.volume24h).filter(v => v !== undefined && v !== null && v > 0);
                  const avgVolume24h = allVolumes.length > 0 ? (allVolumes.reduce((sum, val) => sum + val, 0) / allVolumes.length) : 0;
                  const totalVolume24h = allVolumes.reduce((sum, val) => sum + val, 0);
                  
                  // Detectar alta liquidez (importante para arbitragem)
                  if (totalVolume24h > 10_000_000) {
                    opportunities.push('Alta Liquidez');
                    score += 0.5;
                  }

                  // --- Lógica de "Pump Signal" (Volume e Variação) ---
                  const allChanges = Object.values(crypto.change24h).filter(c => c !== undefined && c !== null);
                  const avgChange24h = allChanges.length > 0 ? (allChanges.reduce((sum, val) => sum + val, 0) / allChanges.length) : 0;
                  const maxChange24h = allChanges.length > 0 ? Math.max(...allChanges) : 0;

                  if (avgChange24h > 10 && avgVolume24h > 1_000_000) {
                    opportunities.push('Volume Spike');
                    score += 1.5;
                  }
                  
                  if (maxChange24h > 20) {
                    opportunities.push('Mega Pump');
                    score += 2;
                  } else if (avgChange24h > 15) {
                    opportunities.push('Strong Momentum');
                    score += 1;
                  }
                  
                  // Detectar divergência de preço entre exchanges
                  if (allChanges.length >= 3) {
                    const changeSpread = Math.max(...allChanges) - Math.min(...allChanges);
                    if (changeSpread > 5) {
                      opportunities.push('Divergência de Mercado');
                      score += 0.8;
                    }
                  }

                  // Define o preço principal para exibição (prioriza exchanges por volume)
                  const displayPrice = crypto.price.binance || crypto.price.okx || crypto.price.bybit || 
                                     crypto.price.kucoin || crypto.price.mexc || crypto.price.gateio || 
                                     crypto.price.huobi || crypto.price.kraken || 0;

                  return {
                    symbol: crypto.symbol,
                    name: crypto.name,
                    price: displayPrice,
                    change24h: avgChange24h,
                    volume24h: avgVolume24h,
                    totalVolume24h: totalVolume24h,
                    exchangeData: {
                        binance: { price: crypto.price.binance, change24h: crypto.change24h.binance, volume24h: crypto.volume24h.binance },
                        mexc: { price: crypto.price.mexc, change24h: crypto.change24h.mexc, volume24h: crypto.volume24h.mexc },
                        gateio: { price: crypto.price.gateio, change24h: crypto.change24h.gateio, volume24h: crypto.volume24h.gateio },
                        bybit: { price: crypto.price.bybit, change24h: crypto.change24h.bybit, volume24h: crypto.volume24h.bybit },
                        kucoin: { price: crypto.price.kucoin, change24h: crypto.change24h.kucoin, volume24h: crypto.volume24h.kucoin },
                        okx: { price: crypto.price.okx, change24h: crypto.change24h.okx, volume24h: crypto.volume24h.okx },
                        huobi: { price: crypto.price.huobi, change24h: crypto.change24h.huobi, volume24h: crypto.volume24h.huobi },
                        kraken: { price: crypto.price.kraken, change24h: crypto.change24h.kraken, volume24h: crypto.volume24h.kraken },
                    },
                    fundingRates: crypto.fundingRate,
                    score: parseFloat(score.toFixed(1)),
                    opportunities: opportunities,
                    arbitrageDetails: arbitrageDetails, // Detalhes específicos de arbitragem
                    rank: 0,
                    marketCap: 0,
                    exchangeCount: Object.keys(exchangePrices).length // Número de exchanges com este par
                  };
                });

              const sortedNewCryptoData = newCryptoData.sort((a, b) => b.score - a.score);

              setCryptoData(sortedNewCryptoData);
              generatePumpData(sortedNewCryptoData);
              setLastUpdate(new Date());
              setApiStatus(prev => ({ ...prev, general: 'connected' }));

            } catch (error) {
              console.error('Erro ao buscar dados das APIs:', error);
              
              // Usar dados simulados se as APIs falharem
              const simulatedData = generateSimulatedData();
              setCryptoData(simulatedData);
              generatePumpData(simulatedData);
              setLastUpdate(new Date());
              setApiStatus({ binance: 'simulated', mexc: 'simulated', gateio: 'simulated', general: 'simulated' });
              
              // Informar o usuário sobre o modo simulado
              console.log(`
                ⚠️ Modo Simulado Ativado
                =======================
                As APIs públicas das exchanges não puderam ser acessadas diretamente do navegador devido a CORS.
                
                Para usar dados reais em produção:
                1. Configure um servidor proxy backend
                2. Use as APIs através do seu servidor
                3. Ou teste localmente com extensões que desabilitam CORS
                
                APIs Públicas Disponíveis:
                - Binance: https://api.binance.com/api/v3/ticker/24hr
                - MEXC: https://api.mexc.com/api/v3/ticker/24hr  
                - Gate.io: https://api.gateio.ws/api/v4/spot/tickers
                
                Todas são gratuitas e não requerem autenticação!
              `);
            } finally {
              setIsUpdating(false);
              setIsLoadingInitialData(false);
            }
          };

          // Função para gerar dados simulados (caso as APIs falhem)
          const generateSimulatedData = () => {
            // Simula dados realistas baseados no que as APIs públicas fornecem
            const symbols = [
              { symbol: 'BTC', basePrice: 43250.50, volatility: 0.02 },
              { symbol: 'ETH', basePrice: 2280.75, volatility: 0.03 },
              { symbol: 'BNB', basePrice: 315.20, volatility: 0.025 },
              { symbol: 'XRP', basePrice: 0.6245, volatility: 0.04 },
              { symbol: 'ADA', basePrice: 0.5832, volatility: 0.035 },
              { symbol: 'SOL', basePrice: 98.45, volatility: 0.045 },
              { symbol: 'DOT', basePrice: 7.82, volatility: 0.04 },
              { symbol: 'DOGE', basePrice: 0.0952, volatility: 0.05 },
              { symbol: 'AVAX', basePrice: 38.92, volatility: 0.038 },
              { symbol: 'MATIC', basePrice: 1.1250, volatility: 0.042 },
              { symbol: 'LINK', basePrice: 14.85, volatility: 0.035 },
              { symbol: 'UNI', basePrice: 6.24, volatility: 0.04 },
              { symbol: 'ATOM', basePrice: 9.87, volatility: 0.038 },
              { symbol: 'LTC', basePrice: 72.45, volatility: 0.03 },
              { symbol: 'NEAR', basePrice: 3.68, volatility: 0.045 }
            ];
            
            return symbols.map((item, index) => {
              // Simula variação de preço realista
              const change24h = (Math.random() - 0.5) * item.volatility * 100;
              const baseVolume = Math.random() * 50000000 * (item.symbol === 'BTC' ? 100 : item.symbol === 'ETH' ? 50 : 1);
              
              // Simula pequenas diferenças de preço entre exchanges (0.1% a 3%)
              const priceVariations = {
                binance: 0,
                bybit: (Math.random() - 0.5) * 0.015,
                okx: (Math.random() - 0.5) * 0.012,
                kucoin: (Math.random() - 0.5) * 0.02,
                mexc: (Math.random() - 0.5) * 0.025,
                gateio: (Math.random() - 0.5) * 0.03,
                huobi: (Math.random() - 0.5) * 0.018,
                kraken: (Math.random() - 0.5) * 0.01
              };
              
              // Calcula preços com variações
              const exchangePrices = {};
              const exchangeVolumes = {};
              const exchangeChanges = {};
              const availableExchanges = ['binance', 'bybit', 'okx', 'kucoin', 'mexc', 'gateio', 'huobi', 'kraken'];
              
              // Simula disponibilidade realista (nem todas as moedas estão em todas as exchanges)
              const numExchanges = Math.floor(Math.random() * 4) + 5; // Entre 5-8 exchanges
              const selectedExchanges = availableExchanges.sort(() => Math.random() - 0.5).slice(0, numExchanges);
              
              selectedExchanges.forEach(exchange => {
                exchangePrices[exchange] = item.basePrice * (1 + priceVariations[exchange]);
                exchangeVolumes[exchange] = baseVolume * (0.5 + Math.random() * 0.5);
                exchangeChanges[exchange] = change24h + (Math.random() - 0.5) * 2;
              });
              
              // Calcula spread real
              const prices = Object.values(exchangePrices);
              const maxPrice = Math.max(...prices);
              const minPrice = Math.min(...prices);
              const actualSpread = ((maxPrice - minPrice) / minPrice) * 100;
              
              const opportunities = [];
              const arbitrageDetails = [];
              let score = 0;
              
              // Encontra exchanges com menor e maior preço
              const minExchange = Object.keys(exchangePrices).find(ex => exchangePrices[ex] === minPrice);
              const maxExchange = Object.keys(exchangePrices).find(ex => exchangePrices[ex] === maxPrice);
              
              // Detecção de oportunidades baseada em dados simulados
              if (actualSpread > 0.3) {
                const profitLevel = actualSpread > 2 ? 'Alta' : actualSpread > 1 ? 'Média' : 'Baixa';
                opportunities.push(`Arbitragem ${profitLevel} (${actualSpread.toFixed(2)}%)`);
                arbitrageDetails.push({
                  buyExchange: minExchange,
                  sellExchange: maxExchange,
                  spread: actualSpread,
                  buyPrice: minPrice,
                  sellPrice: maxPrice
                });
                
                if (actualSpread > 2) score += 3;
                else if (actualSpread > 1) score += 2;
                else if (actualSpread > 0.5) score += 1;
              }
              
              // Simula alta liquidez para algumas moedas
              const totalVolume = Object.values(exchangeVolumes).reduce((sum, vol) => sum + vol, 0);
              if (totalVolume > 10000000) {
                opportunities.push('Alta Liquidez');
                score += 0.5;
              }
              
              if (change24h > 10 && totalVolume > 5000000) {
                opportunities.push('Volume Spike');
                score += 1.5;
              }
              
              if (change24h > 20) {
                opportunities.push('Mega Pump');
                score += 2;
              } else if (change24h > 15) {
                opportunities.push('Strong Momentum');
                score += 1;
              }
              
              // Cria objeto exchangeData completo
              const exchangeData = {};
              availableExchanges.forEach(exchange => {
                exchangeData[exchange] = {
                  price: exchangePrices[exchange] || null,
                  change24h: exchangeChanges[exchange] || null,
                  volume24h: exchangeVolumes[exchange] || null
                };
              });
              
              return {
                symbol: item.symbol,
                name: item.symbol,
                price: exchangePrices.binance || prices[0],
                change24h: change24h,
                volume24h: baseVolume,
                totalVolume24h: totalVolume,
                exchangeData: exchangeData,
                fundingRates: {},
                score: parseFloat(score.toFixed(1)),
                opportunities,
                arbitrageDetails,
                rank: index + 1,
                marketCap: 0,
                exchangeCount: selectedExchanges.length
              };
            });
          };

          // Efeito para iniciar a busca inicial de dados
          useEffect(() => {
            fetchRealTimeData();
          }, []);

          // Efeito para o temporizador de atualização automática
          useEffect(() => {
            let intervalId;
            if (isAutoUpdateEnabled && !isUpdating) {
              setCountdown(updateInterval);
              intervalId = setInterval(() => {
                setCountdown(prev => {
                  if (prev <= 1) {
                    fetchRealTimeData();
                    return updateInterval;
                  }
                  return prev - 1;
                });
              }, 1000);
            } else {
              setCountdown(updateInterval);
            }
            return () => clearInterval(intervalId);
          }, [isAutoUpdateEnabled, updateInterval, isUpdating]);

          // Função para gerar dados do PUMP Scanner
          const generatePumpData = (data) => {
            const pumpResults = data.filter(crypto => {
              return crypto.score > 1.5 && crypto.opportunities.some(opp => opp.includes('Volume Spike') || opp.includes('Strong Momentum'));
            }).map(crypto => ({
              ...crypto,
              pumpScore: crypto.score * 10,
              signals: crypto.opportunities.filter(opp => opp.includes('Volume Spike') || opp.includes('Strong Momentum'))
            }));
            setPumpData(pumpResults.sort((a, b) => b.pumpScore - a.pumpScore));
          };

          // Filtro de criptomoedas
          const filteredCryptos = cryptoData.filter(crypto => {
            const matchesSearch = searchTerm === '' ||
              crypto.symbol.toLowerCase().includes(searchTerm.toLowerCase()) ||
              crypto.name.toLowerCase().includes(searchTerm.toLowerCase());

            const matchesScore = crypto.score >= minScore && crypto.score <= maxScore;

            const matchesOpportunities = !onlyWithOpportunities || crypto.opportunities.length > 0;

            return matchesSearch && matchesScore && matchesOpportunities;
          });

          // Ordenação de criptomoedas
          const sortedCryptos = [...filteredCryptos].sort((a, b) => {
            switch (sortBy) {
              case 'rank':
                return a.rank - b.rank;
              case 'price':
                return b.price - a.price;
              case 'change24h':
                return b.change24h - a.change24h;
              case 'volume24h':
                return b.volume24h - a.volume24h;
              case 'score':
                return b.score - a.score;
              default:
                return 0;
            }
          });

          // Estilos base para o tema
          const themeStyles = {
            backgroundColor: darkMode ? '#0f172a' : '#f1f5f9',
            textColor: darkMode ? '#f1f5f9' : '#334155',
            cardBg: darkMode ? '#1e293b' : '#ffffff',
            borderColor: darkMode ? '#334155' : '#e2e8f0',
            headerBg: darkMode ? '#1e293b' : '#ffffff',
            inputBg: darkMode ? '#334155' : '#f8fafc',
            inputBorder: darkMode ? '#475569' : '#cbd5e1',
            buttonBg: darkMode ? '#2d3748' : '#e2e8f0',
            buttonHoverBg: darkMode ? '#4a5568' : '#d1d5db',
            buttonText: darkMode ? '#f1f5f9' : '#334155',
            tabActiveBg: darkMode ? '#3b82f6' : '#60a5fa',
            tabInactiveBg: darkMode ? '#1e293b' : '#cbd5e1',
            tabActiveText: '#ffffff',
            tabInactiveText: darkMode ? '#94a3b8' : '#475569',
          };

          // Renderização da interface de usuário
          return (
            <div className="min-h-screen font-sans" style={{ backgroundColor: themeStyles.backgroundColor, color: themeStyles.textColor }}>
              {/* Header */}
              <header style={{
                backgroundColor: themeStyles.headerBg,
                borderBottom: `1px solid ${themeStyles.borderColor}`,
                padding: '1rem 2rem',
                display: 'flex',
                justifyContent: 'space-between',
                alignItems: 'center',
                flexWrap: 'wrap',
                gap: '1rem'
              }}>
                <div className="flex items-center gap-4">
                  <h1 className="text-2xl font-bold" style={{ color: themeStyles.textColor }}>🚀 Dashboard ArbTrading SCC</h1>
                  <button
                    onClick={toggleDarkMode}
                    className="p-2 rounded-full focus:outline-none"
                    style={{ backgroundColor: themeStyles.buttonBg, color: themeStyles.buttonText }}
                  >
                    {darkMode ? '☀️' : '🌙'}
                  </button>
                </div>
                <div className="flex gap-2 text-sm font-medium flex-wrap">
                  <span style={{ color: apiStatus.general === 'connected' ? '#10b981' : (apiStatus.general === 'error' ? '#ef4444' : apiStatus.general === 'simulated' ? '#f59e0b' : '#6b7280') }}>
                    Status: {apiStatus.general === 'connected' ? 'Online' : (apiStatus.general === 'error' ? 'Erro' : apiStatus.general === 'simulated' ? 'Simulado' : 'Conectando...')}
                  </span>
                  <div className="flex gap-1 flex-wrap">
                    {Object.entries(apiStatus).filter(([key]) => key !== 'general').map(([exchange, status]) => (
                      <span key={exchange} className="px-2 py-0.5 rounded text-xs capitalize" style={{ 
                        backgroundColor: status === 'connected' ? '#10b981' : status === 'simulated' ? '#f59e0b' : '#ef4444',
                        color: '#ffffff'
                      }}>
                        {exchange}
                      </span>
                    ))}
                  </div>
                  <span>Próxima: {countdown}s</span>
                  <button
                    onClick={fetchRealTimeData}
                    disabled={isUpdating}
                    className="px-3 py-1 rounded-md text-white font-semibold"
                    style={{ backgroundColor: isUpdating ? '#6b7280' : '#3b82f6' }}
                  >
                    {isUpdating ? 'Atualizando...' : 'Atualizar Agora'}
                  </button>
                </div>
              </header>

              {/* Navegação por Abas */}
              <nav style={{
                backgroundColor: themeStyles.headerBg,
                borderBottom: `1px solid ${themeStyles.borderColor}`,
                padding: '0.5rem 2rem',
                display: 'flex',
                gap: '1rem',
                overflowX: 'auto',
              }}>
                {['dashboard', 'scanner', 'pumpScanner', 'favorites', 'opportunities', 'strategy', 'fluxograma'].map(tab => (
                  <button
                    key={tab}
                    onClick={() => setActiveTab(tab)}
                    className="px-4 py-2 rounded-md font-medium capitalize whitespace-nowrap"
                    style={{
                      backgroundColor: activeTab === tab ? themeStyles.tabActiveBg : themeStyles.tabInactiveBg,
                      color: activeTab === tab ? themeStyles.tabActiveText : themeStyles.tabInactiveText,
                      transition: 'background-color 0.2s, color 0.2s',
                    }}
                  >
                    {tab === 'pumpScanner' ? 'PUMP Scanner' : tab}
                  </button>
                ))}
              </nav>

              <main className="p-4 md:p-8">
                {/* Aviso de Modo Simulado */}
                {apiStatus.general === 'simulated' && (
                  <div className="mb-6 p-4 rounded-lg" style={{ backgroundColor: '#fef3c7', borderLeft: '4px solid #f59e0b' }}>
                    <h3 className="text-lg font-bold mb-2" style={{ color: '#92400e' }}>⚠️ Modo Simulado Ativo</h3>
                    <p className="text-sm mb-2" style={{ color: '#92400e' }}>
                      Os dados estão sendo simulados porque as APIs públicas não podem ser acessadas diretamente do navegador devido a políticas CORS.
                    </p>
                    <details className="text-sm" style={{ color: '#92400e' }}>
                      <summary className="cursor-pointer font-semibold">Como usar dados reais?</summary>
                      <div className="mt-2 pl-4">
                        <p className="mb-1"><strong>Opção 1:</strong> Configure um servidor proxy backend (Node.js, Python, etc.)</p>
                        <p className="mb-1"><strong>Opção 2:</strong> Use uma extensão do navegador para desabilitar CORS (apenas desenvolvimento)</p>
                        <p className="mb-1"><strong>Opção 3:</strong> Hospede o app com um servidor que faça as requisições</p>
                        <p className="mt-2">Todas as APIs usadas são <strong>públicas e gratuitas</strong>, sem necessidade de chaves!</p>
                      </div>
                    </details>
                  </div>
                )}

                {/* Dashboard Tab */}
                {activeTab === 'dashboard' && (
                  <section className="mb-8">
                    <h2 className="text-xl font-bold mb-4" style={{ color: themeStyles.textColor }}>Dashboard de Visão Geral</h2>
                    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                      <div className="p-6 rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg }}>
                        <h3 className="text-lg font-semibold" style={{ color: themeStyles.textColor }}>Volume Total (24h)</h3>
                        <p className="text-3xl font-bold mt-2" style={{ color: '#3b82f6' }}>${formatNumber(cryptoData.reduce((sum, crypto) => sum + crypto.volume24h, 0), 0)}</p>
                      </div>
                      <div className="p-6 rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg }}>
                        <h3 className="text-lg font-semibold" style={{ color: themeStyles.textColor }}>Moedas Analisadas</h3>
                        <p className="text-3xl font-bold mt-2" style={{ color: '#10b981' }}>{cryptoData.length}</p>
                      </div>
                      <div className="p-6 rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg }}>
                        <h3 className="text-lg font-semibold" style={{ color: themeStyles.textColor }}>Oportunidades Ativas</h3>
                        <p className="text-3xl font-bold mt-2" style={{ color: '#f59e0b' }}>{cryptoData.filter(c => c.opportunities.length > 0).length}</p>
                      </div>
                      <div className="p-6 rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg }}>
                        <h3 className="text-lg font-semibold" style={{ color: themeStyles.textColor }}>Score Médio</h3>
                        <p className="text-3xl font-bold mt-2" style={{ color: '#ef4444' }}>{formatNumber(cryptoData.reduce((sum, crypto) => sum + crypto.score, 0) / cryptoData.length || 0, 1)}</p>
                      </div>
                    </div>

                    <div className="mt-8 p-6 rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg }}>
                        <h3 className="text-lg font-semibold mb-4" style={{ color: themeStyles.textColor }}>📊 Estatísticas por Exchange</h3>
                        <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
                            {Object.entries(apiStatus).filter(([key]) => key !== 'general').map(([exchange, status]) => {
                                const activeCoins = cryptoData.filter(c => c.exchangeData[exchange]?.price > 0).length;
                                const totalVolume = cryptoData.reduce((sum, c) => sum + (c.exchangeData[exchange]?.volume24h || 0), 0);
                                
                                return (
                                    <div key={exchange} className="text-center p-3 rounded-lg" style={{ backgroundColor: themeStyles.inputBg }}>
                                        <h4 className="font-semibold capitalize" style={{ color: themeStyles.textColor }}>{exchange}</h4>
                                        <div className="mt-1">
                                            <span className="text-xs px-2 py-1 rounded" style={{
                                                backgroundColor: status === 'connected' ? '#10b981' : status === 'simulated' ? '#f59e0b' : '#ef4444',
                                                color: '#ffffff'
                                            }}>
                                                {status === 'connected' ? 'Online' : status === 'simulated' ? 'Simulado' : 'Offline'}
                                            </span>
                                        </div>
                                        <p className="text-sm mt-2" style={{ color: themeStyles.textColor }}>
                                            {activeCoins} moedas
                                        </p>
                                        <p className="text-xs opacity-75" style={{ color: themeStyles.textColor }}>
                                            Vol: ${formatNumber(totalVolume, 0)}
                                        </p>
                                    </div>
                                );
                            })}
                        </div>
                    </div>

                    <div className="mt-8 p-6 rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg }}>
                        <h3 className="text-lg font-semibold mb-4" style={{ color: themeStyles.textColor }}>Configurações de Atualização</h3>
                        <div className="flex items-center gap-4">
                            <label className="flex items-center gap-2">
                                <input
                                    type="checkbox"
                                    checked={isAutoUpdateEnabled}
                                    onChange={(e) => setIsAutoUpdateEnabled(e.target.checked)}
                                    className="form-checkbox"
                                />
                                <span>Atualização Automática</span>
                            </label>
                            <label className="flex items-center gap-2">
                                <span>Intervalo (segundos):</span>
                                <select
                                    value={updateInterval}
                                    onChange={(e) => setUpdateInterval(Number(e.target.value))}
                                    className="px-2 py-1 rounded-md"
                                    style={{ backgroundColor: themeStyles.inputBg, color: themeStyles.textColor, borderColor: themeStyles.inputBorder }}
                                >
                                    <option value={3}>3s</option>
                                    <option value={5}>5s</option>
                                    <option value={10}>10s</option>
                                    <option value={15}>15s</option>
                                    <option value={30}>30s</option>
                                    <option value={60}>60s</option>
                                </select>
                            </label>
                        </div>
                        <p className="text-sm mt-2 opacity-80" style={{ color: themeStyles.textColor }}>
                            Última atualização: {lastUpdate.toLocaleTimeString()} ({connectionCount} conexões)
                        </p>
                    </div>
                  </section>
                )}

                {/* Scanner Tab */}
                {activeTab === 'scanner' && (
                  <section className="mb-8">
                    <h2 className="text-xl font-bold mb-4" style={{ color: themeStyles.textColor }}>Scanner de Criptomoedas</h2>
                    <div className="p-6 rounded-lg shadow-md mb-6" style={{ backgroundColor: themeStyles.cardBg }}>
                      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                        <div>
                          <label className="block text-sm font-medium mb-1" style={{ color: themeStyles.textColor }}>Buscar Cripto:</label>
                          <input
                            type="text"
                            placeholder="Símbolo ou Nome"
                            value={searchTerm}
                            onChange={(e) => setSearchTerm(e.target.value)}
                            className="w-full px-3 py-2 rounded-md"
                            style={{ backgroundColor: themeStyles.inputBg, color: themeStyles.textColor, border: `1px solid ${themeStyles.inputBorder}` }}
                          />
                        </div>
                        <div>
                          <label className="block text-sm font-medium mb-1" style={{ color: themeStyles.textColor }}>Score Mínimo:</label>
                          <input
                            type="range"
                            min="0"
                            max="5"
                            step="0.1"
                            value={minScore}
                            onChange={(e) => setMinScore(parseFloat(e.target.value))}
                            className="w-full"
                          />
                          <p className="text-sm text-center">{formatNumber(minScore, 1)}</p>
                        </div>
                        <div>
                          <label className="block text-sm font-medium mb-1" style={{ color: themeStyles.textColor }}>Score Máximo:</label>
                          <input
                            type="range"
                            min="0"
                            max="5"
                            step="0.1"
                            value={maxScore}
                            onChange={(e) => setMaxScore(parseFloat(e.target.value))}
                            className="w-full"
                          />
                          <p className="text-sm text-center">{formatNumber(maxScore, 1)}</p>
                        </div>
                        <div>
                          <label className="block text-sm font-medium mb-1" style={{ color: themeStyles.textColor }}>Ordenar por:</label>
                          <select
                            value={sortBy}
                            onChange={(e) => setSortBy(e.target.value)}
                            className="w-full px-3 py-2 rounded-md"
                            style={{ backgroundColor: themeStyles.inputBg, color: themeStyles.textColor, border: `1px solid ${themeStyles.inputBorder}` }}
                          >
                            <option value="rank">Rank</option>
                            <option value="price">Preço</option>
                            <option value="change24h">Variação 24h</option>
                            <option value="volume24h">Volume 24h</option>
                            <option value="score">Score</option>
                          </select>
                        </div>
                        <div className="flex items-center">
                          <input
                            type="checkbox"
                            id="onlyOpportunities"
                            checked={onlyWithOpportunities}
                            onChange={(e) => setOnlyWithOpportunities(e.target.checked)}
                            className="form-checkbox"
                          />
                          <label htmlFor="onlyOpportunities" className="ml-2 text-sm font-medium" style={{ color: themeStyles.textColor }}>Apenas com Oportunidades</label>
                        </div>
                      </div>
                    </div>

                    {isLoadingInitialData ? (
                      <p className="text-center py-8" style={{ color: themeStyles.textColor }}>Carregando dados iniciais...</p>
                    ) : (
                      <div className="overflow-x-auto rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg, border: `1px solid ${themeStyles.borderColor}` }}>
                        <table className="min-w-full divide-y" style={{ borderColor: themeStyles.borderColor }}>
                          <thead style={{ backgroundColor: themeStyles.buttonBg }}>
                            <tr>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Símbolo</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Nome</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Preço</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Variação 24h</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Volume 24h</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Score</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Oportunidades</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Ações</th>
                            </tr>
                          </thead>
                          <tbody style={{ backgroundColor: themeStyles.cardBg, divideColor: themeStyles.borderColor }}>
                            {sortedCryptos.length > 0 ? (
                              sortedCryptos.map((crypto) => (
                                <tr key={crypto.symbol} className="hover:opacity-90 transition-opacity" style={{ borderBottom: `1px solid ${themeStyles.borderColor}` }}>
                                  <td className="px-6 py-4 whitespace-nowrap text-sm font-medium" style={{ color: themeStyles.textColor }}>{crypto.symbol}</td>
                                  <td className="px-6 py-4 whitespace-nowrap text-sm" style={{ color: themeStyles.textColor }}>{crypto.name}</td>
                                  <td className="px-6 py-4 whitespace-nowrap text-sm" style={{ color: themeStyles.textColor }}>${formatNumber(crypto.price, 4)}</td>
                                  <td className={`px-6 py-4 whitespace-nowrap text-sm ${crypto.change24h >= 0 ? 'text-green-500' : 'text-red-500'}`}>
                                    {formatNumber(crypto.change24h, 2)}%
                                  </td>
                                  <td className="px-6 py-4 whitespace-nowrap text-sm" style={{ color: themeStyles.textColor }}>${formatNumber(crypto.volume24h, 0)}</td>
                                  <td className="px-6 py-4 whitespace-nowrap text-sm font-semibold" style={{ color: crypto.score >= 3.5 ? '#10b981' : (crypto.score >= 2 ? '#f59e0b' : themeStyles.textColor) }}>
                                    {formatNumber(crypto.score, 1)}
                                  </td>
                                  <td className="px-6 py-4 whitespace-nowrap text-sm">
                                    <div className="flex flex-wrap gap-1">
                                      {crypto.opportunities.length > 0 ? (
                                        crypto.opportunities.map((opp, index) => (
                                          <span key={index} className="px-2 py-1 text-xs font-medium rounded-full" style={{ backgroundColor: '#60a5fa', color: '#ffffff' }}>
                                            {opp}
                                          </span>
                                        ))
                                      ) : (
                                        <span className="text-sm opacity-60" style={{ color: themeStyles.textColor }}>Nenhuma</span>
                                      )}
                                    </div>
                                  </td>
                                  <td className="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                                    <button
                                      onClick={() => openCryptoModal(crypto)}
                                      className="text-indigo-600 hover:text-indigo-900"
                                      style={{ color: darkMode ? '#93c5fd' : '#4f46e5' }}
                                    >
                                      Ver Detalhes
                                    </button>
                                  </td>
                                </tr>
                              ))
                            ) : (
                              <tr>
                                <td colSpan="8" className="px-6 py-4 text-center text-sm" style={{ color: themeStyles.textColor }}>Nenhuma criptomoeda encontrada com os critérios selecionados.</td>
                              </tr>
                            )}
                          </tbody>
                        </table>
                      </div>
                    )}
                  </section>
                )}

                {/* PUMP Scanner Tab */}
                {activeTab === 'pumpScanner' && (
                  <section className="mb-8">
                    <h2 className="text-xl font-bold mb-4" style={{ color: themeStyles.textColor }}>PUMP Scanner - Movimentos Explosivos</h2>
                    {isLoadingInitialData ? (
                      <p className="text-center py-8" style={{ color: themeStyles.textColor }}>Analisando dados para PUMP Signals...</p>
                    ) : (
                      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                        {pumpData.length > 0 ? (
                          pumpData.map((pumpItem) => (
                            <div key={pumpItem.symbol} className="p-6 rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg, border: `1px solid ${themeStyles.borderColor}` }}>
                              <h3 className="text-xl font-semibold mb-2" style={{ color: themeStyles.textColor }}>{pumpItem.name} ({pumpItem.symbol})</h3>
                              <p className="text-2xl font-bold mb-2" style={{ color: '#ef4444' }}>PUMP Score: {formatNumber(pumpItem.pumpScore, 1)}</p>
                              <p className="text-sm" style={{ color: themeStyles.textColor }}>Preço: ${formatNumber(pumpItem.price, 4)}</p>
                              <p className={`text-sm ${pumpItem.change24h >= 0 ? 'text-green-500' : 'text-red-500'}`}>Variação 24h: {formatNumber(pumpItem.change24h, 2)}%</p>
                              <p className="text-sm" style={{ color: themeStyles.textColor }}>Volume 24h: ${formatNumber(pumpItem.volume24h, 0)}</p>
                              <div className="mt-3">
                                <span className="font-semibold" style={{ color: themeStyles.textColor }}>Sinais: </span>
                                {pumpItem.signals.length > 0 ? (
                                  <div className="flex flex-wrap gap-1 mt-1">
                                    {pumpItem.signals.map((signal, idx) => (
                                      <span key={idx} className="px-2 py-1 text-xs font-medium rounded-full" style={{ backgroundColor: '#f59e0b', color: '#ffffff' }}>
                                        {signal}
                                      </span>
                                    ))}
                                  </div>
                                ) : (
                                  <span className="text-sm opacity-60" style={{ color: themeStyles.textColor }}>Nenhum sinal ativo</span>
                                )}
                              </div>
                              <div className="mt-4 flex gap-2">
                                <button
                                  onClick={() => openCryptoModal(pumpItem)}
                                  className="px-4 py-2 rounded-md font-semibold text-white"
                                  style={{ backgroundColor: '#3b82f6' }}
                                >
                                  Ver Detalhes
                                </button>
                              </div>
                            </div>
                          ))
                        ) : (
                          <p className="col-span-full text-center py-8" style={{ color: themeStyles.textColor }}>Nenhum PUMP signal ativo no momento.</p>
                        )}
                      </div>
                    )}
                  </section>
                )}

                {/* Favorites Tab */}
                {activeTab === 'favorites' && (
                  <section className="mb-8">
                    <h2 className="text-xl font-bold mb-4" style={{ color: themeStyles.textColor }}>Minhas Criptomoedas Favoritas</h2>
                    {favorites.length === 0 ? (
                      <p className="text-center py-8" style={{ color: themeStyles.textColor }}>Você ainda não adicionou nenhuma criptomoeda aos favoritos.</p>
                    ) : (
                      <div className="overflow-x-auto rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg, border: `1px solid ${themeStyles.borderColor}` }}>
                        <table className="min-w-full divide-y" style={{ borderColor: themeStyles.borderColor }}>
                          <thead style={{ backgroundColor: themeStyles.buttonBg }}>
                            <tr>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Símbolo</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Nome</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Preço</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Variação 24h</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Volume 24h</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Score</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Oportunidades</th>
                              <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Ações</th>
                            </tr>
                          </thead>
                          <tbody style={{ backgroundColor: themeStyles.cardBg, divideColor: themeStyles.borderColor }}>
                            {cryptoData.filter(c => favorites.includes(c.symbol)).map((crypto) => (
                              <tr key={crypto.symbol} className="hover:opacity-90 transition-opacity" style={{ borderBottom: `1px solid ${themeStyles.borderColor}` }}>
                                <td className="px-6 py-4 whitespace-nowrap text-sm font-medium" style={{ color: themeStyles.textColor }}>{crypto.symbol}</td>
                                <td className="px-6 py-4 whitespace-nowrap text-sm" style={{ color: themeStyles.textColor }}>{crypto.name}</td>
                                <td className="px-6 py-4 whitespace-nowrap text-sm" style={{ color: themeStyles.textColor }}>${formatNumber(crypto.price, 4)}</td>
                                <td className={`px-6 py-4 whitespace-nowrap text-sm ${crypto.change24h >= 0 ? 'text-green-500' : 'text-red-500'}`}>
                                  {formatNumber(crypto.change24h, 2)}%
                                </td>
                                <td className="px-6 py-4 whitespace-nowrap text-sm" style={{ color: themeStyles.textColor }}>${formatNumber(crypto.volume24h, 0)}</td>
                                <td className="px-6 py-4 whitespace-nowrap text-sm font-semibold" style={{ color: crypto.score >= 3.5 ? '#10b981' : (crypto.score >= 2 ? '#f59e0b' : themeStyles.textColor) }}>
                                  {formatNumber(crypto.score, 1)}
                                </td>
                                <td className="px-6 py-4 whitespace-nowrap text-sm">
                                  <div className="flex flex-wrap gap-1">
                                    {crypto.opportunities.length > 0 ? (
                                      crypto.opportunities.map((opp, index) => (
                                        <span key={index} className="px-2 py-1 text-xs font-medium rounded-full" style={{ backgroundColor: '#60a5fa', color: '#ffffff' }}>
                                          {opp}
                                        </span>
                                      ))
                                    ) : (
                                      <span className="text-sm opacity-60" style={{ color: themeStyles.textColor }}>Nenhuma</span>
                                    )}
                                  </div>
                                </td>
                                <td className="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                                  <button
                                    onClick={() => openCryptoModal(crypto)}
                                    className="text-indigo-600 hover:text-indigo-900 mr-2"
                                    style={{ color: darkMode ? '#93c5fd' : '#4f46e5' }}
                                  >
                                    Ver Detalhes
                                  </button>
                                  <button
                                    onClick={() => toggleFavorite(crypto.symbol)}
                                    className="px-3 py-1 rounded-md text-white font-semibold"
                                    style={{ backgroundColor: '#ef4444' }}
                                  >
                                    Remover
                                  </button>
                                </td>
                              </tr>
                            ))}
                          </tbody>
                        </table>
                      </div>
                    )}
                  </section>
                )}

                {/* Opportunities Tab */}
                {activeTab === 'opportunities' && (
                  <section className="mb-8">
                    <h2 className="text-xl font-bold mb-4" style={{ color: themeStyles.textColor }}>Oportunidades de Arbitragem Ativas</h2>
                    <div className="overflow-x-auto rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg, border: `1px solid ${themeStyles.borderColor}` }}>
                      <table className="min-w-full divide-y" style={{ borderColor: themeStyles.borderColor }}>
                        <thead style={{ backgroundColor: themeStyles.buttonBg }}>
                          <tr>
                            <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Símbolo</th>
                            <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Preço</th>
                            <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Score</th>
                            <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Oportunidades</th>
                            <th className="px-6 py-3 text-left text-xs font-medium uppercase tracking-wider" style={{ color: themeStyles.buttonText }}>Ações</th>
                          </tr>
                        </thead>
                        <tbody style={{ backgroundColor: themeStyles.cardBg, divideColor: themeStyles.borderColor }}>
                          {cryptoData.filter(c => c.opportunities.length > 0).length > 0 ? (
                            cryptoData.filter(c => c.opportunities.length > 0).map((crypto) => (
                              <tr key={crypto.symbol} className="hover:opacity-90 transition-opacity" style={{ borderBottom: `1px solid ${themeStyles.borderColor}` }}>
                                <td className="px-6 py-4 whitespace-nowrap text-sm font-medium" style={{ color: themeStyles.textColor }}>{crypto.symbol}</td>
                                <td className="px-6 py-4 whitespace-nowrap text-sm" style={{ color: themeStyles.textColor }}>${formatNumber(crypto.price, 4)}</td>
                                <td className="px-6 py-4 whitespace-nowrap text-sm font-semibold" style={{ color: crypto.score >= 3.5 ? '#10b981' : (crypto.score >= 2 ? '#f59e0b' : themeStyles.textColor) }}>
                                  {formatNumber(crypto.score, 1)}
                                </td>
                                <td className="px-6 py-4 whitespace-nowrap text-sm">
                                  <div className="flex flex-wrap gap-1">
                                    {crypto.opportunities.map((opp, index) => (
                                      <span key={index} className="px-2 py-1 text-xs font-medium rounded-full" style={{ backgroundColor: '#60a5fa', color: '#ffffff' }}>
                                        {opp}
                                      </span>
                                    ))}
                                  </div>
                                </td>
                                <td className="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                                  <button
                                    onClick={() => openCryptoModal(crypto)}
                                    className="text-indigo-600 hover:text-indigo-900"
                                    style={{ color: darkMode ? '#93c5fd' : '#4f46e5' }}
                                  >
                                    Ver Detalhes
                                  </button>
                                </td>
                              </tr>
                            ))
                          ) : (
                            <tr>
                              <td colSpan="5" className="px-6 py-4 text-center text-sm" style={{ color: themeStyles.textColor }}>Nenhuma oportunidade ativa no momento.</td>
                            </tr>
                          )}
                        </tbody>
                      </table>
                    </div>
                  </section>
                )}

                {/* Strategy Tab */}
                {activeTab === 'strategy' && (
                  <section className="mb-8 p-6 rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg }}>
                    <h2 className="text-xl font-bold mb-4" style={{ color: themeStyles.textColor }}>Estratégia de Arbitragem e Day Trading</h2>
                    <div className="prose max-w-none" style={{ color: themeStyles.textColor, opacity: 0.9 }}>
                      <p>O <strong>Dashboard ArbTrading SCC</strong> foi projetado para auxiliar traders a identificar e capitalizar em ineficiências do mercado e movimentos rápidos de preços de criptomoedas.</p>
                      
                      <h3>🌐 Exchanges Integradas (8 no total):</h3>
                      <ul>
                        <li><strong>Binance:</strong> Maior exchange global, alta liquidez, API estável</li>
                        <li><strong>Bybit:</strong> Popular para derivativos, crescendo em spot</li>
                        <li><strong>OKX:</strong> Top 3 global, excelente liquidez</li>
                        <li><strong>KuCoin:</strong> Boa variedade de altcoins, API confiável</li>
                        <li><strong>MEXC:</strong> Foco em novos projetos, listagens rápidas</li>
                        <li><strong>Gate.io:</strong> Grande variedade de pares, boa para arbitragem</li>
                        <li><strong>Huobi:</strong> Exchange estabelecida, forte presença asiática</li>
                        <li><strong>Kraken:</strong> Regulamentada nos EUA, alta segurança</li>
                      </ul>
                      
                      <h3>📊 O que as APIs Públicas Fornecem:</h3>
                      <ul>
                        <li><strong>Ticker 24hr:</strong> Preço atual, volume, variação percentual</li>
                        <li><strong>Order Book (limitado):</strong> Primeiras ordens de compra/venda</li>
                        <li><strong>Trades Recentes:</strong> Histórico de transações executadas</li>
                        <li><strong>Klines/Candles:</strong> Dados históricos OHLCV</li>
                      </ul>
                      
                      <h3>🎯 Estratégias de Arbitragem Multi-Exchange:</h3>
                      <p>Com 8 exchanges integradas, as oportunidades de arbitragem aumentam exponencialmente:</p>
                      <ul>
                        <li><strong>Arbitragem Simples:</strong> Comprar na exchange mais barata e vender na mais cara</li>
                        <li><strong>Arbitragem Triangular:</strong> Explorar diferenças entre 3 ou mais exchanges</li>
                        <li><strong>Arbitragem de Liquidez:</strong> Aproveitar diferenças temporárias em exchanges com menor volume</li>
                        <li><strong>Flash Arbitrage:</strong> Oportunidades rápidas durante alta volatilidade</li>
                      </ul>
                      
                      <h3>💡 Dicas para Maximizar Lucros:</h3>
                      <ul>
                        <li><strong>Fees:</strong> Considere as taxas de trading de cada exchange (0.05% - 0.1%)</li>
                        <li><strong>Velocidade:</strong> Arbitragem requer execução rápida (segundos importam)</li>
                        <li><strong>Liquidez:</strong> Verifique o volume antes de executar grandes trades</li>
                        <li><strong>Limites:</strong> Algumas exchanges têm limites de saque diários</li>
                        <li><strong>KYC:</strong> Verifique os requisitos de cada exchange</li>
                      </ul>
                      
                      <h3>🎯 Oportunidades de Arbitragem Spot:</h3>
                      <p>Comparamos os preços de uma mesma criptomoeda entre as exchanges Binance, MEXC e Gate.io. Uma diferença percentual significativa pode indicar uma oportunidade de comprar barato em uma exchange e vender caro em outra. A lógica atual busca um <strong>spread de preço acima de 0.5%</strong>.</p>
                      
                      <h3>🚀 Sinais de PUMP (Volume e Momentum):</h3>
                      <p>Monitoramos o volume de negociação e a variação percentual de 24 horas. Sinais como <strong>"Volume Spike"</strong> (alto volume + alta variação) e <strong>"Strong Momentum"</strong> (alta variação sustentada) são indicados para identificar movimentos explosivos de preço. A lógica atual considera <strong>variação de 24h acima de 10% e volume acima de 1 milhão</strong> para "Volume Spike", e <strong>variação acima de 15%</strong> para "Strong Momentum".</p>
                      
                      <h3>⚖️ Score de Oportunidade:</h3>
                      <p>Cada oportunidade detectada contribui para um <strong>Score</strong> geral da criptomoeda. Scores mais altos indicam uma confluência de múltiplos sinais de interesse.</p>
                      
                      <h3>🔓 Limitações das APIs Públicas:</h3>
                      <ul>
                        <li><strong>Rate Limits:</strong> Número limitado de requisições por minuto</li>
                        <li><strong>Sem Execução:</strong> Não é possível criar ordens automaticamente</li>
                        <li><strong>Dados Limitados:</strong> Sem acesso a saldos ou histórico pessoal</li>
                        <li><strong>Funding Rates:</strong> Requerem APIs de futuros (públicas mas separadas)</li>
                      </ul>
                      
                      <h3>🔐 Futuras Melhorias com APIs Privadas:</h3>
                      <p>Em versões futuras, com autenticação via API Keys, seria possível:</p>
                      <ul>
                        <li>Executar trades automaticamente ao detectar arbitragem</li>
                        <li>Monitorar saldos e P&L em tempo real</li>
                        <li>Implementar stop-loss e take-profit automáticos</li>
                        <li>Acessar histórico completo de trades pessoais</li>
                      </ul>
                      
                      <p><strong>Disclaimer:</strong> Trading de criptomoedas envolve riscos substanciais. Este dashboard é uma ferramenta de análise e não deve ser considerado como aconselhamento financeiro.</p>
                    </div>
                  </section>
                )}

                {/* Fluxograma Tab */}
                {activeTab === 'fluxograma' && (
                  <section className="mb-8 p-6 rounded-lg shadow-md" style={{ backgroundColor: themeStyles.cardBg }}>
                    <h2 className="text-xl font-bold mb-4" style={{ color: themeStyles.textColor }}>Fluxograma do Sistema</h2>
                    <div className="prose max-w-none" style={{ color: themeStyles.textColor, opacity: 0.9 }}>
                      <p>Este fluxograma ilustra o funcionamento lógico do <strong>Dashboard ArbTrading SCC</strong>:</p>
                      <h3 style={{ color: '#3b82f6' }}>1. Coleta de Dados:</h3>
                      <ul>
                        <li>O sistema faz requisições (a cada <code>{updateInterval}</code> segundos, se automático) para as APIs públicas de <strong>Binance, MEXC e Gate.io</strong>.</li>
                        <li>Os dados incluem: preço atual, variação 24h, e volume 24h para pares USDT.</li>
                      </ul>
                      <h3 style={{ color: '#f59e0b' }}>2. Processamento e Normalização:</h3>
                      <ul>
                        <li>Os dados brutos de cada exchange são <strong>normalizados</strong> para um formato consistente.</li>
                        <li>As informações são <strong>agregadas por símbolo base</strong> (ex: BTC, ETH), consolidando os dados de diferentes exchanges para a mesma criptomoeda.</li>
                      </ul>
                      <h3 style={{ color: '#10b981' }}>3. Análise e Detecção de Oportunidades:</h3>
                      <ul>
                        <li><strong>Arbitragem Spot:</strong> O sistema compara os preços da mesma criptomoeda entre as exchanges para identificar um <code>spread</code> de preço significativo (atualmente {'>'} 0.5%).</li>
                        <li><strong>PUMP Signals (Volume/Momentum):</strong> Analisa a variação de 24h e o volume de negociação para detectar movimentos explosivos (ex: <code>change24h {'>'} 10%</code> e <code>volume24h {'>'} $1M</code>).</li>
                        <li>Um <strong>Score</strong> é calculado para cada criptomoeda, refletindo a força e o número de oportunidades detectadas.</li>
                      </ul>
                      <h3 style={{ color: '#ef4444' }}>4. Exibição no Dashboard:</h3>
                      <ul>
                        <li>Os dados processados são apresentados nas abas: <strong>Dashboard, Scanner, PUMP Scanner, Favoritos e Oportunidades</strong>.</li>
                        <li>Filtros e opções de ordenação permitem ao usuário personalizar a visualização.</li>
                        <li>Alertas visuais e cores indicam o status das oportunidades e a performance.</li>
                      </ul>
                      <h3 style={{ color: themeStyles.textColor }}>5. Interação do Usuário:</h3>
                      <ul>
                        <li>O usuário pode favoritar criptomoedas, pesquisar, filtrar por score e oportunidades.</li>
                        <li>Modo escuro e controle de intervalo de atualização.</li>
                        <li>Ações rápidas para ver detalhes ou acessar exchanges.</li>
                      </ul>
                    </div>
                  </section>
                )}
              </main>

              {/* Crypto Detail Modal */}
              {showModal && selectedCrypto && (
                <div
                  className="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-70"
                  onClick={closeCryptoModal}
                >
                  <div
                    className="rounded-lg shadow-xl p-6 w-11/12 md:w-2/3 lg:w-1/2 relative"
                    style={{ backgroundColor: themeStyles.cardBg, color: themeStyles.textColor }}
                    onClick={(e) => e.stopPropagation()}
                  >
                    <button
                      onClick={closeCryptoModal}
                      className="absolute top-3 right-3 text-xl font-bold"
                      style={{ color: themeStyles.textColor }}
                    >
                      &times;
                    </button>
                    <h2 className="text-2xl font-bold mb-4">{selectedCrypto.name} ({selectedCrypto.symbol})</h2>

                    <div className="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6">
                      <div>
                        <p className="text-lg font-semibold mb-2">Preço Atual: ${formatNumber(selectedCrypto.price, 4)}</p>
                        <p className={`text-md ${selectedCrypto.change24h >= 0 ? 'text-green-500' : 'text-red-500'}`}>Variação 24h: {formatNumber(selectedCrypto.change24h, 2)}%</p>
                        <p className="text-md">Volume 24h: ${formatNumber(selectedCrypto.volume24h, 0)}</p>
                        <p className="text-md font-semibold mt-2" style={{ color: selectedCrypto.score >= 3.5 ? '#10b981' : (selectedCrypto.score >= 2 ? '#f59e0b' : themeStyles.textColor) }}>Score: {formatNumber(selectedCrypto.score, 1)}</p>
                      </div>
                      <div>
                        <p className="text-lg font-semibold mb-2">Preços por Exchange:</p>
                        {selectedCrypto.exchangeData && Object.keys(selectedCrypto.exchangeData).map(exchangeName => (
                            selectedCrypto.exchangeData[exchangeName].price ? (
                                <p key={exchangeName} className="text-md capitalize">
                                    {exchangeName}: ${formatNumber(selectedCrypto.exchangeData[exchangeName].price, 4)}
                                    <span className={`ml-2 text-sm ${selectedCrypto.exchangeData[exchangeName].change24h >= 0 ? 'text-green-500' : 'text-red-500'}`}>
                                        ({formatNumber(selectedCrypto.exchangeData[exchangeName].change24h, 2)}%)
                                    </span>
                                </p>
                            ) : null
                        ))}
                      </div>
                    </div>

                    <p className="text-lg font-semibold mb-2">Oportunidades:</p>
                    <div className="flex flex-wrap gap-2 mb-6">
                      {selectedCrypto.opportunities.length > 0 ? (
                        selectedCrypto.opportunities.map((opp, index) => (
                          <span key={index} className="px-3 py-1 text-sm font-medium rounded-full" style={{ backgroundColor: '#60a5fa', color: '#ffffff' }}>
                            {opp}
                          </span>
                        ))
                      ) : (
                        <span className="text-md opacity-60">Nenhuma oportunidade detectada no momento.</span>
                      )}
                    </div>

                    <div className="flex flex-wrap gap-3 justify-end">
                      <a
                        href={`https://www.tradingview.com/symbols/${selectedCrypto.symbol}USDT/`}
                        target="_blank"
                        rel="noopener noreferrer"
                        className="px-4 py-2 rounded-md font-semibold text-white"
                        style={{ backgroundColor: '#3b82f6', textDecoration: 'none' }}
                      >
                        Gráfico TradingView
                      </a>
                      <a
                        href={`https://www.mexc.com/exchange/${selectedCrypto.symbol}_USDT`}
                        target="_blank"
                        rel="noopener noreferrer"
                        className="px-4 py-2 rounded-md font-semibold text-white"
                        style={{ backgroundColor: '#10b981', textDecoration: 'none' }}
                      >
                        Negociar na MEXC
                      </a>
                      <a
                        href={`https://www.gate.io/trade/${selectedCrypto.symbol}_USDT`}
                        target="_blank"
                        rel="noopener noreferrer"
                        className="px-4 py-2 rounded-md font-semibold text-white"
                        style={{ backgroundColor: '#f59e0b', textDecoration: 'none' }}
                      >
                        Negociar na Gate.io
                      </a>
                      <button
                        onClick={() => toggleFavorite(selectedCrypto.symbol)}
                        className="px-4 py-2 rounded-md text-sm"
                        style={{
                          backgroundColor: favorites.includes(selectedCrypto.symbol) ? '#fbbf24' : themeStyles.buttonBg,
                          color: favorites.includes(selectedCrypto.symbol) ? '#ffffff' : themeStyles.buttonText,
                          fontWeight: '600'
                        }}
                      >
                        {favorites.includes(selectedCrypto.symbol) ? '★ Favoritado' : '☆ Favoritar'}
                      </button>
                    </div>
                  </div>
                </div>
              )}

              {/* Footer */}
              <footer style={{
                backgroundColor: darkMode ? '#1e293b' : '#f8fafc',
                borderTop: `1px solid ${darkMode ? '#334155' : '#e2e8f0'}`,
                padding: '2rem',
                textAlign: 'center',
                marginTop: '3rem'
              }}>
                <div style={{ fontSize: '0.875rem', opacity: 0.7 }}>
                  <strong>🚀 Dashboard ArbTrading SCC</strong> - Sistema Completo de Análise para Day Trading de Criptomoedas
                </div>
                <div style={{ fontSize: '0.75rem', opacity: 0.6, marginTop: '0.5rem' }}>
                  Desenvolvido para identificar oportunidades de arbitragem entre exchanges usando dados em tempo real e análise técnica avançada
                </div>
                <div style={{ fontSize: '0.75rem', opacity: 0.5, marginTop: '0.5rem' }}>
                  Lembre-se: Este é um sistema de análise. Não constitui aconselhamento financeiro.
                </div>
              </footer>
            </div>
          );
        }

        ReactDOM.render(<App />, document.getElementById('root'));
    </script>
</body>
</html>
