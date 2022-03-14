# Battleship
package battleship;

import java.util.HashMap;
import java.util.Scanner;

public class Main {
    Scanner scanner = new Scanner(System.in);
    String[][] field;
    String[][] field2;
    String[][] shadowField;
    String[][] shadowField2;
    String[][] thirdField;
    String[][] thirdField2;
    HashMap<String, Integer> map = new HashMap<>();
    String x = "";

    String s = "";
    String c = "";
    String sstr = "";
    String cstr = "";
    int sint = 0;
    int cint = 0;
    int check;
    short mark = 17;
    short mark2 = 17;
    boolean first = true;

    public void Map() {
        HashMap<String, Integer> map = new HashMap<>();
        this.map = map;

        map.put("A", 1);
        map.put("B", 2);
        map.put("C", 3);
        map.put("D", 4);
        map.put("E", 5);
        map.put("F", 6);
        map.put("G", 7);
        map.put("H", 8);
        map.put("I", 9);
        map.put("J", 10);
    }

    public void Field() {//СТВОРИЛИ ПОЛЕ
        field = new String[12][12];

        field[0][0] = " ";
        field[1][0] = "A";
        field[2][0] = "B";
        field[3][0] = "C";
        field[4][0] = "D";
        field[5][0] = "E";
        field[6][0] = "F";
        field[7][0] = "G";
        field[8][0] = "H";
        field[9][0] = "I";
        field[10][0] = "J";
        field[11][0] = "";

        field[0][1] = "1";
        field[0][2] = "2";
        field[0][3] = "3";
        field[0][4] = "4";
        field[0][5] = "5";
        field[0][6] = "6";
        field[0][7] = "7";
        field[0][8] = "8";
        field[0][9] = "9";
        field[0][10] = "10";
        field[0][11] = "";
        System.out.println("Player 1, place your ships on the game field\n");
        for (int i = 1; i < field.length; i++) {
            for (int j = 1; j < field[i].length; j++) {
                field[i][j] = "~";
                field[i][11] = "";
                field[11][j] = "";
            }
        }
    }

    public void FieldSecond() {//СТВОРИЛИ ПОЛЕ
        field2 = new String[12][12];

        field2[0][0] = " ";
        field2[1][0] = "A";
        field2[2][0] = "B";
        field2[3][0] = "C";
        field2[4][0] = "D";
        field2[5][0] = "E";
        field2[6][0] = "F";
        field2[7][0] = "G";
        field2[8][0] = "H";
        field2[9][0] = "I";
        field2[10][0] = "J";
        field2[11][0] = "";

        field2[0][1] = "1";
        field2[0][2] = "2";
        field2[0][3] = "3";
        field2[0][4] = "4";
        field2[0][5] = "5";
        field2[0][6] = "6";
        field2[0][7] = "7";
        field2[0][8] = "8";
        field2[0][9] = "9";
        field2[0][10] = "10";
        field2[0][11] = "";
        System.out.println("Player 2, place your ships on the game field\n");
        for (int i = 1; i < field2.length; i++) {
            for (int j = 1; j < field2[i].length; j++) {
                field2[i][j] = "~";
                field2[i][11] = "";
                field2[11][j] = "";
            }
        }
    }

    public void ShadowField() {//Будемо звіряти координати на близькість кораблів
        shadowField = new String[11][11];

        shadowField[0][0] = " ";
        shadowField[1][0] = "A";
        shadowField[2][0] = "B";
        shadowField[3][0] = "C";
        shadowField[4][0] = "D";
        shadowField[5][0] = "E";
        shadowField[6][0] = "F";
        shadowField[7][0] = "G";
        shadowField[8][0] = "H";
        shadowField[9][0] = "I";
        shadowField[10][0] = "J";

        shadowField[0][1] = "1";
        shadowField[0][2] = "2";
        shadowField[0][3] = "3";
        shadowField[0][4] = "4";
        shadowField[0][5] = "5";
        shadowField[0][6] = "6";
        shadowField[0][7] = "7";
        shadowField[0][8] = "8";
        shadowField[0][9] = "9";
        shadowField[0][10] = "10";
        for (int i = 1; i < shadowField.length; i++) {
            for (int j = 1; j < shadowField[i].length; j++) {
                shadowField[i][j] = "~";
            }
        }
    }

    public void ShadowFieldSecond() {//Будемо звіряти координати на близькість кораблів
        shadowField2 = new String[11][11];

        shadowField2[0][0] = " ";
        shadowField2[1][0] = "A";
        shadowField2[2][0] = "B";
        shadowField2[3][0] = "C";
        shadowField2[4][0] = "D";
        shadowField2[5][0] = "E";
        shadowField2[6][0] = "F";
        shadowField2[7][0] = "G";
        shadowField2[8][0] = "H";
        shadowField2[9][0] = "I";
        shadowField2[10][0] = "J";

        shadowField2[0][1] = "1";
        shadowField2[0][2] = "2";
        shadowField2[0][3] = "3";
        shadowField2[0][4] = "4";
        shadowField2[0][5] = "5";
        shadowField2[0][6] = "6";
        shadowField2[0][7] = "7";
        shadowField2[0][8] = "8";
        shadowField2[0][9] = "9";
        shadowField2[0][10] = "10";
        for (int i = 1; i < shadowField2.length; i++) {
            for (int j = 1; j < shadowField2[i].length; j++) {
                shadowField2[i][j] = "~";
            }
        }
    }

    public void ThirdField() {//Fog of war
        thirdField = new String[11][11];

        thirdField[0][0] = " ";
        thirdField[1][0] = "A";
        thirdField[2][0] = "B";
        thirdField[3][0] = "C";
        thirdField[4][0] = "D";
        thirdField[5][0] = "E";
        thirdField[6][0] = "F";
        thirdField[7][0] = "G";
        thirdField[8][0] = "H";
        thirdField[9][0] = "I";
        thirdField[10][0] = "J";

        thirdField[0][1] = "1";
        thirdField[0][2] = "2";
        thirdField[0][3] = "3";
        thirdField[0][4] = "4";
        thirdField[0][5] = "5";
        thirdField[0][6] = "6";
        thirdField[0][7] = "7";
        thirdField[0][8] = "8";
        thirdField[0][9] = "9";
        thirdField[0][10] = "10";
        for (int i = 1; i < thirdField.length; i++) {
            for (int j = 1; j < thirdField[i].length; j++) {
                thirdField[i][j] = "~";
            }
        }
    }

    public void ThirdFieldSecond() {//Fog of war
        thirdField2 = new String[11][11];

        thirdField2[0][0] = " ";
        thirdField2[1][0] = "A";
        thirdField2[2][0] = "B";
        thirdField2[3][0] = "C";
        thirdField2[4][0] = "D";
        thirdField2[5][0] = "E";
        thirdField2[6][0] = "F";
        thirdField2[7][0] = "G";
        thirdField2[8][0] = "H";
        thirdField2[9][0] = "I";
        thirdField2[10][0] = "J";

        thirdField2[0][1] = "1";
        thirdField2[0][2] = "2";
        thirdField2[0][3] = "3";
        thirdField2[0][4] = "4";
        thirdField2[0][5] = "5";
        thirdField2[0][6] = "6";
        thirdField2[0][7] = "7";
        thirdField2[0][8] = "8";
        thirdField2[0][9] = "9";
        thirdField2[0][10] = "10";
        for (int i = 1; i < thirdField2.length; i++) {
            for (int j = 1; j < thirdField2[i].length; j++) {
                thirdField2[i][j] = "~";
            }
        }
    }

    public void FieldInConsole() {//ВИВОДИМ ПОЛЕ В КОНСОЛЬ
        for (int i = 0; i < field.length; i++) {
            for (int j = 0; j < field[i].length; j++) {
                if (j == field[i].length - 1) {
                    System.out.print(field[i][j]);
                } else {
                    System.out.print(field[i][j]);
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
    }

    public void FieldInConsoleSecond() {//ВИВОДИМ ПОЛЕ В КОНСОЛЬ
        for (int i = 0; i < field2.length; i++) {
            for (int j = 0; j < field2[i].length; j++) {
                if (j == field2[i].length - 1) {
                    System.out.print(field2[i][j]);
                } else {
                    System.out.print(field2[i][j]);
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
    }

    public void ThirdFieldInConsole() {//ВИВОДИМ FOG-ПОЛЕ В КОНСОЛЬ
        for (int i = 0; i < thirdField.length; i++) {
            for (int j = 0; j < thirdField[i].length; j++) {
                if (j == thirdField[i].length - 1) {
                    System.out.print(thirdField[i][j]);
                } else {
                    System.out.print(thirdField[i][j]);
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
    }

    public void ThirdFieldInConsole2() {//ВИВОДИМ FOG-ПОЛЕ В КОНСОЛЬ
        for (int i = 0; i < thirdField2.length; i++) {
            for (int j = 0; j < thirdField2[i].length; j++) {
                if (j == thirdField2[i].length - 1) {
                    System.out.print(thirdField2[i][j]);
                } else {
                    System.out.print(thirdField2[i][j]);
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
    }

    public void Check() {
        if (sstr.equals(cstr) && sint != cint) {
            check = Math.abs(sint - cint);
        } else if (sint == cint && !sstr.equals(cstr)) {
            check = Math.abs(map.get(sstr) - map.get(cstr));
        } else check = 0;
    }

    public boolean RockSar() {
        return sstr.equals(cstr) && sint == cint;
    }

    public void TwoLetters() {//Без десятки
        s = x.substring(0, 2);
        sstr = s.substring(0, 1);//letter
        sint = Integer.parseInt(s.substring(1, 2));//number
    }

    public void TwoLetters10() {//10
        if (x.contains("10")) {
            s = x.substring(0, 3);
            sstr = s.substring(0, 1);//letter
            sint = Integer.parseInt(s.substring(1, 3));//number
        } else {
            System.out.println("Error! You entered the wrong coordinates! Try again:");
            GameFirstPlayer();
        }
    }

    public void TwoLetters10Second() {//10
        if (x.contains("10")) {
            s = x.substring(0, 3);
            sstr = s.substring(0, 1);//letter
            sint = Integer.parseInt(s.substring(1, 3));//number
        } else {
            System.out.println("Error! You entered the wrong coordinates! Try again:");
            GameSecondPlayer();
        }
    }

    public void No10() {//Без десятки
        s = x.substring(0, 2);
        c = x.substring(3, 5);

        sstr = s.substring(0, 1);//letters
        cstr = c.substring(0, 1);//letters

        sint = Integer.parseInt(s.substring(1, 2));//numbers
        cint = Integer.parseInt(c.substring(1, 2));//numbers
    }

    public void First10() {//Десятка після першої букви
        s = x.substring(0, 3);
        c = x.substring(4, 6);

        sstr = s.substring(0, 1);//letters
        cstr = c.substring(0, 1);//letters

        sint = Integer.parseInt(c.substring(1, 2));//numbers
        cint = Integer.parseInt(s.substring(1, 3));//numbers
    }

    public void Second10() {//Десятка після другої букви
        s = x.substring(0, 2);
        c = x.substring(3, 6);

        sstr = s.substring(0, 1);//letters
        cstr = c.substring(0, 1);//letters

        sint = Integer.parseInt(s.substring(1, 2));//numbers
        cint = Integer.parseInt(c.substring(1, 3));//numbers
    }

    public void Twice10() {//Десятка після обох букв
        s = x.substring(0, 3);
        c = x.substring(4, 7);

        sstr = s.substring(0, 1);//letters
        cstr = c.substring(0, 1);//letters

        sint = Integer.parseInt(s.substring(1, 3));//numbers
        cint = Integer.parseInt(c.substring(1, 3));//numbers
    }

    public void TwiceLetters() {//ОДНАКОВІ БУКВИ
        for (int i = 1; i < field.length; i++) {
            if (i == map.get(sstr)) {
                for (int j = 1; j < field[i].length; j++) {
                    if (j >= sint && j <= cint) {
                        if (shadowField[i][j].equals("O")) {
                            System.out.println("Error! You placed it too close to another one. Try again:");
                            x = scanner.nextLine();
                            Check10();
                            Check();
                        } else field[i][j] = "O";
                    }
                }
            }
        }
        for (int i = 1; i < shadowField.length; i++) {
            if (i == map.get(sstr) + 1 || i == map.get(sstr) - 1 || i == map.get(sstr)) {
                for (int j = 1; j < shadowField[i].length; j++) {
                    if (j >= sint - 1 && j <= cint + 1) {
                        shadowField[i][j] = "O";
                    }
                }
            }
        }
    }

    public void TwiceNumbers() {//ОДНАКОВІ ЦИФРИ
        for (int i = 1; i < field.length; i++) {
            for (int j = 1; j < field[i].length; j++) {
                if (i >= map.get(sstr) && i <= map.get(cstr) && j == sint) {
                    if (shadowField[i][j].equals("O") && field[i][j].equals("~")) {
                        System.out.println("Error! You placed it too close to another one. Try again:");
                        x = scanner.nextLine();
                        Check10();
                        Check();
                    } else field[i][j] = "O";
                }
            }
        }
        for (int i = 1; i < shadowField.length; i++) {
            for (int j = 1; j < shadowField[i].length; j++) {
                if (i >= map.get(sstr) - 1 && i <= map.get(cstr) + 1 && j == sint
                        || i >= map.get(sstr) - 1 && i <= map.get(cstr) + 1 && j == sint - 1
                        || i >= map.get(sstr) - 1 && i <= map.get(cstr) + 1 && j == sint + 1) {
                    shadowField[i][j] = "O";
                }
            }
        }
    }

    public boolean TwiceLettersClose() {//ОДНАКОВІ БУКВИ Close
        for (int i = 1; i < field.length; i++) {
            if (i == map.get(sstr)) {
                for (int j = 1; j < field[i].length; j++) {
                    if (j >= sint && j <= cint) {
                        if (shadowField[i][j].equals("O") && field[i][j].equals("~")) {
                            return true;
                        }
                    }
                }
            }
        }
        return false;
    }

    public boolean TwiceNumbersClose() {//ОДНАКОВІ ЦИФРИ Close
        for (int i = 1; i < field.length; i++) {
            for (int j = 1; j < field[i].length; j++) {
                if (i >= map.get(sstr) && i <= map.get(cstr) && j == sint) {
                    if (shadowField[i][j].equals("O") && field[i][j].equals("~")) {
                        return true;
                    }
                }
            }
        }
        return false;
    }

    public void TwiceLetters2() {//ОДНАКОВІ БУКВИ
        for (int i = 1; i < field2.length; i++) {
            if (i == map.get(sstr)) {
                for (int j = 1; j < field2[i].length; j++) {
                    if (j >= sint && j <= cint) {
                        if (shadowField2[i][j].equals("O")) {
                            System.out.println("Error! You placed it too close to another one. Try again:");
                            x = scanner.nextLine();
                            Check10();
                            Check();
                        } else field2[i][j] = "O";
                    }
                }
            }
        }
        for (int i = 1; i < shadowField2.length; i++) {
            if (i == map.get(sstr) + 1 || i == map.get(sstr) - 1 || i == map.get(sstr)) {
                for (int j = 1; j < shadowField2[i].length; j++) {
                    if (j >= sint - 1 && j <= cint + 1) {
                        shadowField2[i][j] = "O";
                    }
                }
            }
        }
    }

    public void TwiceNumbers2() {//ОДНАКОВІ ЦИФРИ
        for (int i = 1; i < field2.length; i++) {
            for (int j = 1; j < field2[i].length; j++) {
                if (i >= map.get(sstr) && i <= map.get(cstr) && j == sint) {
                    if (shadowField2[i][j].equals("O") && field2[i][j].equals("~")) {
                        System.out.println("Error! You placed it too close to another one. Try again:");
                        x = scanner.nextLine();
                        Check10();
                        Check();
                    } else field2[i][j] = "O";
                }
            }
        }
        for (int i = 1; i < shadowField2.length; i++) {
            for (int j = 1; j < shadowField2[i].length; j++) {
                if (i >= map.get(sstr) - 1 && i <= map.get(cstr) + 1 && j == sint
                        || i >= map.get(sstr) - 1 && i <= map.get(cstr) + 1 && j == sint - 1
                        || i >= map.get(sstr) - 1 && i <= map.get(cstr) + 1 && j == sint + 1) {
                    shadowField2[i][j] = "O";
                }
            }
        }
    }

    public boolean TwiceLettersClose2() {//ОДНАКОВІ БУКВИ Close
        for (int i = 1; i < field2.length; i++) {
            if (i == map.get(sstr)) {
                for (int j = 1; j < field2[i].length; j++) {
                    if (j >= sint && j <= cint) {
                        if (shadowField2[i][j].equals("O") && field2[i][j].equals("~")) {
                            return true;
                        }
                    }
                }
            }
        }
        return false;
    }

    public boolean TwiceNumbersClose2() {//ОДНАКОВІ ЦИФРИ Close
        for (int i = 1; i < field2.length; i++) {
            for (int j = 1; j < field2[i].length; j++) {
                if (i >= map.get(sstr) && i <= map.get(cstr) && j == sint) {
                    if (shadowField2[i][j].equals("O") && field2[i][j].equals("~")) {
                        return true;
                    }
                }
            }
        }
        return false;
    }

    public void TwiceLettersRevers() {// РЕВЕРС ДЛЯ ОДНАКОВИХ БУКВ
        int empty;
        if (sstr.equals(cstr) && sint > cint) {
            empty = sint;
            sint = cint;
            cint = empty;
        }
    }

    public void TwiceNumbersRevers() {// РЕВЕРС ДЛЯ ОДНАКОВИХ ЦИФР
        String empty = "";
        if (sint == cint && map.get(sstr) > map.get(cstr)) {
            empty = sstr;
            sstr = cstr;
            cstr = empty;
        }
    }

    public void Check10() {
        if (x.length() == 5) {//Без числа 10
            No10();
        } else if (x.indexOf("10") == 1 && x.length() == 6) {//Десятка після першої букви
            First10();
        } else if (x.indexOf("10") == 4 && x.length() == 6) {//Десятка після другої букви
            Second10();
        } else if (x.length() == 7) {//Десятка після обох букв
            Twice10();
        } else if (x.length() == 2) {//Без числа 10, игра
            TwoLetters();
        } else if (x.length() == 3) {//З числом 10, игра
            TwoLetters10();
        }
    }

    public void FieldCum() {
        TwiceNumbersRevers();
        TwiceLettersRevers();
        if (sstr.equals(cstr)) {//ДЛЯ ОДНАКОВИХ БУКВ(КОРАБЕЛЬ В РЯД)
            TwiceLetters();
        } else if (sint == cint) {//ДЛЯ ОДНАКОВИХ ЧИСЕЛ (КОРАБЕЛЬ В СТОВПЧИК)
            TwiceNumbers();
        }
    }

    public void FieldCum2() {
        TwiceNumbersRevers();
        TwiceLettersRevers();
        if (sstr.equals(cstr)) {//ДЛЯ ОДНАКОВИХ БУКВ(КОРАБЕЛЬ В РЯД)
            TwiceLetters2();
        } else if (sint == cint) {//ДЛЯ ОДНАКОВИХ ЧИСЕЛ (КОРАБЕЛЬ В СТОВПЧИК)
            TwiceNumbers2();
        }
    }

    public void SwitchPlayer() { // Медот, що переключає гравців
        if (mark > 0 && mark2 > 0) {
            System.out.print("Press Enter and pass the move to another player");
            if (first) {
                try {
                    System.in.read();
                } catch (Exception e) {
                }
                GameSecondPlayer();
            } else {
                try {
                    System.in.read();
                } catch (Exception e) {
                }
                GameFirstPlayer();
            }
        } else if (mark == 0) {
            System.out.println("You sank the last ship. You won. Congratulations!");
            System.exit(0);
        } else {
            System.out.println("You sank the last ship. You won. Congratulations!");
            System.exit(0);
        }
    }

    public void GameFirstPlayer() {
        first = true;
        ThirdFieldInConsole2();
        System.out.println("---------------------");
        FieldInConsole();
        System.out.println("Player 1, it's your turn:");
        x = scanner.nextLine();
        Check();
        Check10();
        try {
            for (int i = 1; i < field2.length; i++) {
                for (int j = 1; j < field2[i].length; j++) {
                    if (i == map.get(sstr) && j == sint) {
                        if (field2[i][j].equals("O")) {
                            field2[i][j] = "X";
                            thirdField2[i][j] = "X";
                            if (field2[i][j - 1].equals(thirdField2[i][j]) && !field2[i][j + 1].equals("O")
                                    || !field2[i][j - 1].equals("O") && field2[i][j + 1].equals(thirdField2[i][j])
                                    || field2[i - 1][j].equals(thirdField2[i][j]) && !field2[i + 1][j].equals("O")
                                    || !field2[i - 1][j].equals("O") && field2[i + 1][j].equals(thirdField2[i][j])) {
                                if (mark == 1) {
                                } else System.out.println("You sank a ship!");
                            } else System.out.println("You hit a ship!");
                            mark--;
                            SwitchPlayer();
                        } else if (field2[i][j].equals("~")) {
                            field2[i][j] = "M";
                            thirdField2[i][j] = "M";
                            field2[i][j] = "M";
                            System.out.println("You missed!");
                            SwitchPlayer();
                        } else if (field2[i][j].equals("X")) {
                            field2[i][j] = "X";
                            thirdField2[i][j] = "X";
                            ThirdFieldInConsole2();
                            if (field2[i][j - 1].equals(thirdField2[i][j]) && !field2[i][j + 1].equals("O")
                                    || !field2[i][j - 1].equals("O") && field2[i][j + 1].equals(thirdField2[i][j])
                                    || field2[i - 1][j].equals(thirdField2[i][j]) && !field2[i + 1][j].equals("O")
                                    || !field2[i - 1][j].equals("O") && field2[i + 1][j].equals(thirdField2[i][j])) {
                                if (mark == 1) {
                                } else System.out.println("You sank a ship!");
                            } else System.out.println("You hit a ship!");
                        }
                    }
                }
            }
        } catch (Exception e) {
            System.out.println("Error! You entered the wrong coordinates! Try again:");
            GameFirstPlayer();
        }
    }

    public void GameSecondPlayer() {
        first = false;
        ThirdFieldInConsole();
        System.out.println("---------------------");
        FieldInConsoleSecond();
        System.out.println("Player 2, it's your turn:");
        x = scanner.nextLine();
        Check();
        Check10();
        if (mark2 > 0) {
            try {
                for (int i = 1; i < field.length; i++) {
                    for (int j = 1; j < field[i].length; j++) {
                        if (i == map.get(sstr) && j == sint) {
                            if (field[i][j].equals("O")) {
                                field[i][j] = "X";
                                thirdField[i][j] = "X";
                                if (field[i][j - 1].equals(thirdField[i][j]) && !field[i][j + 1].equals("O")
                                        || !field[i][j - 1].equals("O") && field[i][j + 1].equals(thirdField[i][j])
                                        || field[i - 1][j].equals(thirdField[i][j]) && !field[i + 1][j].equals("O")
                                        || !field[i - 1][j].equals("O") && field[i + 1][j].equals(thirdField[i][j])) {
                                    if (mark2 == 1) {
                                    } else System.out.println("You sank a ship!");
                                } else System.out.println("You hit a ship!");
                                mark2--;
                                SwitchPlayer();
                            } else if (field[i][j].equals("~")) {
                                field[i][j] = "M";
                                thirdField[i][j] = "M";
                                System.out.println("You missed!");
                                SwitchPlayer();
                            } else if (field[i][j].equals("X")) {
                                field[i][j] = "X";
                                thirdField[i][j] = "X";
                                ThirdFieldInConsole();
                                if (field[i][j - 1].equals(thirdField[i][j]) && !field[i][j + 1].equals("O")
                                        || !field[i][j - 1].equals("O") && field[i][j + 1].equals(thirdField[i][j])
                                        || field[i - 1][j].equals(thirdField[i][j]) && !field[i + 1][j].equals("O")
                                        || !field[i - 1][j].equals("O") && field[i + 1][j].equals(thirdField[i][j])) {
                                    if (mark2 == 1) {
                                    } else System.out.println("You sank a ship!");
                                } else System.out.println("You hit a ship!");
                            }
                        }
                    }
                }
            } catch (Exception e) {
                System.out.println("Error! You entered the wrong coordinates! Try again:");
                GameSecondPlayer();
            }
        } else if (mark2 == 0) {
            System.out.println("You sank the last ship. You won. Congratulations!");
            System.exit(0);
        }
    }

    public void EnterCords() {//СТАВИМО КОРАБЛІ
        ShadowField();
        short counter = 5;
        System.out.println("Enter the coordinates of the Aircraft Carrier (5 cells):");

        while (counter == 5) {
            x = scanner.nextLine();
            Check10();
            Check();
            if (check == 4) {
                FieldCum();
                FieldInConsole();//Виводимо наш оновлений масив
                counter--;
            } else if (check != 4 && sstr.equals(cstr) || check != 4 && sint == cint) {
                System.out.println("Error! Wrong length of the Aircraft Carrier! Try again:");
            } else if (!RockSar()) {
                System.out.println("Error! Wrong ship location! Try again:");
            }
        }

        System.out.println("Enter the coordinates of the Battleship (4 cells):");
        while (counter == 4) {
            x = scanner.nextLine();
            Check10();
            Check();
            if (check == 3) {
                if (!TwiceNumbersClose() && !TwiceLettersClose()) {
                    FieldCum();
                    FieldInConsole();//Виводимо наш оновлений масив
                    counter--;
                } else System.out.println("Error! You placed it too close to another one. Try again:");
            } else if (check != 3 && sstr.equals(cstr) || check != 3 && sint == cint) {
                System.out.println("Error! Wrong length of the Battleship! Try again:");

            } else if (!RockSar()) {
                System.out.println("Error! Wrong ship location! Try again:");

            }
        }
        System.out.println("Enter the coordinates of the Submarine (3 cells):");
        while (counter == 3) {
            x = scanner.nextLine();
            Check10();
            Check();
            if (check == 2 && counter == 3) {
                if (!TwiceNumbersClose() && !TwiceLettersClose()) {
                    FieldCum();
                    FieldInConsole();//Виводимо наш оновлений масив
                    counter--;
                } else System.out.println("Error! You placed it too close to another one. Try again:");
            } else if (check != 2 && sstr.equals(cstr) && counter == 3 || check != 2 && sint == cint && counter == 3) {
                System.out.println("Error! Wrong length of the Submarine! Try again:");

            } else if (!RockSar()) {
                System.out.println("Error! Wrong ship location! Try again:");

            }
        }

        System.out.println("Enter the coordinates of the Cruiser (3 cells):");
        while (counter == 2) {
            x = scanner.nextLine();
            Check10();
            Check();
            if (check == 2 && counter == 2) {
                if (!TwiceNumbersClose() && !TwiceLettersClose()) {
                    FieldCum();
                    FieldInConsole();//Виводимо наш оновлений масив
                    counter--;
                } else System.out.println("Error! You placed it too close to another one. Try again:");
            } else if (check != 2 && sstr.equals(cstr) && counter == 2 || check != 2 && sint == cint && counter == 2) {
                System.out.println("Error! Wrong length of the Cruiser! Try again:");

            } else if (!RockSar()) {
                System.out.println("Error! Wrong ship location! Try again:");

            }
        }

        System.out.println("Enter the coordinates of the Destroyer (2 cells):");
        while (counter == 1) {
            x = scanner.nextLine();
            Check10();
            Check();
            if (check == 1 && counter == 1) {
                if (!TwiceNumbersClose() && !TwiceLettersClose()) {
                    FieldCum();
                    FieldInConsole();//Виводимо наш оновлений масив
                    counter--;
                } else System.out.println("Error! You placed it too close to another one. Try again:");
            } else if (check != 1 && sstr.equals(cstr) || check != 1 && sint == cint) {
                System.out.println("Error! Wrong length of the Destroyer! Try again:");
            } else if (!RockSar()) {
                System.out.println("Error! Wrong ship location! Try again:");
            }
        }
        System.out.print("Press Enter and pass the move to another player");
        try {
            System.in.read();
        } catch (Exception e) {
        }
    }

    public void EnterCords2() {//СТАВИМО КОРАБЛІ
        ShadowFieldSecond();
        short count = 5;
        System.out.println("Enter the coordinates of the Aircraft Carrier (5 cells):");

        while (count == 5) {
            x = scanner.nextLine();
            Check10();
            Check();
            if (check == 4) {
                FieldCum2();
                FieldInConsoleSecond();//Виводимо наш оновлений масив
                count--;
            } else if (check != 4 && sstr.equals(cstr) || check != 4 && sint == cint) {
                System.out.println("Error! Wrong length of the Aircraft Carrier! Try again:");
            } else if (!RockSar()) {
                System.out.println("Error! Wrong ship location! Try again:");
            }
        }

        System.out.println("Enter the coordinates of the Battleship (4 cells):");
        while (count == 4) {
            x = scanner.nextLine();
            Check10();
            Check();
            if (check == 3) {
                if (!TwiceNumbersClose2() && !TwiceLettersClose2()) {
                    FieldCum2();
                    FieldInConsoleSecond();//Виводимо наш оновлений масив
                    count--;
                } else System.out.println("Error! You placed it too close to another one. Try again:");
            } else if (check != 3 && sstr.equals(cstr) || check != 3 && sint == cint) {
                System.out.println("Error! Wrong length of the Battleship! Try again:");

            } else if (!RockSar()) {
                System.out.println("Error! Wrong ship location! Try again:");

            }
        }
        System.out.println("Enter the coordinates of the Submarine (3 cells):");
        while (count == 3) {
            x = scanner.nextLine();
            Check10();
            Check();
            if (check == 2 && count == 3) {
                if (!TwiceNumbersClose2() && !TwiceLettersClose2()) {
                    FieldCum2();
                    FieldInConsoleSecond();//Виводимо наш оновлений масив
                    count--;
                } else System.out.println("Error! You placed it too close to another one. Try again:");
            } else if (check != 2 && sstr.equals(cstr) && count == 3 || check != 2 && sint == cint && count == 3) {
                System.out.println("Error! Wrong length of the Submarine! Try again:");

            } else if (!RockSar()) {
                System.out.println("Error! Wrong ship location! Try again:");

            }
        }

        System.out.println("Enter the coordinates of the Cruiser (3 cells):");
        while (count == 2) {
            x = scanner.nextLine();
            Check10();
            Check();
            if (check == 2 && count == 2) {
                if (!TwiceNumbersClose2() && !TwiceLettersClose2()) {
                    FieldCum2();
                    FieldInConsoleSecond();//Виводимо наш оновлений масив
                    count--;
                } else System.out.println("Error! You placed it too close to another one. Try again:");
            } else if (check != 2 && sstr.equals(cstr) && count == 2 || check != 2 && sint == cint && count == 2) {
                System.out.println("Error! Wrong length of the Cruiser! Try again:");

            } else if (!RockSar()) {
                System.out.println("Error! Wrong ship location! Try again:");

            }
        }

        System.out.println("Enter the coordinates of the Destroyer (2 cells):");
        while (count == 1) {
            x = scanner.nextLine();
            Check10();
            Check();
            if (check == 1 && count == 1) {
                if (!TwiceNumbersClose2() && !TwiceLettersClose2()) {
                    FieldCum2();
                    FieldInConsoleSecond();//Виводимо наш оновлений масив
                    count--;
                } else System.out.println("Error! You placed it too close to another one. Try again:");
            } else if (check != 1 && sstr.equals(cstr) || check != 1 && sint == cint) {
                System.out.println("Error! Wrong length of the Destroyer! Try again:");
            } else if (!RockSar()) {
                System.out.println("Error! Wrong ship location! Try again:");
            }
            System.out.print("Press Enter and pass the move to another player");
            try {
                System.in.read();
            } catch (Exception e) {
            }
        }
        GameFirstPlayer();
    }

    public static void main(String[] args) {//ВИКЛИКАЄМО МЕТОДИ НА ПЕРЕВІРКУ
        Main main = new Main();
        main.Field();
        main.Map();
        main.ThirdField();
        main.ThirdFieldSecond();
        main.FieldInConsole();
        main.EnterCords();
        main.FieldSecond();
        main.FieldInConsoleSecond();
        main.EnterCords2();
    }
}
