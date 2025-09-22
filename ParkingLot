import java.util.*;

class Vehicle {
    String number;
    String type;   // Car or Bike
    long entryTime;
    long exitTime;

    Vehicle(String number, String type) {
        this.number = number;
        this.type = type;
        this.entryTime = System.currentTimeMillis();
    }

    void exit() {
        this.exitTime = System.currentTimeMillis();
    }

    int getCharge() {
        long duration = (exitTime - entryTime) / 1000; // seconds
        int rate = type.equalsIgnoreCase("Car") ? 20 : 10; // per unit
        return (int) (duration * rate);
    }
}

public class ParkingLot {
    static int totalSlots = 5;
    static List<Vehicle> parked = new ArrayList<>();

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        while (true) {
            System.out.println("\n1.Entry  2.Exit  3.Show Slots  4.Record  5.Exit Program");
            int choice = sc.nextInt();

            switch (choice) {
                case 1: // Vehicle entry
                    if (parked.size() < totalSlots) {
                        System.out.print("Enter Vehicle Number: ");
                        String num = sc.next();
                        System.out.print("Enter Type (Car/Bike): ");
                        String type = sc.next();
                        parked.add(new Vehicle(num, type));
                        System.out.println("Vehicle Parked.");
                    } else {
                        System.out.println("No Slots Available!");
                    }
                    break;

                case 2: // Vehicle exit
                    System.out.print("Enter Vehicle Number: ");
                    String num = sc.next();
                    Vehicle v = null;
                    for (Vehicle ve : parked) {
                        if (ve.number.equals(num)) {
                            v = ve;
                            break;
                        }
                    }
                    if (v != null) {
                        v.exit();
                        System.out.println("Parking Charge: Rs." + v.getCharge());
                        parked.remove(v);
                    } else {
                        System.out.println("Vehicle not found!");
                    }
                    break;

                case 3: // Show available slots
                    System.out.println("Available Slots: " + (totalSlots - parked.size()));
                    break;

                case 4: // Show record
                    System.out.println("Vehicles Currently Parked:");
                    for (Vehicle ve : parked) {
                        System.out.println(ve.number + " (" + ve.type + ")");
                    }
                    break;

                case 5:
                    System.out.println("Thank you! System closed.");
                    return;

                default:
                    System.out.println("Invalid Choice!");
            }
        }
    }
}
