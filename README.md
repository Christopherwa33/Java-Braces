
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Brace {

    static String[] Bra(String[] values) {
        String[] ris = new String[values.length];
        for(int i=0; i<values.length; i++) {
            Stack<Character> stuff = new Stack<Character>();
            String testCase = values[i];
            for(int j=0; j<testCase.length(); j++) {
                char c = testCase.charAt(j);
                if(c=='{') {
                   stuff.push('{');
                } else if (c=='(') {
                    stuff.push('(');
                } else if (c=='[') {
                    stuff.push('[');
                } else if (c=='}') {
                    if(!stuff.isEmpty() && stuff.peek()=='{') {
                        stuff.pop();
                    } else {
                        ris[i] = "NO";
                    }
                } else if (c==')') {
                    if(!stuff.isEmpty() && stuff.peek()=='(') {
                        stuff.pop();
                    } else {
                        ris[i] = "NO";
                    }
                } else if (c==']') {
                    if(!stuff.isEmpty() && stuff.peek()=='[') {
                        stuff.pop();
                    } else {
                        ris[i] = "NO";
                    }
                }
            }
            ris[i] = stuff.isEmpty() ? "YES" : "NO";
        }

        return ris;
    }


    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        String value = in.nextLine();
        String[] valueArr = value.split(" ");
        String[] risArr = Bra(valueArr);
        for(int i=0; i<risArr.length; i++) {
            System.out.println(risArr[i]);
        }
    }
}
