import java.util.Scanner;

public class Calendar {


    public static void main (String[] args){

        Scanner scanner = new Scanner(System.in);

        while (true) {
            String []today= {"15","10","2021"};//Непонятно пока откуда будет браться текущая дата. Прописал шаблон.

            showMonth(today[0],today[1]);
            System.out.println();

            System.out.println("Select operation:");
            System.out.println("(add) Add event");
            System.out.println("(update) Update event");
            System.out.println("(delete) Delete event");
            System.out.println("(show) Show all events");
            System.out.println("(search) Show event");
            System.out.println("(exit) Exit");

            String operation = scanner.nextLine();

            switch (operation) {

                case "add": {

                }
                case "update": {

                }
                case "delete": {

                }
                case "show": {

                }
                case "search": {

                }
                case "exit": {

                }


            }
        }

    }




    public static void showMonth(String day, String month){
        String[][] January={{"    ","    ","    ","    ","  1 ","  2 ","  3 "},
                {"  4 ","  5 ","  6 ","  7 ","  8 ","  9 "," 10 "},
                {" 11 "," 12 "," 13 "," 14 "," 15 "," 16 "," 17 "},
                {" 18 "," 19 "," 20 "," 21 "," 22 "," 23 "," 24 "},
                {" 25 "," 26 "," 27 "," 28 "," 29 "," 30 "," 31 "}};
        String[][] February={{"  1 ","  2 ","  3 ","  4 ","  5 ","  6 ","  7 "},
                {"  8 ","  9 "," 10 "," 11 "," 12 "," 13 "," 14 "},
                {" 15 "," 16 "," 17 "," 18 "," 19 "," 20 "," 21 "},
                {" 22 "," 23 "," 24 "," 25 "," 26 "," 27 "," 28 "}};
        String[][] March={{"  1 ","  2 ","  3 ","  4 ","  5 ","  6 ","  7 "},
                {"  8 ","  9 "," 10 "," 11 "," 12 "," 13 "," 14 "},
                {" 15 "," 16 "," 17 "," 18 "," 19 "," 20 "," 21 "},
                {" 22 "," 23 "," 24 "," 25 "," 26 "," 27 "," 28 "},
                {" 29 "," 30 "," 31 "}};
        String[][] April={{"    ","    ","    ","  1 ","  2 ","  3 ","  4 "},
                {"  5 ","  6 ","  7 ","  8 ","  9 "," 10 "," 11 "},
                {" 12 "," 13 "," 14 "," 15 "," 16 "," 17 "," 18 "},
                {" 19 "," 20 "," 21 "," 22 "," 23 "," 24 "," 25 "},
                {" 26 "," 27 "," 28 "," 29 "," 30 "}};
        String[][] May={{"    ","    ","    ","    ","    ","  1 ","  2 "},
                {"  3 ","  4 ","  5 ","  6 ","  7 ","  8 ","  9 "},
                {" 10 "," 11 "," 12 "," 13 "," 14 "," 15 "," 16 "},
                {" 17 "," 18 "," 19 "," 20 "," 21 "," 22 "," 23 "},
                {" 24 "," 25 "," 26 "," 27 "," 28 "," 29 "," 30 "},
                {" 31 "}};
        String[][] June={{"    ","  1 ","  2 ","  3 ","  4 ","  5 ","  6 "},
                {"  7 ","  8 ","  9 "," 10 "," 11 "," 12 "," 13 "},
                {" 14 "," 15 "," 16 "," 17 "," 18 "," 19 "," 20 "},
                {" 21 "," 22 "," 23 "," 24 "," 25 "," 26 "," 27 "},
                {" 28 "," 29 "," 30 "}};
        String[][] July={{"    ","    ","    ","  1 ","  2 ","  3 ","  4 "},
                {"  5 ","  6 ","  7 ","  8 ","  9 "," 10 "," 11 "},
                {" 12 "," 13 "," 14 "," 15 "," 16 "," 17 "," 18 "},
                {" 19 "," 20 "," 21 "," 22 "," 23 "," 24 "," 25 "},
                {" 26 "," 27 "," 28 "," 29 "," 30 "," 31 "}};
        String[][] August={{"    ","    ","    ","    ","    ","    ","  1 "},
                {"  2 ","  3 ","  4 ","  5 ","  6 ","  7 ","  8 "},
                {"  9 "," 10 "," 11 "," 12 "," 13 "," 14 "," 15 "},
                {" 16 "," 17 "," 18 "," 19 "," 20 "," 21 "," 22 "},
                {" 23 "," 24 "," 25 "," 26 "," 27 "," 28 "," 29 "},
                {" 30 "," 31 "}};
        String[][] September={{"    ","    ","  1 ","  2 ","  3 ","  4 ","  5 "},
                {"  6 ","  7 ","  8 ","  9 "," 10 "," 11 "," 12 "},
                {" 13 "," 14 "," 15 "," 16 "," 17 "," 18 "," 19 "},
                {" 20 "," 21 "," 22 "," 23 "," 24 "," 25 "," 26 "},
                {" 27 "," 28 "," 29 "," 30 "}};
        String[][] October={{"    ","    ","    ","    ","  1 ","  2 ","  3 "},
                {"  4 ","  5 ","  6 ","  7 ","  8 ","  9 "," 10 "},
                {" 11 "," 12 "," 13 "," 14 "," 15 "," 16 "," 17 "},
                {" 18 "," 19 "," 20 "," 21 "," 22 "," 23 "," 24 "},
                {" 25 "," 26 "," 27 "," 28 "," 29 "," 30 "," 31 "}};
        String[][] November={{"  1 ","  2 ","  3 ","  4 ","  5 ","  6 ","  7 "},
                {"  8 ","  9 "," 10 "," 11 "," 12 "," 13 "," 14 "},
                {" 15 "," 16 "," 17 "," 18 "," 19 "," 20 "," 21 "},
                {" 22 "," 23 "," 24 "," 25 "," 26 "," 27 "," 28 "},
                {" 29 "," 30 "}};
        String[][] December={{"    ","    ","  1 ","  2 ","  3 ","  4 ","  5 "},
                {"  6 ","  7 ","  8 ","  9 "," 10 "," 11 "," 12 "},
                {" 13 "," 14 "," 15 "," 16 "," 17 "," 18 "," 19 "},
                {" 20 "," 21 "," 22 "," 23 "," 24 "," 25 "," 26 "},
                {" 27 "," 28 "," 29 "," 30 "," 31 "}};


        String [][]monthToday;
        switch (month) {

            case "1":
                monthToday=January;
                printMonth(monthToday, day);
                break;
            case "2":
                monthToday=February;
                printMonth(monthToday, day);
                break;
            case "3":
                monthToday=March;
                printMonth(monthToday, day);
                break;
            case "4":
                monthToday=April;
                printMonth(monthToday, day);
                break;
            case "5":
                monthToday=May;
                printMonth(monthToday, day);
                break;
            case "6":
                monthToday=June;
                printMonth(monthToday, day);
                break;
            case "7":
                monthToday=July;
                printMonth(monthToday, day);
                break;
            case "8":
                monthToday=August;
                printMonth(monthToday, day);
                break;
            case "9":
                monthToday=September;
                printMonth(monthToday, day);
                break;
            case "10":
                monthToday=October;
                printMonth(monthToday, day);
                break;
            case "11":
                monthToday=November;
                printMonth(monthToday, day);
                break;
            case "12":
                monthToday=December;
                printMonth(monthToday, day);
                break;
            default:
                System.out.println("Incorrect month");
            }


        }

        public static void printMonth(String [][] monthToday, String day){
            for (int i = 0; i < monthToday.length; i++) {
                for (int j = 0; j < monthToday[i].length; j++) {
                    if (monthToday[i][j].trim().equals(day)){
                        if(day.trim().length()==2){
                            System.out.print("["+day+"]");
                        }else{
                            System.out.print("[ "+day+"]");
                        }
                    }else {
                        System.out.print(monthToday[i][j]);
                    }
                }
                System.out.println();
            }
        }

}

