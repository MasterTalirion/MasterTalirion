- 👋 Hi, I’m @MasterTalirion
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
MasterTalirion/MasterTalirion is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
Helloooo


import java.util.Scanner;

public class Hello {
    public static void main (String [] args){
        String input = "Tomato";
        String inCase= "Tomao";

        check(input,inCase);


    }

    public static void check(String input,String inCase){

        int i=0;
        int j=0;

        int checkpoint=0;

        if(input.length()>inCase.length()) {

            while (j < inCase.length()) {
                if (input.charAt(i) == inCase.charAt(j)) {
                    i++;
                    j++;
                } else {
                    checkpoint++;
                    i++;
                }
                if (i == input.length()) {
                    break;
                }
            }
            int dif=input.length()-inCase.length();
            if (checkpoint+(dif-checkpoint) > 2) {
                System.out.println("Not found...");
            } else if (checkpoint > 0) {
                System.out.println("Maybe you search " + inCase + "?");
            } else {
                System.out.println("We finde contacts: " + inCase);
            }
        }else{
            while (j < input.length()) {
                if (inCase.charAt(i) == input.charAt(j)) {
                    i++;
                    j++;
                } else {
                    checkpoint++;
                    i++;
                }
                if (i == inCase.length()) {
                    break;
                }
            }

            if (checkpoint > 2) {
                System.out.println("Not found...");
            } else if (checkpoint > 0) {
                System.out.println("Maybe you search " + inCase + "?");
            } else {
                System.out.println("We finde contacts: " + inCase);
            }
        }

    }
}

