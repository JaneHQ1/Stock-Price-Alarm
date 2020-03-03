import yfinance as yf
import requests
import sys


class stock:
    def __init__(self, stock_name):
        self.stock_name = stock_name

    def fetch_prices(self):
        stock = yf.Ticker(self.stock_name)  # get stock info
        self.bid = stock.info.get('bid')
        self.ask = stock.info.get('ask')

    def alarm(self):
        # build an event in app ifttt and replace the URL below by yours
        ifttt_event_url = 'https://maker.ifttt.com/trigger/stock_price_emergency/with/key/dMOw4cpb1EWriodbhvRULY'
        values = { "value1" : self.bid, "value2" : self.ask}
        requests.post(ifttt_event_url, json=values)

    def compare_prices(self, action, threshold):
        stock.fetch_prices(self)
        if action == "sell":
            print(self.ask)
            if self.ask > threshold:
                stock.alarm(self)
                sys.exit()

        if action == "buy":
            print(self.bid)
            if self.bid < threshold:
                stock.alarm(self)
                sys.exit()



if __name__ == '__main__':
    # Setting the price threshold
    stock_price_threshold = 100
    # Setting the stock name
    stock_name = "MSFT"
    # setting your action, sell or buy
    action = "buy"
    while True:
        love_Jane = stock(stock_name)
        love_Jane.compare_prices(action, stock_price_threshold)





