# Hot-potato-game
import java.util.ArrayList;
import java.util.Random;
import java.util.Scanner;

public class HotPotatoGame {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        Random random = new Random();

        System.out.print("Enter number of players: ");
        int n = sc.nextInt();
        sc.nextLine();  // Clear buffer

        ArrayList<String> players = new ArrayList<>();

        // Adding players
        for (int i = 0; i < n; i++) {
            System.out.print("Enter Player " + (i + 1) + " Name: ");
            players.add(sc.nextLine());
        }

        System.out.println("\n--- HOT POTATO GAME STARTED ---");

        int currentIndex = 0;

        while (players.size() > 1) {

            // Random passing duration (3 to 10 passes)
            int passes = random.nextInt(8) + 3;

            System.out.println("\nPassing the potato... (" + passes + " passes)");

            // Simulate passing
            for (int i = 0; i < passes; i++) {
                currentIndex = (currentIndex + 1) % players.size();
            }

            // Player holding potato when "music stops"
            String eliminatedPlayer = players.get(currentIndex);
            System.out.println("Music Stopped! Player Holding Potato: " + eliminatedPlayer);
            System.out.println("Player Eliminated: " + eliminatedPlayer);

            // Remove player
            players.remove(currentIndex);

            // Adjust index
            currentIndex = currentIndex % players.size();
        }

        // Final Winner
        System.out.println("\n🏆 Winner of the Game: " + players.get(0));
        System.out.println("\n--- GAME OVER ---");
    }
}
