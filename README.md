# Codility-Fury-Road-Challenge
Calculate the minimum time that you need to get through the diversified road to your work.


# Task description
You have to be at your work as soon as possible. The road on your route to work may consist of two types of surface: asphalt or sand. To simplify the description, it will be denoted by a string R consisting only of the letters: "A" for an asphalt segment and "S" for a sand segment. All segments represent the same distance. For example, R = "SAAS" describes a road comprising of sand, asphalt, asphalt and sand segments.

When you go on foot, you need 20 minutes to pass through an asphalt segment and 30 minutes through a sand segment. You also have an electric scooter, which needs 5 minutes to pass through an asphalt segment and 40 minutes through a sand segment.

You start your journey on the scooter, but at any point you can get off the scooter and go on foot for the rest of the journey. What is the shortest time in which you can get to work?

# Link Details
[https://app.codility.com/cert/view/certBDJSE6-QFN3UG54ZSQDR26V/details/](https://app.codility.com/cert/view/certBDJSE6-QFN3UG54ZSQDR26V/details/)

# Programmming Language
Java SE 8

#Solution Code

```
import java.util.*;

class Solution {
    static int scooter(char[] charArray, int p) {
        for (int i = 0; i < charArray.length; i++) {
            if(charArray[i]=='A'){
                p=p+5;
            }
            else if(charArray[i]=='S'){
                p=p+40;
            }
        }
        return p;
    
    }
    static int footer(char[] charArray, int q) {
        for (int i = 0; i < charArray.length; i++) {
            if(charArray[i]=='A'){
                q=q+20;
            }
            else if(charArray[i]=='S'){
                q=q+30;
            }
        }
        return q;
    
    }

 public int solution(String R) {
       ArrayList<Character> charArr1;
       ArrayList<Character> charArr2;
        ArrayList<Integer> resu = new ArrayList<Integer>();
        int p=0,q=0;
        int pos= 0;
        
       
        char[] charArray = R.toCharArray();
        resu.add(scooter(charArray, p));
        resu.add(footer(charArray, q));

        if(pos==0 && pos < charArray.length){
            charArr1=new ArrayList<Character>();
            charArr2 = new ArrayList<Character>();
           for (int i = 0; i < pos+1; i++) {
                charArr1.add(charArray[i]) ;
            } 
            for (int i = pos + 1; i < charArray.length; i++)          {
                charArr2.add(charArray[i]) ;
                
            }
            pos=pos+1;
            char[] myCharArray1 = new char[charArr1.size()];
                for(int i = 0; i < charArr1.size(); i++) {
                    myCharArray1[i] = charArr1.get(i);
            }
            char[] myCharArray2 = new char[charArr2.size()];
                for(int i = 0; i < charArr2.size(); i++) {
                    myCharArray2[i] = charArr2.get(i);
            }
            int a1=scooter(myCharArray1, p)+footer(myCharArray2, q);
            resu.add(a1);
        }
            while(pos>0 && pos < charArray.length){
                charArr1=new ArrayList<Character>();
                charArr2 = new ArrayList<Character>();
                for (int i = 0; i < pos+1; i++) {
                    charArr1.add(charArray[i]) ;
                }
                for (int i = pos + 1; i < charArray.length; i++)          {
                    charArr2.add(charArray[i]) ;
                    
                }
                pos++;
                char[] myCharArray1 = new char[charArr1.size()];
                for(int i = 0; i < charArr1.size(); i++) {
                    myCharArray1[i] = charArr1.get(i);
                }
                char[] myCharArray2 = new char[charArr2.size()];
                    for(int i = 0; i < charArr2.size(); i++) {
                        myCharArray2[i] = charArr2.get(i);
                }
                int a1=scooter(myCharArray1, p)+footer(myCharArray2, q);
                resu.add(a1);
            }
        return Collections.min(resu);
    }
}

```
