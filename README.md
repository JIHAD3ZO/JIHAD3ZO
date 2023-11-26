import java.util.ArrayList;
import java.util.List;

class Product {
    private String name;
    private double price;
    private int quantity;

    public Product(String name, double price, int quantity) {
        this.name = name;
        this.price = price;
        this.quantity = quantity;
    }

    // Getters and setters for the name, price, and quantity fields

    public void updatePrice(double newPrice) {
        this.price = newPrice;
    }

    public void updateQuantity(int newQuantity) {
        this.quantity = newQuantity;
    }
}

class Inventory {
    private List<Product> products;

    public Inventory() {
        products = new ArrayList<>();
    }

    public void addProduct(Product product) {
        products.add(product);
    }

    public void sellProduct(String productName, int quantity) {
        for (Product product : products) {
            if (product.getName().equals(productName)) {
                if (product.getQuantity() >= quantity) {
                    product.updateQuantity(product.getQuantity() - quantity);
                    System.out.println(quantity + " units of '" + productName + "' sold.");
                } else {
                    System.out.println("Insufficient quantity of '" + productName + "' in stock.");
                }
                return;
            }
        }
        System.out.println("Product '" + productName + "' not found in inventory.");
    }

    public void updateProductPrice(String productName, double newPrice) {
        for (Product product : products) {
            if (product.getName().equals(productName)) {
                product.updatePrice(newPrice);
                System.out.println("Price of '" + productName + "' updated.");
                return;
            }
        }
        System.out.println("Product '" + productName + "' not found in inventory.");
    }

    public void updateProductQuantity(String productName, int newQuantity) {
        for (Product product : products) {
            if (product.getName().equals(productName)) {
                product.updateQuantity(newQuantity);
                System.out.println("Quantity of '" + productName + "' updated.");
                return;
            }
        }
        System.out.println("Product '" + productName + "' not found in inventory.");
    }
}

public class Main {
    public static void main(String[] args) {
        Inventory inventory = new Inventory();

        // Example: Adding products to inventory
        Product newspaper = new Product("Newspaper", 2.5, 100);
        Product magazine = new Product("Magazine", 5.0, 50);
        Product book = new Product("Book", 10.0, 20);

        inventory.addProduct(newspaper);
        inventory.addProduct(magazine);
        inventory.addProduct(book);

        // Example: Selling a product
        inventory.sellProduct("Magazine", 10);

        // Example: Updating product price
        inventory.updateProductPrice("Newspaper", 3.0);

        // Example: Updating product quantity
        inventory.updateProductQuantity("Book", 15);
    }
}
