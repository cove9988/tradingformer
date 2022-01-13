# tradingformer
1) using transformer for time serial to create a model (forecasting next x bars) . 
2) applying knowledge distillation to get features extraction 
3) fine tuning pre-trained model with the trading pair 
4) creating trading model, applying sparse DRL model in gym environment by using pre-trained transformer  model as prophet


每一个bar是一个token[open_t，high_t，low_t，close_t, distant]，用一天，一个星期，一个月的bar （min，5m，30m，1h，daily）就像一个sentence，我们naming 它tentence。用于训练。
bar的特征：
  
  每个token [n] 的values
      distant[n]=open[n]- open[0]
      open_t[n] = open[0]-distant[n] = 0.0
      high_t[n] = high[n] - open[n] 
      low_t[n] = low[n] - open[n] 
      close_t[n] = close[n] - open[n] 
      
      
   
  
