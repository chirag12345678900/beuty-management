# beuty-management
import pandas as pd
import matplotlib.pyplot as plt

location = "C:\\Users\\91946\\Downloads\\ipdata(1).csv"
df = pd.read_csv(location)

def showgraph(df):
    while True:
        print('\n1. Costume v/s Stock sold Graph')
        print('2. Costume v/s Profit Graph')
        print('3. Go Back to the previous menu')
        c = int(input('\nEnter your choice: '))
        
        if c == 1:
            dress = df['Costume']
            dress_stock = df['Stock_sold']
            plt.bar(dress, dress_stock, color="r")
            plt.xlabel("Costume")
            plt.ylabel("No. of Pieces Sold")
            plt.title('Costume v/s Stock sold')
            plt.show()
        elif c == 2:
            dress = df['Costume']
            dress_stock = df['Profit']
            plt.bar(dress, dress_stock, color="g")
            plt.xlabel("Costume")
            plt.ylabel("Profit")
            plt.title('Costume v/s Profit')
            plt.show()
        elif c == 3:
            break

def data_analysis(df):
    while True:
        print("\nBoutique Data Analysis Menu")
        print("-" * 80)
        print("\n1. View record(s)")
        print("2. Add a new record")
        print("3. Modify a record")
        print("4. Delete a record")
        print("5. Graph Creation")
        print("6. Exit")
        
        ch = int(input("\nEnter Your Choice: "))
        
        if ch == 1:
            while True:
                print("\n1. View All Records")
                print("2. Back")
                ans = int(input("Enter your choice: "))
                if ans == 1:
                    print("\nALL RECORDS OF BOUTIQUE\n")
                    print(df)
                    input('Press enter to continue...')
                elif ans == 2:
                    break
                else:
                    print('Wrong value input for the choice')
        # To add a new record
        elif ch == 2:
            print(df)
            dress = input("\nEnter costume: ")
            dtype = input("\nEnter style: ")
            CostPrice = int(input("\nEnter Cost Price: "))
            MRP = int(input("\nEnter MRP: "))
            Stock = int(input("\nEnter no. of pieces in stock: "))
            StockSold = int(input("\nEnter no. of pieces sold: "))
            Profit = int(input("\nEnter profit earned: "))
            data = [dress, dtype, CostPrice, MRP, Stock, StockSold, Profit]
            df.loc[len(df.index)] = data
            print(df)
            df.to_csv(location, index=False)
            input('Press enter to continue...')
        # Rest of the code for modification, deletion, and exit goes here
        # ...
        elif ch == 5:
            showgraph(df)
        elif ch == 6:
            break
        else:
            print("Wrong input! Try again")

def modify_data(df, dress_code, column, new_data):
    columns = ['Costume', 'Style', 'CostPrice', 'MRP', 'Profit']
    df.loc[dress_code, columns[column]] = new_data
    df.to_csv(location, index=False)

def main_menu():
    print('\t \t WELCOME TO BOUTIQUE MANAGEMENT SYSTEM\n')
    print('_' * 80)
    # password of software
    password = 0000
    i = int(input('Enter your password: '))
    if i == 1234:
        data_analysis(df)
        main_menu()

# Call the main_menu function to start the program
main_menu()
