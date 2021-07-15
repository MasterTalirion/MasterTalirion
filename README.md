import java.util.Scanner;

public class NewStep9 {

    //MODIFICATION - STEP 8 - START
    //MODIFICATION - STEP 6 - START

    final static int EXTSIZE = 20;
    final static int TOTALCOLUMNS = 7;

    final static int NAMECELL = 0;
    final static int SURNAMECELL = 1;
    final static int TELCELL = 2;
    final static int EMAILCELL = 3;
    final static int PATNAMECELL = 4;
    final static int MATNAMECELL = 5;
    final static int ADDRESSCELL = 6;

    //MODIFICATION - STEP 6 - END
    //MODIFICATION - STEP 8 - END

    public static void main(String[] args) {

        String[][] telContacts = new String[100][TOTALCOLUMNS]; //MODIFICATION IN: STEP 6
        int lastEmptyCell = 0;

        Scanner scanner = new Scanner(System.in);

        while (true) {

            System.out.println("Select operation:");
            System.out.println("(add) Add contact");
            System.out.println("(update) Update contact");
            System.out.println("(delete) Delete contact");
            System.out.println("(show) Show contacts");
            System.out.println("(search) Show contacts");
            System.out.println("(exit) Exit");

            String operation = scanner.nextLine();

            switch (operation) {

                case "add": {

                    //increase array size when array is exhausted
                    if (lastEmptyCell == telContacts.length) {

                        String[][] tmp = new String[telContacts.length
                                + EXTSIZE][TOTALCOLUMNS]; //MODIFICATION IN: STEP 6

                        for (int i = 0; i < telContacts.length; i++) {
                            //MODIFICATION - STEP 8 - START
                            copyOneContactToAnother(telContacts, i, tmp, i);
                            //MODIFICATION - STEP 8 - END
                        }

                        telContacts = tmp;
                    }

                    //MODIFICATION - STEP 4 - START
                    //Entered data validation logic goes here

                    while (true) {
                        System.out.println("Name:");
                        telContacts[lastEmptyCell][NAMECELL] = scanner.nextLine();
                        if (telContacts[lastEmptyCell][NAMECELL].matches("[A-Z][a-z]+")) {
                            break;
                        } else {
                            System.out.println(
                                    "Name value is not valid (should be only lower case letters starting with upper letter, smth like \"John\")! Please enter again.");
                        }
                    }

                    while (true) {
                        System.out.println("Surname:");
                        telContacts[lastEmptyCell][SURNAMECELL] = scanner.nextLine();
                        if (telContacts[lastEmptyCell][SURNAMECELL].matches("[A-Z][a-z]+")) {
                            break;
                        } else {
                            System.out.println(
                                    "Surname value is not valid (should be only lower case letters starting with upper letter, smth like \"Smith\")! Please enter again.");
                        }
                    }

                    while (true) {
                        System.out.println("Tel:");
                        telContacts[lastEmptyCell][TELCELL] = scanner.nextLine();
                        if (telContacts[lastEmptyCell][TELCELL].matches("\\+[1-9][0-9]+")) {
                            break;
                        } else {
                            System.out.println(
                                    "Tel value is not valid (should be smth like \"+1575759484\")! Please enter again.");
                        }
                    }

                    while (true) {
                        System.out.println("Email:");
                        telContacts[lastEmptyCell][EMAILCELL] = scanner.nextLine();
                        if (telContacts[lastEmptyCell][EMAILCELL]
                                .matches("[A-Za-z.-_0-9]+@[A-Za-z.-_0-9]+.[a-z]+")) {
                            break;
                        } else {
                            System.out.println(
                                    "Email value is not valid (should be smth like \"john@gmail.com\"! Please enter again.");
                        }
                    }

                    //MODIFICATION - STEP 4 - END

                    //MODIFICATION - STEP 6 - START
                    while (true) {
                        System.out.println("Paternal:");
                        telContacts[lastEmptyCell][PATNAMECELL] = scanner.nextLine();
                        if (telContacts[lastEmptyCell][PATNAMECELL].matches("[A-Z][a-z]+")) {
                            break;
                        } else {
                            System.out.println(
                                    "Surname value is not valid (should be only lower case letters starting with upper letter, smth like \"Smith\")! Please enter again.");
                        }
                    }

                    while (true) {
                        System.out.println("Maternal:");
                        telContacts[lastEmptyCell][MATNAMECELL] = scanner.nextLine();
                        if (telContacts[lastEmptyCell][MATNAMECELL].matches("[A-Z][a-z]+")) {
                            break;
                        } else {
                            System.out.println(
                                    "Surname value is not valid (should be only lower case letters starting with upper letter, smth like \"Smith\")! Please enter again.");
                        }
                    }

                    while (true) {
                        System.out.println("Address:");
                        telContacts[lastEmptyCell][ADDRESSCELL] = scanner.nextLine();
                        if (telContacts[lastEmptyCell][ADDRESSCELL].trim().length() > 0) {
                            break;
                        } else {
                            System.out.println(
                                    "Address should not be empty! Please enter again.");
                        }
                    }

                    lastEmptyCell++;

                    break;
                }
                case "search": {
                    if(lastEmptyCell==0){
                        System.out.println("Not find telContacts!");
                        break;
                    }

                    System.out.println("Enter search keyword:");

                    String searchKeyword = scanner.nextLine();


                    String[][] foundTelContacts = searchTelContacts(telContacts, lastEmptyCell,
                            searchKeyword);

                    showTelContacts(foundTelContacts);

                    break;
                }
                case "update": {
                    if(lastEmptyCell==0){
                        System.out.println("Not find telContacts!");
                        break;
                    }
                    System.out.println("Enter contact number:");

                    int contactIndex = scanner.nextInt();

                    if (contactIndex < lastEmptyCell) {

                        System.out.println("Current values:");
                        System.out.print("#" + contactIndex + ":");
                        System.out.print(telContacts[contactIndex][NAMECELL] + ", ");
                        System.out.print(telContacts[contactIndex][SURNAMECELL] + ", ");
                        System.out.print(telContacts[contactIndex][TELCELL] + ", ");
                        System.out.print(telContacts[contactIndex][EMAILCELL] + ",");
                        System.out.print(telContacts[contactIndex][PATNAMECELL] + ", ");
                        System.out.print(telContacts[contactIndex][MATNAMECELL] + ", ");
                        System.out.print(telContacts[contactIndex][ADDRESSCELL] + ".");
                        System.out.println();

                        System.out.println("New name:");
                        telContacts[contactIndex][NAMECELL] = scanner.nextLine();
                        System.out.println("New surname:");
                        telContacts[contactIndex][SURNAMECELL] = scanner.nextLine();
                        System.out.println("New tel:");
                        telContacts[contactIndex][TELCELL] = scanner.nextLine();
                        System.out.println("New email:");
                        telContacts[contactIndex][EMAILCELL] = scanner.nextLine();
                        System.out.println("New paternal name:");
                        telContacts[contactIndex][PATNAMECELL] = scanner.nextLine();
                        System.out.println("New maternal name:");
                        telContacts[contactIndex][MATNAMECELL] = scanner.nextLine();
                        System.out.println("New address:");
                        telContacts[contactIndex][ADDRESSCELL] = scanner.nextLine();

                    } else {
                        System.out.println("No such contact!");
                    }

                    break;
                }
                case "delete": {

                    if (lastEmptyCell == 0) {
                        System.out.println("Not find telContacts!");
                        break;
                    }


                    System.out.println("Entry id#:");

                    String strId = scanner.nextLine();
                    String[] idForDelete = strId.split(",");
                    int []id = new int[idForDelete.length];

                    for(int i=0;i<id.length;i++){
                        id[i] = Integer.parseInt(idForDelete[i]); //new tool for students to remember
                        System.out.println("Deleting entry id#=" + id[i] + "...");
                    }

                    boolean isAnythingDeleted = false;

                    for(int j=0;j<id.length;j++){

                        if (id[j] < lastEmptyCell) {

                            for (int i = id[j]; i < lastEmptyCell && lastEmptyCell < telContacts.length; i++) {
                                copyOneContactToAnother(telContacts, i+1, telContacts, i);
                                isAnythingDeleted = true;
                            }
                            for(int i=j+1;i<id.length;i++){
                                if(id[j]<id[i]){
                                    id[i]=id[i]-1;
                                }
                            }
                        }else{
                            System.out.println("Incorrect index!");
                            break;
                        }

                        if (lastEmptyCell > 0) {

                            telContacts[lastEmptyCell - 1][NAMECELL] = null; //new notion for students to remember: null
                            telContacts[lastEmptyCell - 1][SURNAMECELL] = null; //new notion for students to remember: null
                            telContacts[lastEmptyCell - 1][TELCELL] = null; //new notion for students to remember: null
                            telContacts[lastEmptyCell - 1][EMAILCELL] = null; //new notion for students to remember: null
                            telContacts[lastEmptyCell - 1][PATNAMECELL] = null;
                            telContacts[lastEmptyCell - 1][MATNAMECELL] = null;
                            telContacts[lastEmptyCell - 1][ADDRESSCELL] = null;

                            isAnythingDeleted = true;

                        }

                        if (isAnythingDeleted) {
                            lastEmptyCell--;
                        }
                        System.out.println("Deleted entry id#=" + id + ".");
                    }



                    //MODIFICATION - STEP 5 - END

                    //MODIFICATION - STEP 6 - START
                    //decrease array size if too many cells are empty
                    if (lastEmptyCell == (telContacts.length - 2 * EXTSIZE)) {

                        String[][] tmp = new String[lastEmptyCell
                                + EXTSIZE][TOTALCOLUMNS]; //MODIFICATION IN: STEP 6

                        for (int i = 0; i < lastEmptyCell; i++) {

                            //MODIFICATION - STEP 8 - START
                            copyOneContactToAnother(telContacts, i, tmp, i);
                            //MODIFICATION - STEP 8 - END
                        }

                        telContacts = tmp;
                    }

                    //MODIFICATION - STEP 6 - END

                    break;


                }
                case "show": {
                    if(lastEmptyCell==0){
                        System.out.println("Not find telContacts!");
                        break;
                    }
                    //MODIFICATION - STEP 2 - START
                    //sort before showing
                    System.out.println();
                    System.out.println("Sort by:");
                    System.out.println("(name) Sort by name");
                    System.out.println("(surname) Sort by surname");
                    System.out.println("(tel) Sort by tel");
                    System.out.println("(email) Sort by email");
                    System.out.println("(paternal) Sort by surname");
                    System.out.println("(maternal) Sort by tel");
                    System.out.println("(address) Sort by email");
                    System.out.println();
                    System.out.println("Sort by?:");
                    String field = scanner.nextLine();
                    System.out.println();
                    System.out.println("Ascending or descending?");
                    System.out.println("(asc) Ascending");
                    System.out.println("(desc) Descending");
                    System.out.println();
                    String order = scanner.nextLine();
                    System.out.println();

                    System.out.println("Showing all contacts:");
                    String[][] sortedTelContacts = new String[lastEmptyCell][TOTALCOLUMNS
                            + 1]; //MODIFICATION IN: STEP 6

                    for (int i = 0; i < lastEmptyCell; i++) {

                        //MODIFICATION - STEP 8 - START
                        copyOneContactToAnother(telContacts, i, sortedTelContacts, i);
                        sortedTelContacts[i][TOTALCOLUMNS] = "" + i;
                        //MODIFICATION - STEP 8 - END

                    }

                    int fieldIndex = 0;

                    switch (field) {
                        case "name": {
                            fieldIndex = NAMECELL;
                            break;
                        }
                        case "surname": {
                            fieldIndex = SURNAMECELL;
                            break;
                        }
                        case "tel": {
                            fieldIndex = TELCELL;
                            break;
                        }
                        case "email": {
                            fieldIndex = EMAILCELL;
                            break;
                        }
                        case "paternal": {
                            fieldIndex = PATNAMECELL;
                            break;
                        }
                        case "maternal": {
                            fieldIndex = MATNAMECELL;
                            break;
                        }
                        case "address": {
                            fieldIndex = ADDRESSCELL;
                            break;
                        }
                        default: //do nothing
                    }

                    if (order.equalsIgnoreCase("asc")) {
                        for (int i = 0; i < sortedTelContacts.length; i++) {
                            for (int j = 1; j < sortedTelContacts.length; j++) {
                                // Hint: need to explain str.compareToIgnoreCase() function
                                if (sortedTelContacts[j - 1][fieldIndex]
                                        .compareToIgnoreCase(sortedTelContacts[j][fieldIndex]) > 0) {
                                    //This can be of course achieved easier through references, but not to confuse with a new terms we do like this

                                    //MODIFICATION - STEP 8 - START

                                    String[][] tmpContact = new String[1][TOTALCOLUMNS+1];

                                    copyOneContactToAnother(sortedTelContacts, j-1, tmpContact, 0);
                                    copyOneContactToAnother(sortedTelContacts, j, sortedTelContacts, j-1);
                                    copyOneContactToAnother(tmpContact, 0, sortedTelContacts, j);

                                    //MODIFICATION - STEP 8 - END

                                }
                            }
                        }
                    } else if (order.equalsIgnoreCase("desc")) {
                        for (int i = 0; i < sortedTelContacts.length; i++) {
                            for (int j = 1; j < sortedTelContacts.length; j++) {
                                // Hint: need to explain str.compareToIgnoreCase() function
                                if (sortedTelContacts[j - 1][fieldIndex]
                                        .compareToIgnoreCase(sortedTelContacts[j][fieldIndex]) < 0) {
                                    //This can be of course achieved easier through references, but not to confuse with a new terms we do like this

                                    //MODIFICATION - STEP 8 - START

                                    String[][] tmpContact = new String[1][TOTALCOLUMNS+1];

                                    copyOneContactToAnother(sortedTelContacts, j-1, tmpContact, 0);
                                    copyOneContactToAnother(sortedTelContacts, j, sortedTelContacts, j-1);
                                    copyOneContactToAnother(tmpContact, 0, sortedTelContacts, j);

                                    //MODIFICATION - STEP 8 - END

                                }
                            }
                        }
                    }
                    //MODIFICATION - STEP 2 - END

                    for (int i = 0; i < lastEmptyCell; i++) {
                        System.out.print("#" + sortedTelContacts[i][TOTALCOLUMNS] + ":"); //MODIFICATION
                        System.out.print(sortedTelContacts[i][NAMECELL] + ", ");
                        System.out.print(sortedTelContacts[i][SURNAMECELL] + ", ");
                        System.out.print(sortedTelContacts[i][TELCELL] + ", ");
                        System.out.print(sortedTelContacts[i][EMAILCELL] + ",");
                        System.out.print(sortedTelContacts[i][PATNAMECELL] + ", ");
                        System.out.print(sortedTelContacts[i][MATNAMECELL] + ", ");
                        System.out.print(sortedTelContacts[i][ADDRESSCELL] + ".");
                        System.out.println();
                    }

                    break;
                }
                case "exit": {
                    System.out.println("Exiting TelBookApplication...");
                    return;
                }

            }

        }

    }


    private static void copyOneContactToAnother(String[][] fromContact, int fromContactIndex, String[][] toContact, int toContactIndex) {

        toContact[toContactIndex][NAMECELL] = fromContact[fromContactIndex][NAMECELL];
        toContact[toContactIndex][SURNAMECELL] = fromContact[fromContactIndex][SURNAMECELL];
        toContact[toContactIndex][TELCELL] = fromContact[fromContactIndex][TELCELL];
        toContact[toContactIndex][EMAILCELL] = fromContact[fromContactIndex][EMAILCELL];
        toContact[toContactIndex][PATNAMECELL] = fromContact[fromContactIndex][PATNAMECELL];
        toContact[toContactIndex][MATNAMECELL] = fromContact[fromContactIndex][MATNAMECELL];
        toContact[toContactIndex][ADDRESSCELL] = fromContact[fromContactIndex][ADDRESSCELL];

    }

    private static void showTelContacts(String[][] telContacts) {

        if (telContacts != null && telContacts.length > 0) {
            for (int i = 0; i < telContacts.length; i++) {
                for (int j = 0; j < telContacts[0].length; j++) {
                    System.out.print(telContacts[i][j]);
                    System.out.print((j == telContacts[0].length - 1) ? ".\n" : ", ");
                }
            }
        }else{
            System.out.println("NOT FOUND!");
        }

    }

    private static String[][] searchTelContacts(String[][] telContacts, int lastEmptyCell,
                                                String searchKeyword) {


        String[][] foundTelContacts = new String[lastEmptyCell][telContacts[0].length + 1];

        int foundTelContactsCounter = 0;

        for (int i = 0; i < lastEmptyCell; i++) {

            for (int j = 0; j < telContacts[i].length; j++) {

                //MODIFICATION - STEP 8 - START
                if (contains(telContacts[i][j], searchKeyword)||newContains(telContacts[i][j], searchKeyword)) {
                    //MODIFICATION - STEP 8 - END

                    foundTelContacts[foundTelContactsCounter][0] = "#" + i;

                    for (int k = 1; k < foundTelContacts[foundTelContactsCounter].length; k++) {
                        foundTelContacts[foundTelContactsCounter][k] = telContacts[i][k - 1];
                    }

                    foundTelContactsCounter++;

                    break;
                }
            }

        }

        if (foundTelContactsCounter > 0) {

            String[][] resultTelContacts = new String[foundTelContactsCounter][foundTelContacts[0].length];

            for (int i = 0; i < resultTelContacts.length; i++) {
                for (int j = 0; j < resultTelContacts[0].length; j++) {
                    resultTelContacts[i][j] = foundTelContacts[i][j];
                }
            }

            return resultTelContacts;

        } else {

            return null;

        }
    }

    //MODIFICATION - STEP 8 - START
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
                    System.out.println("Check 1");
                }
                if(i==input.length()){
                    break;
                }
            }

            if(input.length()-inCase.length()<3&&checkpoint<3) {
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
                    System.out.println("Check 1");
                }
                if(i==inCase.length()){
                    break;
                }
            }

            if(inCase.length()-input.length()<3&&checkpoint<3) {
                return true;
            }else{
                return false;
            }
        }
    }
}
