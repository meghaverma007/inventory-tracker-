# inventory-tracker-

class Inventory:
    def __init__(self):
        self.items = {}

    def add_item(self, name, quantity, price):
        if name in self.items:
            self.items[name]['quantity'] += quantity
        else:
            self.items[name] = {'quantity': quantity, 'price': price}
        print(f"Added {quantity} of {name}.")

    def update(self, name, quantity=None, price=None):
        if name not in self.items:
            print(f"{name} not found.")
            return
        if quantity is not None:
            self.items[name]['quantity'] = quantity
        if price is not None:
            self.items[name]['price'] = price
        print(f"Updated {name}: Quantity={self.items[name]['quantity']}, Price=${self.items[name]['price']:.2f}")

    def remove(self, name):
        if name in self.items:
            del self.items[name]
            print(f"Removed {name}.")
        else:
            print(f"{name} not found.")

    def view(self):
        if not self.items:
            print("Inventory is empty.")
            return
        print("\nInventory List:")
        for name, details in self.items.items():
            print(f"{name}: {details['quantity']} @ ${details['price']:.2f}")

    def search(self, name):
        if name in self.items:
            print(f"{name}: {self.items[name]['quantity']} @ ${self.items[name]['price']:.2f}")
        else:
            print(f"{name} not found.")

# example
if __name__ == "__main__":
    inv = Inventory()
    inv.add_item("Laptop", 10, 799.99)
    inv.add_item("Smartphone", 20, 499.99)
    inv.view()
    inv.update("Laptop", 8, 759.99)
    inv.search("Smartphone")
    inv.remove("Smartphone")
    inv.view()
