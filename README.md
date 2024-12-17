# Final
Финальная работа
Добрый день, представляю вашему вниманию проект на тему "Система онлайн-заказа еды"
class Menu:
    def __init__(self):
        self.items = {}

    def add_item(self, name, price):
        self.items[name] = price
        print(f"В меню добавлено блюдо: {name}")

    def get_price(self, name):
        return self.items.get(name)

    def display_menu(self):
        for name, price in self.items.items():
            print(f"{name}: {price} руб.")


class Order:
    def __init__(self):
        self.items = []
        self.total = 0
        self.status = "Создан"

    def add_item(self, name, price):
        self.items.append((name, price))
        self.total += price
        print(f"В заказ добавлено блюдо: {name}")

    def confirm_payment(self):
        self.status = "Оплачен"

    def update_status(self, status):
        self.status = status

    def display_order(self):
        print("Ваш заказ:")
        for name, price in self.items:
            print(f"{name}: {price} руб.")
        print(f"Итого: {self.total} руб.")
        print(f"Статус заказа: {self.status}")


class Delivery:
    def __init__(self, order):
        self.order = order
        self.status = "Доставка не начата"

    def start_delivery(self):
        self.status = "В пути"
        self.order.update_status("Доставляется")

    def complete_delivery(self):
        self.status = "Доставлено"
        self.order.update_status("Доставлено")

    def display_status(self):
        print(f"Статус доставки: {self.status}")


menu = Menu()
menu.add_item("Пицца", 500)
menu.add_item("Суши", 700)
menu.display_menu()

order = Order()
order.add_item("Пицца", menu.get_price("Пицца"))
order.display_order()
order.confirm_payment()
order.display_order()

delivery = Delivery(order)
delivery.display_status()
delivery.start_delivery()
delivery.display_status()
delivery.complete_delivery()
delivery.display_status()

<img src="https://raw.githubusercontent.com/D1nteSS/Final/513b73c0d6fcee61dc8ca8f765782a619ef5a26b/bpmn/diagram1.svg">
