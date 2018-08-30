import pandas as pd

"""Financial Indices DataFrames"""
sp500 = pd.read_csv("/users/andreachello/Downloads/data/sp500.csv",
                    index_col = "Symbol",
                    usecols=[0, 2, 3, 7])


"""Stock Class"""
class Stock:

    def __init__(self, stock_index):
        self.stock_index = stock_index

    def all_stocks(self):
        return self.stock_index[:]
        
    def get_index(self):
        return self.stock_index.index

    def get_prices(self):
        return self.stock_index["Price"]

    def get_books(self):
        return self.stock_index["Book Value"]

    def get_sectors(self):
        return self.stock_index["Sector"]

    def get_price_compare_upperlower(self, upper, lower):
        return self.stock_index[(self.stock_index.Price < float(upper)) & (self.stock_index.Price > float(lower))][["Price"]]

    def get_singlevalue_stock(self, ticker, index):
        return print("\n{}'s {} is {}".format(ticker, index, self.stock_index.at[ticker, index]))

    def get_sector(self, sector):

        self.sector = str(sector)
        return self.stock_index.loc[0, self.sector]


"""Mainline Method"""
if __name__ == '__main__':

    print("\n            =========================================================")
    print("\n                   Welcome to Python's Financial Database: \n")
    print ("            =========================================================\n\n")

    while True:
        try:
            index_choice = input ("Which stock index do you want to use(SP500): ")
            if index_choice == "SP500":
                index = sp500
                stock = Stock(sp500)
                break

        except Exception as e:
            continue

    print("\n\nYou can choose to view any of the following stocks: \n")
    print ("------------------------------------------------------------------------------------ \n")
    print(stock.get_index())

    print ("------------------------------------------------------------------------------------ \n")

    done = False
    while not done:

        initial_choice = str(input("Do you want to look at single stocks or at all of them: Single, All, Exit: "))
        print ("************************************************************************************\n")

        if initial_choice == "All":

            choice = str(input("Choose: All Stocks, Prices, Book Values, Sectors, Constrained Prices, Specific Sector, Back: "))
            print("************************************************************************************\n")

            if choice == "Prices":
                print(stock.get_prices())
                print ("\n")

            elif choice == "All Stocks":
                print(stock.all_stocks())
                print ("\n")

            elif choice == "Book Values":
                print(stock.get_books())
                print ("\n")

            elif choice == "Sectors":
                print(stock.get_sectors())
                print ("\n")

            elif choice == "Constrained Prices":
                print("You can view all companies with prices within a lower and upper bound.\n")
                upper = float(input("Enter upper bound of price(e.g. 100.0): "))
                lower = float(input("Enter lower bound of price(e.g. 0.0): "))
                print(stock.get_price_compare_upperlower(upper, lower))
                print ("\n")

            elif choice == "Specific Sector":
                sector = str (input ("Enter Sector: "))
                print (stock.get_sector(sector))
                print ("\n")

            elif choice == "Back":
                continue

        if initial_choice == "Single":

            choice = str (input ("Choose: Stock Specific Value, Back: "))
            print ("**************************************************\n")

            if choice == "Stock Specific Value":
                ticker = str (input ("Enter Ticker: "))
                value = str (input ("What would you like to look up: Price, Book Value or Sector: "))
                print (stock.get_singlevalue_stock (ticker, value))
                print ("\n")

            elif choice == "Back":
                continue

        elif initial_choice == "Exit":
            print("Have a Good Day.")
            done = True

