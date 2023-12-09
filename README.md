// Vehicle class
class Vehicle {
    // Instance variables
    private String make;
    private int model;
    private int year;
    private int mileage;
    private String plateNumber;
    private int numSeats;

    // Constructors
    public Vehicle(String make, int model, int year, int mileage, String plateNumber, int numSeats) {
        this.make = make;
        this.model = model;
        this.year = year;
        this.mileage = mileage;
        this.plateNumber = plateNumber;
        this.numSeats = numSeats;
    }

    // Getters and setters for all instance variables
    public String getMake() {
        return make;
    }

    public int getModel() {
        return model;
    }

    // Other getters and setters for year, mileage, plateNumber, numSeats

    // toString method
    @Override
    public String toString() {
        return "Make: " + make + ", Model: " + model + ", Mileage: " + mileage;
    }
}

// Taxi class
class Taxi extends Vehicle {
    // Additional instance variables
    private double fareTotal;
    private int numFares;
    private String taxiID;

    // Constructor
    public Taxi(String make, int model, int year, int mileage, String plateNumber, int numSeats, String taxiID) {
        super(make, model, year, mileage, plateNumber, numSeats);
        this.taxiID = taxiID;
        this.fareTotal = 0.0;
        this.numFares = 0;
    }

    // Getters and setters for taxiID, fareTotal, numFares

    public String getTaxiID() {
        return taxiID;
    }

    public double getFareTotal() {
        return fareTotal;
    }

    public int getNumFares() {
        return numFares;
    }

    // Method to add fare
    public void addFare(double fare) {
        this.fareTotal += fare;
        this.numFares++;
    }

    // Method to calculate average fare
    public double getAverageFare() {
        if (numFares == 0) {
            return 0.0;
        }
        return fareTotal / numFares;
    }

    // Method to reset fare info
    public void resetFareInfo() {
        this.fareTotal = 0.0;
        this.numFares = 0;
    }

    // Overridden toString method
    @Override
    public String toString() {
        return super.toString() + ", Taxi ID: " + taxiID;
    }
}

// Main class
public class Main {
    public static void main(String[] args) {
        // Your student ID here
        String studentID = "YourStudentID";

        // Create a Taxi object with your student ID
        Taxi myTaxi = new Taxi("Toyota", 2023, 0, 0, "ABC123", 4, studentID);

        // Display all instance variable values of Taxi using the get methods
        System.out.println("Taxi Details:");
        System.out.println(myTaxi); // This will use the overridden toString method

        // Add two fares
        myTaxi.addFare(20.0);
        myTaxi.addFare(30.0);

        // Show average fare and number of fares
        System.out.println("Average Fare: " + myTaxi.getAverageFare());
        System.out.println("Number of Fares: "+ myTaxi.getNumFares());
    }
}
