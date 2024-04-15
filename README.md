def calculate_rsi(prices, period=14):
    delta = [prices[i + 1] - prices[i] for i in range(len(prices)-1)]
    gain = [delta[i] if delta[i] > 0 else 0 for i in range(len(delta))]
    loss = [abs(delta[i]) if delta[i] < 0 else 0 for i in range(len(delta))]
    
    avg_gain = sum(gain[:period]) / period
    avg_loss = sum(loss[:period]) / period
    
    rs = avg_gain / avg_loss if avg_loss != 0 else 0
    
    rsi = 100 - (100 / (1 + rs))
    
    return rsi

# Örnek fiyat verileri
prices = [45.15, 46.22, 45.78, 46.91, 47.16, 46.54, 45.89, 46.23, 45.78, 46.12, 47.08, 47.53, 46.91, 47.35]

# RSI hesapla
rsi = calculate_rsi(prices)
print("14 günlük RSI değeri:", rsi)
