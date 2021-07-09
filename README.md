import java.util.Date;
import java.util.Scanner;

public class Calendar {

    final static int EXTSIZE = 20;
    final static int TOTALCOLUMNS = 6;
    final static int INDEXCELL =0;
    final static int DATECELL = 1;
    final static int NAMECELL = 2;
    final static int TYPECELL = 3;
    final static int GUESTCELL = 4;
    final static int PLACECELL = 5;


    public static void main (String[] args) {

        Date date = new Date();
        String dateStr = date.toString();

        Scanner scanner = new Scanner(System.in);

      String[][] events = new String[100][TOTALCOLUMNS];
      int lastEmptyCell = 0;

        while (true) {
            String []today = dateStr.split(" ");

            showMonth(today[2],today[1]);
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
                    events[lastEmptyCell][INDEXCELL] =  Integer.toString(lastEmptyCell);;
                    System.out.println(events[lastEmptyCell][INDEXCELL]);

                    while (true) {
                        System.out.println("Date: ");
                        events[lastEmptyCell][DATECELL] = scanner.nextLine();
                        if (events[lastEmptyCell][DATECELL].matches("[0-9]{2}[.][0-9]{2}[.][0-9]{4}")) {            //TODO
                            break;
                        } else {
                            System.out.println("Date value is not valid! Please enter again.");
                        }
                    }
                    while (true) {
                        System.out.println("Name: ");
                        events[lastEmptyCell][NAMECELL] = scanner.nextLine();
                        if (events[lastEmptyCell][NAMECELL].matches("[A-Za-z0-9 ]+")) {   //TODO
                            break;
                        } else {
                            System.out.println("Name value is not valid! Please enter again.");
                        }
                    }
                    while (true) {
                        System.out.println("Type: ");
                        events[lastEmptyCell][TYPECELL] = scanner.nextLine();
                        if (events[lastEmptyCell][TYPECELL].equals("Regular")||events[lastEmptyCell][TYPECELL].equals("One-type")) {           //TODO
                            break;
                        }else{
                            System.out.println("Type value is not valid! Please enter again (Regular or One-type).");
                        }
                    }
                    while (true) {
                        System.out.println("Members: ");
                        events[lastEmptyCell][GUESTCELL] = scanner.nextLine();
                        if (events[lastEmptyCell][GUESTCELL].matches("[A-Za-z,]+")) {          //TODO
                            break;
                        } else {
                            System.out.println("Members value is not valid! Please enter again.");
                        }
                    }
                    while (true) {
                        System.out.println("Place: ");
                        events[lastEmptyCell][PLACECELL] = scanner.nextLine();
                        if (events[lastEmptyCell][PLACECELL].matches("[A-Za-z0-9, ]+")) {          //TODO
                            break;
                        }else{
                            System.out.println("Place value is not valid! Please enter again.");
                        }
                    }

                    lastEmptyCell++;
                    break;
                }
                case "update": {

                }
                case "delete": {

                }
                case "show": {
                    System.out.println("Showing all contacts:");
                    String[][] sortedEvents = new String[lastEmptyCell][TOTALCOLUMNS];

                    for (int i = 0; i < lastEmptyCell; i++) {
                        copyOneContactToAnother(events, i, sortedEvents, i);
                        sortedEvents[i][TOTALCOLUMNS] = "" + i;
                    }
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
            case "Jan":
                System.out.println("           JANUARY");
                monthToday=January;
                printMonth(monthToday, day);
                break;
            case "Feb":
                System.out.println("           FEBRUARY");
                monthToday=February;
                printMonth(monthToday, day);
                break;
            case "Mar":
                System.out.println("            MARCH");
                monthToday=March;
                printMonth(monthToday, day);
                break;
            case "Apr":
                System.out.println("            APRIL");
                monthToday=April;
                printMonth(monthToday, day);
                break;
            case "May":
                System.out.println("             MAY");
                monthToday=May;
                printMonth(monthToday, day);
                break;
            case "Jun":
                System.out.println("            JUNE");
                monthToday=June;
                printMonth(monthToday, day);
                break;
            case "Jul":
                System.out.println("            JULY");
                monthToday=July;
                printMonth(monthToday, day);
                break;
            case "Aug":
                System.out.println("           AUGUST");
                monthToday=August;
                printMonth(monthToday, day);
                break;
            case "Sep":
                System.out.println("          SEPTEMBER");
                monthToday=September;
                printMonth(monthToday, day);
                break;
            case "Oct":
                System.out.println("           OCTOBER");
                monthToday=October;
                printMonth(monthToday, day);
                break;
            case "Nov":
                System.out.println("          NOVEMBER");
                monthToday=November;
                printMonth(monthToday, day);
                break;
            case "Dec":
                System.out.println("          DECEMBER");
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
                    if (monthToday[i][j].trim().equals(day)||("0"+monthToday[i][j].trim()).equals(day)){
                        if(day.trim().length()==2&&day.trim().charAt(0)!='0'){
                            System.out.print("["+day+"]");
                        }else{
                            System.out.print("[ "+monthToday[i][j].trim()+"]");
                        }
                    }else{
                        System.out.print(monthToday[i][j]);
                    }
                }
                System.out.println();
            }
        }

    private static void copyOneContactToAnother(String[][] fromEvent, int fromEventIndex, String[][] toEvent, int toEventIndex) {

        toEvent[toEventIndex][INDEXCELL] = fromEvent[fromEventIndex][INDEXCELL];
        toEvent[toEventIndex][DATECELL] = fromEvent[fromEventIndex][DATECELL];
        toEvent[toEventIndex][NAMECELL] = fromEvent[fromEventIndex][NAMECELL];
        toEvent[toEventIndex][TYPECELL] = fromEvent[fromEventIndex][TYPECELL];
        toEvent[toEventIndex][GUESTCELL] = fromEvent[fromEventIndex][GUESTCELL];
        toEvent[toEventIndex][PLACECELL] = fromEvent[fromEventIndex][PLACECELL];
    }

}

