# Gigi's Donuts Ordering System

Welcome to **Gigi's Donuts Ordering System**, a console-based application built in **DumPy**. This program simulates a simple donut shop where customers can view the menu, place orders, view their cart, and checkout.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [DumPy Code](#dumpy-code)
- [How to Use the Program](#how-to-use-the-program)
- [Expected Output](#expected-output)
- [Explanation of the Code](#explanation-of-the-code)
  - [Classes and Objects](#classes-and-objects)
  - [Main Function](#main-function)
  - [Control Flow](#control-flow)
  - [Type Annotations](#type-annotations)
  - [User Interaction](#user-interaction)
- [Demonstrated DumPy Features](#demonstrated-dumpy-features)
- [Possible Extensions](#possible-extensions)
- [Conclusion](#conclusion)
- [Note](#note)

## Project Overview

The Gigi's Donuts Ordering System allows customers to:

- **View the Donut Menu**: See all available donut flavors and their prices.
- **Place an Order**: Add selected donuts to their cart.
- **View Order Summary**: Review items in the cart and the total cost.
- **Checkout**: Finalize the order and receive a thank-you message.
- **Exit**: Leave the ordering system.

This project demonstrates the capabilities of DumPy, focusing on readability, type safety, and best practices.

## Features

- **Class Definitions**: Uses `Donut`, `Cart`, and `DonutShop` classes to model real-world entities.
- **Type Annotations**: Enforces variable and function parameter types for type safety.
- **Control Flow**: Implements `if-elif-else` statements and loops for program logic.
- **User Interaction**: Engages users through console input and output.
- **Error Handling**: Validates user input and provides appropriate feedback.

## DumPy Code

```dumpy
# Gigi's Donuts Ordering System in DumPy

# Represents a donut item
class Donut:
    let flavor: String
    let price: Float

    # Constructor to initialize a donut
    func init(flavor: String, price: Float):
        self.flavor = flavor
        self.price = price

    # Method to display donut information
    func displayInfo():
        echo("Flavor: " + self.flavor + ", Price: $" + String(self.price))

# Represents the customer's cart
class Cart:
    var items: [Donut] = []

    # Method to add a donut to the cart
    func addItem(donut: Donut):
        self.items.append(donut)
        echo("Added to cart: " + donut.flavor)

    # Method to display the cart summary
    func displaySummary():
        if len(self.items) == 0:
            echo("Your cart is empty.")
            return
        echo("\nYour Order Summary:")
        var total: Float = 0.0
        for donut in self.items:
            echo("- " + donut.flavor + ": $" + String(donut.price))
            total += donut.price
        echo("Total Cost: $" + String(total) + "\n")

    # Method to clear the cart after checkout
    func clearCart():
        self.items = []

# Represents the donut shop
class DonutShop:
    let menu: [Donut] = [
        Donut("Glazed", 1.25),
        Donut("Chocolate", 1.50),
        Donut("Strawberry", 1.50),
        Donut("Boston Cream", 1.75),
        Donut("Apple Fritter", 2.00)
    ]

    # Method to display the donut menu
    func displayMenu():
        echo("\nGigi's Donuts Menu:")
        for index, donut in enumerate(self.menu):
            echo(String(index + 1) + ". " + donut.flavor + " - $" + String(donut.price))
        echo("")

    # Method to get a donut by index
    func getDonut(choice: Integer) -> Donut:
        return self.menu[choice - 1]

# Main program logic
func main():
    var shop = DonutShop()
    var cart = Cart()
    var running: Boolean = True

    echo("Welcome to Gigi's Donuts!")

    while running:
        echo("1. View Menu")
        echo("2. Place an Order")
        echo("3. View Order Summary")
        echo("4. Checkout")
        echo("5. Exit")
        let choice: String = input("Enter your choice (1-5): ")

        if choice == "1":
            shop.displayMenu()
        elif choice == "2":
            shop.displayMenu()
            let selection: String = input("Enter the number of the donut to add to your cart: ")
            var index = Integer(selection)
            if index >= 1 and index <= len(shop.menu):
                cart.addItem(shop.getDonut(index))
            else:
                echo("Invalid selection. Please try again.")
        elif choice == "3":
            cart.displaySummary()
        elif choice == "4":
            cart.displaySummary()
            if len(cart.items) > 0:
                echo("Thank you for your purchase!")
                cart.clearCart()
            else:
                echo("Your cart is empty. Add items before checkout.")
        elif choice == "5":
            echo("Thank you for visiting Gigi's Donuts! Goodbye!")
            running = False
        else:
            echo("Invalid choice. Please try again.")

# Start the program
main()
