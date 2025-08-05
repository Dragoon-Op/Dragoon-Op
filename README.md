import java.util.Random;
import java.util.Scanner;

public class RockPaperSissor {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter your choise: ");
        String player = scanner.nextLine().toLowerCase();
        String[] role = {"rock", "papper", "sissor"};
        Random random = new Random();
        String bot = role[random.nextInt(role.length)];
        System.out.println("Computer :" + bot);

        if (player.equals(bot)) {
            System.out.println("Its a Draw :");
        } else if (player.equals("rock") && bot.equals("papper") || (player.equals("sissor") && bot.equals("papper"))) {
            System.out.println("Players Wins");
        } else if (bot.equals("rock") && player.equals("papper") || (bot.equals("sissor") && player.equals("papper"))) {
            System.out.println("Computer wins");
        }
        else{
            System.out.println("No winner");
        }

    }
}

//        System.out.println("Enter your choise (Rock,Paper,Sissor: ");
//        role = scanner.next();
//        System.out.println(random.toString());
//        while (true){
//            System.out.println("Enter your choise :");
//            System.out.println(random);
//            if ()
//
//        }

