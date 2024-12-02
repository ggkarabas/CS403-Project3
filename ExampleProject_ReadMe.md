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
```
# How to Use the Program

Since DumPy is a hypothetical language, we'll explain how you would use the program if it were implemented:

1. **Run the Program**: Execute the DumPy script in your DumPy interpreter.
2. **Navigate the Menu**: Use the numerical menu options to navigate through the system.
3. **View the Menu**: Select option `1` to see the available donuts and their prices.
4. **Place an Order**: Choose option `2`, view the menu, and input the number corresponding to the donut you wish to add to your cart.
5. **View Order Summary**: Option `3` displays the items in your cart and the total cost.
6. **Checkout**: Select option `4` to finalize your order and clear your cart.
7. **Exit**: Choose option `5` to exit the ordering system.

## Expected Output

Below is a sample interaction with the program:

```plaintext
Welcome to Gigi's Donuts!
1. View Menu
2. Place an Order
3. View Order Summary
4. Checkout
5. Exit
Enter your choice (1-5): 1

Gigi's Donuts Menu:
1. Glazed - $1.25
2. Chocolate - $1.5
3. Strawberry - $1.5
4. Boston Cream - $1.75
5. Apple Fritter - $2.0

1. View Menu
2. Place an Order
3. View Order Summary
4. Checkout
5. Exit
Enter your choice (1-5): 2

Gigi's Donuts Menu:
1. Glazed - $1.25
2. Chocolate - $1.5
3. Strawberry - $1.5
4. Boston Cream - $1.75
5. Apple Fritter - $2.0

Enter the number of the donut to add to your cart: 2
Added to cart: Chocolate

1. View Menu
2. Place an Order
3. View Order Summary
4. Checkout
5. Exit
Enter your choice (1-5): 2

Gigi's Donuts Menu:
1. Glazed - $1.25
2. Chocolate - $1.5
3. Strawberry - $1.5
4. Boston Cream - $1.75
5. Apple Fritter - $2.0

Enter the number of the donut to add to your cart: 5
Added to cart: Apple Fritter

1. View Menu
2. Place an Order
3. View Order Summary
4. Checkout
5. Exit
Enter your choice (1-5): 3

Your Order Summary:
- Chocolate: $1.5
- Apple Fritter: $2.0
Total Cost: $3.5

1. View Menu
2. Place an Order
3. View Order Summary
4. Checkout
5. Exit
Enter your choice (1-5): 4

Your Order Summary:
- Chocolate: $1.5
- Apple Fritter: $2.0
Total Cost: $3.5

Thank you for your purchase!

1. View Menu
2. Place an Order
3. View Order Summary
4. Checkout
5. Exit
Enter your choice (1-5): 5
Thank you for visiting Gigi's Donuts! Goodbye!

```

# Explanation of the Code

## Classes and Objects

- **Donut Class**: Represents a donut with flavor and price. Includes methods to initialize and display information.
- **Cart Class**: Manages the items the customer adds to their cart. Contains methods to add items, display the order summary, and clear the cart.
- **DonutShop Class**: Holds the menu of available donuts. Includes methods to display the menu and retrieve donuts based on user selection.

## Main Function

- **`main()`**: The entry point of the program. It initializes the `DonutShop` and `Cart` objects and runs a loop to interact with the user via a menu.

## Control Flow

- **Menu Loop**: A `while` loop keeps the program running until the user chooses to exit.
- **User Choices**: `if-elif-else` statements handle different menu options.
- **Input Validation**: Checks user input for validity and provides feedback.

## Type Annotations

- **Variables and Functions**: All variables and function parameters/return types are annotated for type safety.

## User Interaction

- **`echo` Function**: Outputs messages to the console.
- **`input` Function**: Receives user input.

## Demonstrated DumPy Features

- **Readability and Formatting**: Clean syntax with enforced spacing and indentation rules.
- **Type Safety**: Explicit type annotations prevent type-related errors.
- **Object-Oriented Programming**: Use of classes and objects to model the donut shop.
- **Control Structures**: Implementation of loops and conditional statements.
- **Collections**: Use of lists to manage the menu and cart items.
- **String Manipulation**: Concatenation and conversion of data types to strings.
- **Error Handling**: Logical checks to handle invalid inputs and actions.
- **Built-in Functions**: Utilization of `len()`, `enumerate()`, and type conversion functions.

## Possible Extensions

Enhance the ordering system by adding features such as:

- **Custom Donut Creation**: Allow users to create custom donuts with their choice of toppings.
- **Discounts and Promotions**: Implement special offers or loyalty rewards for customers.
- **Order History**: Keep track of previous orders within the session.
- **Multiple Payment Options**: Simulate different payment methods.
- **Inventory Management**: Track the quantity of each donut and update availability.

## Conclusion

The Gigi's Donuts Ordering System demonstrates how DumPy can be used to build interactive, console-based applications. By utilizing DumPy's features such as type safety, object-oriented programming, and enforced formatting rules, developers can create readable and maintainable code suitable for both learning and professional development.

This project showcases DumPy's emphasis on clarity and best practices, making it an ideal language for those who prioritize clean and reliable codebases.

## Note

**Disclaimer**: DumPy is a hypothetical programming language designed for illustrative purposes. The code provided in this project cannot be executed in a real-world environment but serves to demonstrate the language's syntax and features.

