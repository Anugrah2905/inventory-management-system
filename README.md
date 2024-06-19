"# inventory-management-system" 
import pandas as pd
class Inventory:
    def init(self):
        self.products = []
        self.quantities = []
    def add_product(self, product, quantity):
        self.products.append(product)
        self.quantities.append(quantity)
        inventory.save_changes()
    def update_quantity(self, product, quantity):
        index = self.products.index(product)
        self.quantities[index] = quantity
        inventory.save_changes()
    def save_changes(self):
        data = {'Product': self.products, 'Quantity': self.quantities}
        df = pd.DataFrame(data)
        df.to_csv('inventory_report.csv', index=False)
        print("Inventory updated\n")
    def display(self):
        df = pd.read_csv('inventory_report.csv')
        print(df)
inventory = Inventory()
while(True):
        print("1:Add product \n 2:update quantity \n 3:see inventory \n 4:exit menu \n")
        # op=int(input("enter your choice: "))
        match (int(input("enter your choice: "))):
            case 1:
                inventory.add_product(input("enter product name: "), input("enter product quantity: "))
            case 2:
                inventory.update_quantity(input("enter product name:"), input("enter product quantity:"))
            case 3:
                inventory.display()
            case 4:
                break
            case _:
                print("INVALID CHOICE")
