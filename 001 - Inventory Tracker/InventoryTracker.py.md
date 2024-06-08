# Inventory Tracker Program
```Python
## create classes for the name, quantity, and description of each item

from InventoryPackage import Item_Name, Item_Quantity, Item_Description

Master_List = []

def Add_Inv_Item(lst, name, quant, desc):
    iname = Item_Name(name)
    iquant = Item_Quantity(quant)
    idesc = Item_Description(desc)
    item = [iname.name, iquant.quantity, idesc.description]
    lst.append(item)
    return

Add_Inv_Item(Master_List, 'Laptop', 434, 'HP Laptop')
Add_Inv_Item(Master_List, 'PC', 934, 'HP Desktop')
Add_Inv_Item(Master_List, 'Security Camera', 775, 'Indoor/outdoor cameras')

def print_lst(d):
    for i, d in enumerate(d):
        print(f"\033[1mItem {i+1} \033[0m")
        print(f"Name: {d[0]}")
        print(f"Quantity: {d[1]}")
        print(f"Description: {d[2]}")
        print()

def change_quantity (lst, item_to_change, new_quantity):
    for i, item in enumerate (lst):
        for d, items in enumerate (lst[i]):
            if items == item_to_change:
                desc = lst[i][2]
                lst[i] = [item_to_change, new_quantity, desc]
                break
    return lst

def remove_item(lst, item_name):
    for i, items in enumerate (lst):
        for e, item in enumerate (lst[i]):
            if item == item_name:
                print(f"{item_name} has been removed")
                del lst[i]
                return

Master_List = change_quantity(Master_List, 'Laptop', 800)
remove_item(Master_List, 'PC')
print_lst(Master_List)
```