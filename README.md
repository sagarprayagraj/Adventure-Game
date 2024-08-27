import java.io.*;
import java.util.Random;
import java.util.Scanner;
public class Main 
{
    public static void main(String [] args)
    {
        // System objects
        Scanner s = new Scanner(System.in);
        Random rand = new Random();

        //Game variables
        String[] enemies = {"Nonu", "Baba", "Osama", "Bodu", "Buthasareya"};
        int maxEnemyHealth = 75;
        int enemyAttackDamage = 50;

        //player variables
        int health = 100;
        int attackDamage = 50;
        int numhealthPotions = 3;
        int healthPotionAmount = 30;
        int healthPotionDropChance = 50;//percentage

        boolean running = true;

        System.out.println("---------------Welcome to the Dungeon---------------!");

        Game:
        while(running)
        {
            System.out.println("----------------------------------------------------!");

            int enemyHealth = rand.nextInt(maxEnemyHealth);
            String enemy = enemies[rand.nextInt(5)];
            System.out.println("\t#" + enemy + " has appeared!#\n");

            while(enemyHealth > 0)
            {
                System.out.println("\tYour HP:" + health);
                System.out.println("\t" + enemy + "'s HP:" + enemyHealth);
                System.out.println("\n What would you like to do?");
                System.out.println("\t1. Attack");
                System.out.println("\t2. Drink health potion");
                System.out.println("\t3. Run");

                String input = s.nextLine();

                if(input.equals("1"))
                {
                   int damageDealt = rand.nextInt(attackDamage);
                   int damageTaken = rand.nextInt(enemyAttackDamage);
                   enemyHealth -= damageDealt;
                   health -= damageTaken;
                   System.out.println("\tYou strike the " + enemy + " for " + damageDealt + " damage.");
                   System.out.println("\tYou receive " + damageTaken + " in retaliation.");

                   if(health < 1)
                   {
                     System.out.println("\tyou have taken too much damage, you are too weak to go on");
                     break;
                   }
                }
                else if(input.equals("2"))
                {
                    if(numhealthPotions > 0)
                    {
                        health += healthPotionAmount;
                        numhealthPotions--;
                        System.out.println("\tyou took health potion and your health increases by " + healthPotionAmount + " You have now " + health + " HP and "  + numhealthPotions + " are left");
                    }
                    else
                    {
                        System.out.println("You have no health potions left, Defeat the enemy for a chance to get one.");
                    }
                }
                else if(input.equals("3"))
                {
                   System.out.println("You run away from the " + enemy + "!");
                   continue Game;
                }
                else
                {
                    System.out.println("Invalid Command");
                }
            }

                if(health < 1)
                {
                    System.out.println("You limp out of the dungeon, weak from battle");
                    break;
                }

                System.out.println("------------------------------------------------------");
                System.out.println(enemy + " was defeated");
                System.out.println("you have " + health + "HP left");

                if(rand.nextInt(100) < healthPotionDropChance)
                {
                    numhealthPotions++;
                    System.out.println("#The " + enemy + " dropped a health potion#");
                    System.out.println("#you have now " + numhealthPotions + " healthpotion(s) left#");
                }

                System.out.println("-----------------------------------------------------");
                System.out.println("What would you want to do now?");
                System.out.println("1. Continue playing");
                System.out.println("2.Exit");

                String in = s.nextLine();
                if(!in.equals("1") && !in.equals("2"))
                {
                    System.out.println("Invalid command");
                    in = s.nextLine();
                }
                else if(in.equals("1"))
                {
                    System.out.println("Continue on you adventure");
                }
                else
                {
                    System.out.println("You exit the dungeon, successful from your adventures");
                    break;
                }
            System.out.println("################################");
            System.out.println("#######THANKS FOR PLAYING#######");
            System.out.println("################################");
        }

    }
}# Adventure-Game
This is a text based game in which we have to give different commands to do operations.  Differant creatures will appear and we have to kill them to win the game. Health potions were added to make it more interesting.
