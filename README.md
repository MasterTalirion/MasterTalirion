import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;
import java.util.Date;
import java.util.Scanner;

public class Calendar {

    final static int EXTSIZE = 20;
    final static int TOTALCOLUMNS = 6;
    final static int INDEXCELL = 0;
    final static int DATECELL = 1;
    final static int NAMECELL = 2;
    final static int TYPECELL = 3;
    final static int GUESTCELL = 4;
    final static int PLACECELL = 5;


    public static void main(String[] args) throws ParseException {

        Date date = new Date();
        String dateStr = date.toString();

        Scanner scanner = new Scanner(System.in);

        String[][] events = new String[100][TOTALCOLUMNS];
        int lastEmptyCell = 0;

        while (true) {
            String[] today = dateStr.split(" ");

            showMonth(today[2], today[1]);
            System.out.println();

            int num = eventToday(events,lastEmptyCell);

            System.out.println("Tomorrow you have "+num+" events");

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

                    if (lastEmptyCell == events.length) {
                        String[][] tmp = new String[events.length + EXTSIZE][TOTALCOLUMNS];

                        for (int i = 0; i < events.length; i++) {
                            copyOneContactToAnother(events, i, tmp, i);
                        }
                        events = tmp;
                    }

                    events[lastEmptyCell][INDEXCELL] = Integer.toString(lastEmptyCell);
                    ;
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
                        if (events[lastEmptyCell][TYPECELL].equals("Regular") || events[lastEmptyCell][TYPECELL].equals("One-type")) {           //TODO
                            break;
                        } else {
                            System.out.println("Type value is not valid! Please enter again (Regular or One-type).");
                        }
                    }
                    while (true) {
                        System.out.println("Members: ");
                        events[lastEmptyCell][GUESTCELL] = scanner.nextLine();
                        if (events[lastEmptyCell][GUESTCELL].matches("[A-Za-z, ]+")) {          //TODO
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
                        } else {
                            System.out.println("Place value is not valid! Please enter again.");
                        }
                    }

                    lastEmptyCell++;
                    break;
                }
                case "update": {
                    if (lastEmptyCell == 0) {
                        System.out.println("Not find events!");
                        break;
                    }
                    System.out.println("Enter id:");

                    int eventIndex = scanner.nextInt();

                    if (eventIndex < lastEmptyCell) {

                        System.out.println("Current values:");
                        System.out.print("#" + eventIndex + ":");
                        System.out.print(events[eventIndex][DATECELL] + ", ");
                        System.out.print(events[eventIndex][NAMECELL] + ", ");
                        System.out.print(events[eventIndex][TYPECELL] + ", ");
                        System.out.print(events[eventIndex][GUESTCELL] + ",");
                        System.out.print(events[eventIndex][PLACECELL] + ", ");
                        System.out.println();


                        while (true) {
                            System.out.println("New date:");
                            events[eventIndex][DATECELL] = scanner.nextLine();
                            if (events[eventIndex][DATECELL].matches("[0-9]{2}[.][0-9]{2}[.][0-9]{4}")) {            //TODO
                                break;
                            } else {
                                System.out.println("Date value is not valid! Please enter again.");
                            }
                        }
                        while (true) {
                            System.out.println("New name:");
                            events[eventIndex][NAMECELL] = scanner.nextLine();
                            if (events[eventIndex][NAMECELL].matches("[A-Za-z0-9 ]+")) {   //TODO
                                break;
                            } else {
                                System.out.println("Name value is not valid! Please enter again.");
                            }
                        }
                        while (true) {
                            System.out.println("New type:");
                            events[eventIndex][TYPECELL] = scanner.nextLine();
                            if (events[eventIndex][TYPECELL].equals("Regular") || events[eventIndex][TYPECELL].equals("One-type")) {           //TODO
                                break;
                            } else {
                                System.out.println("Type value is not valid! Please enter again (Regular or One-type).");
                            }
                        }
                        while (true) {
                            System.out.println("New members:");
                            events[eventIndex][GUESTCELL] = scanner.nextLine();
                            if (events[eventIndex][GUESTCELL].matches("[A-Za-z, ]+")) {          //TODO
                                break;
                            } else {
                                System.out.println("Members value is not valid! Please enter again.");
                            }
                        }

                        while (true) {
                            System.out.println("New place:");
                            events[eventIndex][PLACECELL] = scanner.nextLine();
                            if (events[eventIndex][PLACECELL].matches("[A-Za-z0-9, ]+")) {          //TODO
                                break;
                            } else {
                                System.out.println("Place value is not valid! Please enter again.");
                            }
                        }
                    } else {
                        System.out.println("ID not found");
                    }

                    break;
                }
                case "delete": {
                    if (lastEmptyCell == 0) {
                        System.out.println("Not find events!");
                        break;
                    }

                    System.out.println("Delete by id# (id) or search keyword (word)?");

                    String deletionType = scanner.nextLine();
                    int id[]=null;

                    if ("id".equalsIgnoreCase(deletionType)) {

                        System.out.println("Entry id#:");

                        String strId = scanner.nextLine();
                        String[] idForDelete = strId.split(",");
                        id = new int[idForDelete.length];
                        for (int i = 0; i < id.length; i++) {
                            id[i] = Integer.parseInt(idForDelete[i]);
                            System.out.println("Deleting entry id#=" + id[i] + "...");
                        }
                    } else if ("word".equalsIgnoreCase(deletionType)) {

                        System.out.println("Please enter search keyword:");

                        String searchKeyword = scanner.nextLine();


                        String[][] foundEvents = searchEvents(events,lastEmptyCell,searchKeyword);

                        showEvents(foundEvents);

                        System.out.println("Please enter id#:");

                        String strId = scanner.nextLine();
                        String[] idForDelete = strId.split(",");
                        id = new int[idForDelete.length];

                        for (int i = 0; i < id.length; i++) {
                            id[i] = Integer.parseInt(idForDelete[i]);
                            System.out.println("Deleting entry id#=" + id[i] + "...");
                        }
                    }else{
                        System.out.println("Incorrect command");
                        break;
                    }

                    boolean isAnythingDeleted = false;

                    for (int j = 0; j < id.length; j++) {

                        if (id[j] < lastEmptyCell) {

                            for (int i = id[j]; i < lastEmptyCell && lastEmptyCell < events.length; i++) {
                                copyOneContactToAnother(events, i + 1, events, i);
                                events[i][INDEXCELL] = Integer.toString(i);
                                isAnythingDeleted = true;
                            }
                            for (int i = j + 1; i < id.length; i++) {
                                if (id[j] < id[i]) {
                                    id[i] = id[i] - 1;
                                }
                            }
                        } else {
                            System.out.println("Incorrect index!");
                            break;
                        }

                        if (lastEmptyCell > 0) {

                            events[lastEmptyCell - 1][INDEXCELL] = null;
                            events[lastEmptyCell - 1][DATECELL] = null;
                            events[lastEmptyCell - 1][NAMECELL] = null;
                            events[lastEmptyCell - 1][TYPECELL] = null;
                            events[lastEmptyCell - 1][GUESTCELL] = null;
                            events[lastEmptyCell - 1][PLACECELL] = null;

                            isAnythingDeleted = true;

                        }

                        if (isAnythingDeleted) {
                            lastEmptyCell--;
                        }
                        System.out.println("Deleted entry id#=" + id + ".");
                    }

                    if (lastEmptyCell == (events.length - 2 * EXTSIZE)) {

                        String[][] tmp = new String[lastEmptyCell + EXTSIZE][TOTALCOLUMNS];

                        for (int i = 0; i < lastEmptyCell; i++) {
                            copyOneContactToAnother(events, i, tmp, i);
                        }
                        events = tmp;
                    }
                    break;
                }
                case "show": {
                    if (lastEmptyCell == 0) {
                        System.out.println("Not find events!");
                        break;
                    }

                    System.out.println("Showing all events:");
                    String[][] sortedEvents = new String[lastEmptyCell][TOTALCOLUMNS];

                    for (int i = 0; i < lastEmptyCell; i++) {
                        copyOneContactToAnother(events, i, sortedEvents, i);
                    }


                    for (int i = 0; i < sortedEvents.length; i++) {
                        for (int j = 1; j < sortedEvents.length; j++) {
                            Date date1 = new SimpleDateFormat("dd.MM.yyyy").parse(sortedEvents[j - 1][DATECELL]);
                            Date date2 = new SimpleDateFormat("dd.MM.yyyy").parse(sortedEvents[j][DATECELL]);

                            if (date1.after(date2)) {
                                String[][] tmpContact = new String[1][TOTALCOLUMNS];

                                copyOneContactToAnother(sortedEvents, j - 1, tmpContact, 0);
                                copyOneContactToAnother(sortedEvents, j, sortedEvents, j - 1);
                                copyOneContactToAnother(tmpContact, 0, sortedEvents, j);
                            }
                        }
                    }
                    for (int i = 0; i < lastEmptyCell; i++) {
                        System.out.print("# " + sortedEvents[i][INDEXCELL] + " ");
                        System.out.print(sortedEvents[i][DATECELL] + ", ");
                        System.out.print(sortedEvents[i][NAMECELL] + ", ");
                        System.out.print(sortedEvents[i][TYPECELL] + ",");
                        System.out.print(sortedEvents[i][GUESTCELL] + ", ");
                        System.out.print(sortedEvents[i][PLACECELL]);
                        System.out.println();
                    }

                    break;
                }
                case "search": {
                    if (lastEmptyCell == 0) {
                        System.out.println("Not find events!");
                        break;
                    }

                    System.out.println("Enter search keyword:");

                    String searchKeyword = scanner.nextLine();


                    String[][] foundEvents = searchEvents(events, lastEmptyCell, searchKeyword);

                    showEvents(foundEvents);

                    break;
                }
                case "exit": {
                    System.out.println("Exiting Calendar...");
                    return;
                }


            }
        }

    }


    public static void showMonth(String day, String month) {
        String[][] January = {{"    ", "    ", "    ", "    ", "  1 ", "  2 ", "  3 "},
                {"  4 ", "  5 ", "  6 ", "  7 ", "  8 ", "  9 ", " 10 "},
                {" 11 ", " 12 ", " 13 ", " 14 ", " 15 ", " 16 ", " 17 "},
                {" 18 ", " 19 ", " 20 ", " 21 ", " 22 ", " 23 ", " 24 "},
                {" 25 ", " 26 ", " 27 ", " 28 ", " 29 ", " 30 ", " 31 "}};
        String[][] February = {{"  1 ", "  2 ", "  3 ", "  4 ", "  5 ", "  6 ", "  7 "},
                {"  8 ", "  9 ", " 10 ", " 11 ", " 12 ", " 13 ", " 14 "},
                {" 15 ", " 16 ", " 17 ", " 18 ", " 19 ", " 20 ", " 21 "},
                {" 22 ", " 23 ", " 24 ", " 25 ", " 26 ", " 27 ", " 28 "}};
        String[][] March = {{"  1 ", "  2 ", "  3 ", "  4 ", "  5 ", "  6 ", "  7 "},
                {"  8 ", "  9 ", " 10 ", " 11 ", " 12 ", " 13 ", " 14 "},
                {" 15 ", " 16 ", " 17 ", " 18 ", " 19 ", " 20 ", " 21 "},
                {" 22 ", " 23 ", " 24 ", " 25 ", " 26 ", " 27 ", " 28 "},
                {" 29 ", " 30 ", " 31 "}};
        String[][] April = {{"    ", "    ", "    ", "  1 ", "  2 ", "  3 ", "  4 "},
                {"  5 ", "  6 ", "  7 ", "  8 ", "  9 ", " 10 ", " 11 "},
                {" 12 ", " 13 ", " 14 ", " 15 ", " 16 ", " 17 ", " 18 "},
                {" 19 ", " 20 ", " 21 ", " 22 ", " 23 ", " 24 ", " 25 "},
                {" 26 ", " 27 ", " 28 ", " 29 ", " 30 "}};
        String[][] May = {{"    ", "    ", "    ", "    ", "    ", "  1 ", "  2 "},
                {"  3 ", "  4 ", "  5 ", "  6 ", "  7 ", "  8 ", "  9 "},
                {" 10 ", " 11 ", " 12 ", " 13 ", " 14 ", " 15 ", " 16 "},
                {" 17 ", " 18 ", " 19 ", " 20 ", " 21 ", " 22 ", " 23 "},
                {" 24 ", " 25 ", " 26 ", " 27 ", " 28 ", " 29 ", " 30 "},
                {" 31 "}};
        String[][] June = {{"    ", "  1 ", "  2 ", "  3 ", "  4 ", "  5 ", "  6 "},
                {"  7 ", "  8 ", "  9 ", " 10 ", " 11 ", " 12 ", " 13 "},
                {" 14 ", " 15 ", " 16 ", " 17 ", " 18 ", " 19 ", " 20 "},
                {" 21 ", " 22 ", " 23 ", " 24 ", " 25 ", " 26 ", " 27 "},
                {" 28 ", " 29 ", " 30 "}};
        String[][] July = {{"    ", "    ", "    ", "  1 ", "  2 ", "  3 ", "  4 "},
                {"  5 ", "  6 ", "  7 ", "  8 ", "  9 ", " 10 ", " 11 "},
                {" 12 ", " 13 ", " 14 ", " 15 ", " 16 ", " 17 ", " 18 "},
                {" 19 ", " 20 ", " 21 ", " 22 ", " 23 ", " 24 ", " 25 "},
                {" 26 ", " 27 ", " 28 ", " 29 ", " 30 ", " 31 "}};
        String[][] August = {{"    ", "    ", "    ", "    ", "    ", "    ", "  1 "},
                {"  2 ", "  3 ", "  4 ", "  5 ", "  6 ", "  7 ", "  8 "},
                {"  9 ", " 10 ", " 11 ", " 12 ", " 13 ", " 14 ", " 15 "},
                {" 16 ", " 17 ", " 18 ", " 19 ", " 20 ", " 21 ", " 22 "},
                {" 23 ", " 24 ", " 25 ", " 26 ", " 27 ", " 28 ", " 29 "},
                {" 30 ", " 31 "}};
        String[][] September = {{"    ", "    ", "  1 ", "  2 ", "  3 ", "  4 ", "  5 "},
                {"  6 ", "  7 ", "  8 ", "  9 ", " 10 ", " 11 ", " 12 "},
                {" 13 ", " 14 ", " 15 ", " 16 ", " 17 ", " 18 ", " 19 "},
                {" 20 ", " 21 ", " 22 ", " 23 ", " 24 ", " 25 ", " 26 "},
                {" 27 ", " 28 ", " 29 ", " 30 "}};
        String[][] October = {{"    ", "    ", "    ", "    ", "  1 ", "  2 ", "  3 "},
                {"  4 ", "  5 ", "  6 ", "  7 ", "  8 ", "  9 ", " 10 "},
                {" 11 ", " 12 ", " 13 ", " 14 ", " 15 ", " 16 ", " 17 "},
                {" 18 ", " 19 ", " 20 ", " 21 ", " 22 ", " 23 ", " 24 "},
                {" 25 ", " 26 ", " 27 ", " 28 ", " 29 ", " 30 ", " 31 "}};
        String[][] November = {{"  1 ", "  2 ", "  3 ", "  4 ", "  5 ", "  6 ", "  7 "},
                {"  8 ", "  9 ", " 10 ", " 11 ", " 12 ", " 13 ", " 14 "},
                {" 15 ", " 16 ", " 17 ", " 18 ", " 19 ", " 20 ", " 21 "},
                {" 22 ", " 23 ", " 24 ", " 25 ", " 26 ", " 27 ", " 28 "},
                {" 29 ", " 30 "}};
        String[][] December = {{"    ", "    ", "  1 ", "  2 ", "  3 ", "  4 ", "  5 "},
                {"  6 ", "  7 ", "  8 ", "  9 ", " 10 ", " 11 ", " 12 "},
                {" 13 ", " 14 ", " 15 ", " 16 ", " 17 ", " 18 ", " 19 "},
                {" 20 ", " 21 ", " 22 ", " 23 ", " 24 ", " 25 ", " 26 "},
                {" 27 ", " 28 ", " 29 ", " 30 ", " 31 "}};


        String[][] monthToday;
        switch (month) {
            case "Jan":
                System.out.println("           JANUARY");
                monthToday = January;
                printMonth(monthToday, day);
                break;
            case "Feb":
                System.out.println("           FEBRUARY");
                monthToday = February;
                printMonth(monthToday, day);
                break;
            case "Mar":
                System.out.println("            MARCH");
                monthToday = March;
                printMonth(monthToday, day);
                break;
            case "Apr":
                System.out.println("            APRIL");
                monthToday = April;
                printMonth(monthToday, day);
                break;
            case "May":
                System.out.println("             MAY");
                monthToday = May;
                printMonth(monthToday, day);
                break;
            case "Jun":
                System.out.println("            JUNE");
                monthToday = June;
                printMonth(monthToday, day);
                break;
            case "Jul":
                System.out.println("            JULY");
                monthToday = July;
                printMonth(monthToday, day);
                break;
            case "Aug":
                System.out.println("           AUGUST");
                monthToday = August;
                printMonth(monthToday, day);
                break;
            case "Sep":
                System.out.println("          SEPTEMBER");
                monthToday = September;
                printMonth(monthToday, day);
                break;
            case "Oct":
                System.out.println("           OCTOBER");
                monthToday = October;
                printMonth(monthToday, day);
                break;
            case "Nov":
                System.out.println("          NOVEMBER");
                monthToday = November;
                printMonth(monthToday, day);
                break;
            case "Dec":
                System.out.println("          DECEMBER");
                monthToday = December;
                printMonth(monthToday, day);
                break;
            default:
                System.out.println("Incorrect month");
        }


    }

    public static void printMonth(String[][] monthToday, String day) {
        for (int i = 0; i < monthToday.length; i++) {
            for (int j = 0; j < monthToday[i].length; j++) {
                if (monthToday[i][j].trim().equals(day) || ("0" + monthToday[i][j].trim()).equals(day)) {
                    if (day.trim().length() == 2 && day.trim().charAt(0) != '0') {
                        System.out.print("[" + day + "]");
                    } else {
                        System.out.print("[ " + monthToday[i][j].trim() + "]");
                    }
                } else {
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

    private static String[][] searchEvents(String[][] events, int lastEmptyCell, String searchKeyword) {
        String[][] foundEvent = new String[lastEmptyCell][events[0].length];

        int foundEventsCounter = 0;

        for (int i = 0; i < lastEmptyCell; i++) {

            for (int j = 0; j < events[i].length; j++) {

                if (contains(events[i][j], searchKeyword) || newContains(events[i][j], searchKeyword)) {
                System.out.println("found");

                    for (int k = 0; k < foundEvent[foundEventsCounter].length; k++) {
                        foundEvent[foundEventsCounter][k] = events[i][k];
                    }
                    foundEventsCounter++;
                    break;
                }
            }

        }
        if (foundEventsCounter > 0) {

            String[][] resultEvents = new String[foundEventsCounter][foundEvent[0].length];

            for (int i = 0; i < resultEvents.length; i++) {
                for (int j = 0; j < resultEvents[0].length; j++) {
                    resultEvents[i][j] = foundEvent[i][j];
                }
            }

            return resultEvents;

        } else {

            return null;

        }
    }

    private static boolean contains(String check, String input) {

        for(int i=0;i<check.length();i++){
            for(int j=0;j<input.length();j++){
                if(check.toLowerCase().charAt(i)!=input.toLowerCase().charAt(j)){
                    break;
                }
                for(int a=0;a<input.length();a++){
                    if(check.toLowerCase().charAt(i+a)!=input.toLowerCase().charAt(j+a)){
                        break;
                    }
                    if(a==input.length()-1){
                        System.out.println("found cont");
                        return true;
                    }else if(i+a+1>check.length()-1){
                        return false;
                    }
                }
            }
        }
        return false;
    }

    private static boolean newContains(String inCase, String input){
        int i=0;
        int j=0;
        int checkpoint=0;

        if(inCase.length()<input.length()){
            while(j<inCase.length()){
                if(input.charAt(i)==inCase.charAt(j)){
                    i++;
                    j++;
                }else{
                    checkpoint++;
                    i++;
                }
                if(i==input.length()){
                    break;
                }
            }

            if(input.length()-inCase.length()<3&&checkpoint<3) {
                System.out.println("found newCont 1");
                return true;
            }else{
                return false;
            }
        }else{
            while(j<input.length()){
                if(inCase.charAt(i)==input.charAt(j)){
                    i++;
                    j++;
                }else{
                    checkpoint++;
                    i++;
                }
                if(i==inCase.length()){
                    break;
                }
            }

            if(inCase.length()-input.length()<3&&checkpoint<3) {
                System.out.println("found newCont 2");
                return true;
            }else{
                return false;
            }
        }
    }

    private static void showEvents(String[][] events) {

        if ( events!= null && events.length > 0) {
            for (int i = 0; i < events.length; i++) {
                System.out.print("# " + events[i][INDEXCELL] + " ");
                System.out.print(events[i][DATECELL] + ", ");
                System.out.print(events[i][NAMECELL] + ", ");
                System.out.print(events[i][TYPECELL] + ",");
                System.out.print(events[i][GUESTCELL] + ", ");
                System.out.print(events[i][PLACECELL]);
                System.out.println();
            }
        }else{
            System.out.println("NOT FOUND!");
        }

    }

    private static int eventToday(String [][] events, int lastEmp){

        int counter=0;
        LocalDate ld2 = plusDate();

        for(int i=0;i<=lastEmp;i++){

            String str = events[i][DATECELL];
            String formattedDate2 = ld2.format(DateTimeFormatter.ofPattern("dd.MM.yyyy"));
            if(formattedDate2.equals(str)){
               counter++;
            }

        }
        return counter;
    }

    public static LocalDate plusDate(){
        return LocalDate.now().plusDays(1);
    }
}


