import java.util.*;

public class LostKingdomAdventure {

    static Scanner sc = new Scanner(System.in);
    static int health = 100;
    static int gold = 20;

    public static void main(String[] args) {

        System.out.println("=================================");
        System.out.println("   🏰 THE LOST KINGDOM ADVENTURE ");
        System.out.println("=================================\n");

        System.out.print("Enter your hero name: ");
        String hero = sc.nextLine();

        System.out.println("\nWelcome, " + hero + "!");
        System.out.println("Your journey begins in a dark forest...\n");

        forestPath(hero);

        if (health > 0) {
            System.out.println("\n🎉 Congratulations " + hero + "!");
            System.out.println("You survived the Lost Kingdom!");
            System.out.println("Final Health: " + health);
            System.out.println("Gold Collected: " + gold);
        } else {
            System.out.println("\n💀 Game Over...");
        }
    }

    static void forestPath(String hero) {
        System.out.println("You see two paths:");
        System.out.println("1. Enter the Cave");
        System.out.println("2. Walk toward the River");

        int choice = sc.nextInt();

        if (choice == 1)
            caveEncounter(hero);
        else
            riverEncounter(hero);
    }

    static void caveEncounter(String hero) {
        System.out.println("\nA wild Goblin appears!");

        Random rand = new Random();
        int damage = rand.nextInt(30) + 10;
        health -= damage;

        if (health > 0) {
            System.out.println("You defeated the Goblin!");
            System.out.println("Health lost: " + damage);
            gold += 50;
            treasureRoom(hero);
        } else {
            health = 0;
        }
    }

    static void riverEncounter(String hero) {
        System.out.println("\nYou found a healing fountain.");
        health += 30;
        System.out.println("Health increased by 30!");
        treasureRoom(hero);
    }

    static void treasureRoom(String hero) {
        System.out.println("\nYou discover a treasure chest!");
        System.out.println("1. Open it");
        System.out.println("2. Ignore it");

        int choice = sc.nextInt();

        if (choice == 1) {
            Random rand = new Random();
            int reward = rand.nextInt(100) + 20;
            gold += reward;
            System.out.println("You gained " + reward + " gold!");
        } else {
            System.out.println("You chose safety over greed.");
        }
    }
}
