# Moduel-3 
public abstract class Automobile implements Comparable<Automobile> {
    private int modelYear;
    private String brand;

    public Automobile(int modelYear, String brand) {
        this.modelYear = modelYear;
        this.brand = brand;
    }

    // Getter and Setter
    public int getModelYear() {
        return modelYear;
    }

    public void setModelYear(int modelYear) {
        this.modelYear = modelYear;
    }

    public String getBrand() {
        return brand;
    }

    public void setBrand(String brand) {
        this.brand = brand;
    }

    // Honk method
    public void honk() {
        System.out.println("Beep! Beep!");
    }

    // Implemented methods from Comparable interface
    @Override
    public int compareTo(Automobile other) {
        return Integer.compare(this.modelYear, other.modelYear);
    }

    // toString method to provide a string representation of the object
    @Override
    public String toString() {
        return "Automobile [Model Year: " + modelYear + ", Brand: " + brand + "]";
    }

    // equals method to compare two objects
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Automobile that = (Automobile) obj;
        return modelYear == that.modelYear && brand.equals(that.brand);
    }

    // Abstract methods for derived classes
    public abstract void accelerate();
    public abstract void stop();
    public abstract void reverse();
}  
public class Car extends Automobile {

    public Car(int modelYear, String brand) {
        super(modelYear, brand);
    }

    @Override
    public void accelerate() {
        System.out.println("The car is accelerating.");
    }

    @Override
    public void stop() {
        System.out.println("The car has stopped.");
    }

    @Override
    public void reverse() {
        System.out.println("The car is reversing.");
    }

    @Override
    public void honk() {
        System.out.println("Car honk: Beep! Beep!");
    }
}
 SportsCar.java (extends Car)

public class SportsCar extends Car {

    public SportsCar(int modelYear, String brand) {
        super(modelYear, brand);
    }

    @Override
    public void accelerate() {
        System.out.println("The sports car is accelerating at high speed!");
    }

    @Override
    public void honk() {
        System.out.println("Sports car honk: BEEP! BEEP!");
    }
} 
 JunkCar.java (extends Car)
java
Copy
public class JunkCar extends Car {

    public JunkCar(int modelYear, String brand) {
        super(modelYear, brand);
    }

    @Override
    public void accelerate() {
        System.out.println("The junk car struggles to accelerate.");
    }

    @Override
    public void stop() {
        System.out.println("The junk car stops with a loud screech!");
    }

    @Override
    public void reverse() {
        System.out.println("The junk car barely reverses.");
    }

    @Override
    public void honk() {
        System.out.println("Junk car honk: Honk... Honk...");
    }
}
 Tester.java (Main Testing Class)

public class Tester {

    public static void main(String[] args) {
        // Create an array of Automobiles
        Automobile[] automobiles = new Automobile[5];

        // Adding different automobiles to the array
        automobiles[0] = new Car(2022, "Toyota");
        automobiles[1] = new SportsCar(2021, "Ferrari");
        automobiles[2] = new JunkCar(1995, "Chevy");
        automobiles[3] = new SportsCar(2020, "Porsche");
        automobiles[4] = new Car(2010, "Honda");

        // Test the honk method for each automobile
        for (Automobile automobile : automobiles) {
            System.out.println("\nTesting: " + automobile);
            automobile.honk();
            automobile.accelerate();
            automobile.stop();
            automobile.reverse();
        }

        // Compare automobiles based on model year
        System.out.println("\nComparing Automobiles by Model Year:");
        System.out.println(automobiles[0] + " vs " + automobiles[1] + ": " + automobiles[0].compareTo(automobiles[1]));
        
        // Test the equals method
        System.out.println("\nChecking if first and second automobiles are equal:");
        System.out.println(automobiles[0].equals(automobiles[1]) ? "They are equal!" : "They are not equal.");
    }
}