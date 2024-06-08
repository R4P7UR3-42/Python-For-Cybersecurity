# Inventory Tracker Program
```Python
# There's a lot more that could be added to this program, but this was moreso for practice

## create classes for the name, quantity, and description of each item
from InventoryPackage import Item_Name, Item_Quantity, Item_Description

# Initialize the master list
Master_List = []

# Function to add a list of an item and it's attributes to the master list
def Add_Inv_Item(lst, name, quant, desc):
    iname = Item_Name(name)
    iquant = Item_Quantity(quant)
    idesc = Item_Description(desc)
    item = [iname.name, iquant.quantity, idesc.description]
    lst.append(item)
    return

# Code to test the functionality
Add_Inv_Item(Master_List, 'Laptop', 434, 'HP Laptop')
Add_Inv_Item(Master_List, 'PC', 934, 'HP Desktop')
Add_Inv_Item(Master_List, 'Security Camera', 775, 'Indoor/outdoor cameras')

# Function to print the list in a readable format
def print_lst(d):
    for i, d in enumerate(d):
        print(f"\033[1mItem {i+1} \033[0m")
        print(f"Name: {d[0]}")
        print(f"Quantity: {d[1]}")
        print(f"Description: {d[2]}")
        print()

# Function to change the quantity of an item
def change_quantity (lst, item_to_change, new_quantity):
    for i, item in enumerate (lst):
        for d, items in enumerate (lst[i]):
            if items == item_to_change:
                desc = lst[i][2]
                lst[i] = [item_to_change, new_quantity, desc]
                break
    return lst

# Function to remove an item from the list and send a message
def remove_item(lst, item_name):
    for i, items in enumerate (lst):
        for e, item in enumerate (lst[i]):
            if item == item_name:
                print(f"{item_name} has been removed")
                del lst[i]
                return

# Code to test functionality
Master_List = change_quantity(Master_List, 'Laptop', 800)
remove_item(Master_List, 'PC')
print_lst(Master_List)
```