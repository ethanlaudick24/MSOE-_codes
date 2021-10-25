# MSOE | Binary Addition (40 points)

import java.util.Scanner;
import java.lang.String;
import java.lang.Math;
class Main {
  public static void main(String[] args) {
    boolean inputCheck = true;
    boolean inputCheck2 = true;
    int strG;
    double count = 0;
    double str1F =0;
    double str2F =0;
    Scanner scan = new Scanner(System.in);
    System.out.println("Please enter your first binary number");
    String str1 = scan.nextLine();
    for(int x = str1.length(); x>0; x--){
      String sub = str1.substring(x-1,x);
      if(!(sub.equals("1") || sub.equals("0"))){
        System.out.println("Error, That is not a valid binary number.\nProgram has ended.");
        inputCheck = false;
      }
    }
    if(inputCheck){
      System.out.println("Please enter your second binary number");
      String str2 = scan.nextLine();
      for(int x = str2.length(); x>0; x--){
        String sub = str2.substring(x-1,x);
        if(!(sub.equals("1") || sub.equals("0"))){
          System.out.println("Error, That is not a valid binary number.\nProgram has ended.");
          inputCheck2 = false;
        }
      }
      if(inputCheck2){
        int str1L = str1.length();
        int str2L = str2.length();
        if(str1L > str2L)
          strG = str1L;
        else
          strG = str2L;
        String output = "";
        for(int x = strG; x>=0;x--)
          output += "0";
        for(int x = str1L; x > 0; x--,count++){
          String check = str1.substring(x-1,x);
          if(check.equals("1")){
            str1F += Math.pow(2,count);
          }
        }
        count = 0;
        for(int x = str2L; x > 0; x--,count++){
          String check = str2.substring(x-1,x);
          if(check.equals("1")){
            str2F += Math.pow(2,count);
          }
        }
        int strFinal = (int)(str1F + str2F);
        while(strFinal != 0){
          int y = (int)Math.pow(2,strFinal);
          int x;
          for(x = strFinal; y>strFinal; x--){
            y = (int)Math.pow(2,x);
          }
          x+=2;
          output = output.substring(0,output.length()-x) + "1" + output.substring(output.length()-x + 1);
          strFinal -= y;
        }
        while(output.substring(0,1).equals("0"))
        output = output.substring(1);
        System.out.println("The sum of those binary numbers is: " + output);
      }
    }
  }
}



