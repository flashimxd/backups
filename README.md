# backups
just back up some classes

package ie.binary.calculator;

import java.util.Scanner;

/*
 * @author Leonardo Lima
 * 
 */
public class Binary {
	
	private static boolean v1Set = false;
	private static boolean v2Set = false;
	private static String v1Type = ""; 
	private static String v2Type = ""; 
	private static int v1Int;
	private static String v1String;
	private static int v2Int;
	private static String v2String;
	
	
	private static String v2;
	
	public static void main(String[] args) {
		
		try(Scanner in = new Scanner(System.in)) {
			getHeader();
    		String input = in.next();
    		play(input, in);
            
        } catch(NumberFormatException e) {
            System.out.println("Looks like you entered a non Binary digit.");
        }

	}
	
	public static void getHeader() {
		System.out.println("=================================================================");
		System.out.println("==== Computer Programming & Maths for Computing and IT - CCT ====");
		System.out.println("==== Binary	Number Calculator - By Leonardo Lima ================");
		System.out.println("==== Please, enter if your option to use the calculator ====== \n");
		System.out.println("A)	Binary to decimal \n"
				+ "B)	Decimal to binary \n"
				+ "C)	Addition \n"
				+ "D)	Subtraction \n"
				+ "E)	Multiplication \n"
				+ "F)	Division \n"
				+ "G)	Quit \n");
		
		System.out.println("Enter with your option...");
	}
	
	public static void play(String input,Scanner in) {
		
		String choice = "";
		
		if(input.equals("S")) {
			getHeader();
			String st = in.next(); 
			choice = st.toUpperCase();
		}else {
			choice = input.toUpperCase();
		}
		
		switch(choice) {
			case "A":
				System.out.println("Type your binary number to be converted...");
				String binary = in.next();
				int rsBin = convertToDec(binary);
				System.out.println("Operation result: "+rsBin);
				System.out.println("Store value as variable? S/N");
				String st = in.next();
				String store = st.toUpperCase();
				
				if(store.equals("S")) {
					if(!v1Set) {
						v1Set = true;
						v1Type = "int";
						v1Int = rsBin;
					}else {
						v2Set = true;
						v2Type = "int";
						v2Int = rsBin;
					}
					//v1 = rsBin;
					System.out.println("Value stored");
				}
				
				play("S", in);
			break;
			
			case "B":
				System.out.println("Type your decimal number to be converted...");
				int decimal = in.nextInt();
				String rsDec = convertToBin(decimal);
				System.out.println("Operation result: "+rsDec);
				System.out.println("Store value as variable? S/N");
				String st2 = in.next();
				String store2 = st2.toUpperCase();
				
				if(store2.equals("S")) {
					//v2 = rsDec;
					if(!v1Set) {
						v1Set = true;
						v1Type = "str";
						v1String = rsDec;
					}else {
						v2Set = true;
						v2Type = "str";
						v2String = rsDec;
					}
					
					System.out.println("Value stored");
				}
				
				play("S", in);
			break;
			
			case "C":
				int c1 = 0;
				int c2 = 0;
				
				if(v1Set && v2Set) {
					
					if(v1Type.equals("str")) {
						c1 = convertToDec(v1String);
					}else {
						c1 = v1Int;
					}
					
					if(v2Type.equals("str")) {
						c2 = convertToDec(v2String);
					}else {
						c2 = v2Int;
					}
					
				}else if(!v1Set && !v2Set) {
					
					System.out.println("First value: binary or decimal? B/D");
					String st3 = in.next();
					String store3 = st3.toUpperCase();
					
					if(store3.equals("B")) {
						v1Type = "str";
						System.out.println(store3);
					}else if(store3.equals("D")){
						v1Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the first value");
					String input2 = in.next();
					if(v1Type.equals("str")) {
						c1 = convertToDec(input2);
					}else {
						c1 = Integer.parseInt(input2);
					}
					
					System.out.println("Second value: binary or decimal? B/D");
					String st4 = in.next();
					String store4 = st4.toUpperCase();
					if(store4.equals("B")) {
						v2Type = "str";
					}else if(store4.equals("D")){
						v2Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the second value");
					String input3 = in.next();
					if(v2Type.equals("str")) {
						c2 = convertToDec(input3);
					}else {
						c2 = Integer.parseInt(input3);
					}
				}else if(v1Set && !v2Set) {
					if(v1Type.equals("str")) {
						c1 = convertToDec(v1String);
					}else {
						c1 = v1Int;
					}
					
					System.out.println("Second value: binary or decimal? B/D");
					String st5 = in.next();
					String store5 = st5.toUpperCase();
					if(store5.equals("B")) {
						v2Type = "str";
					}else if(store5.equals("D")){
						v2Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the second value:");
					String input4 = in.next();
					if(v2Type.equals("str")) {
						c2 = convertToDec(input4);
					}else {
						c2 = Integer.parseInt(input4);
					}
				}
				
				add(c1, c2);
				play("S", in);
			break;
			
			case "D":
				int d1 = 0;
				int d2 = 0;
				
				if(v1Set && v2Set) {
					
					if(v1Type.equals("str")) {
						d1 = convertToDec(v1String);
					}else {
						d1 = v1Int;
					}
					
					if(v2Type.equals("str")) {
						d2 = convertToDec(v2String);
					}else {
						d2 = v2Int;
					}
					
				}else if(!v1Set && !v2Set) {
					
					System.out.println("First value: binary or decimal? B/D");
					String st3 = in.next();
					String store3 = st3.toUpperCase();
					
					if(store3.equals("B")) {
						v1Type = "str";
						System.out.println(store3);
					}else if(store3.equals("D")){
						v1Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the first value");
					String input2 = in.next();
					if(v1Type.equals("str")) {
						d1 = convertToDec(input2);
					}else {
						d1 = Integer.parseInt(input2);
					}
					
					System.out.println("Second value: binary or decimal? B/D");
					String st4 = in.next();
					String store4 = st4.toUpperCase();
					if(store4.equals("B")) {
						v2Type = "str";
					}else if(store4.equals("D")){
						v2Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the second value");
					String input3 = in.next();
					if(v2Type.equals("str")) {
						d2 = convertToDec(input3);
					}else {
						d2 = Integer.parseInt(input3);
					}
				}else if(v1Set && !v2Set) {
					if(v1Type.equals("str")) {
						d1 = convertToDec(v1String);
					}else {
						d1 = v1Int;
					}
					
					System.out.println("Second value: binary or decimal? B/D");
					String st5 = in.next();
					String store5 = st5.toUpperCase();
					if(store5.equals("B")) {
						v2Type = "str";
					}else if(store5.equals("D")){
						v2Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the second value:");
					String input4 = in.next();
					if(v2Type.equals("str")) {
						d2 = convertToDec(input4);
					}else {
						d2 = Integer.parseInt(input4);
					}
				}
				
				sub(d1, d2);
				play("S", in);
			break;
			
			case "E":
				int e1 = 0;
				int e2 = 0;
				
				if(v1Set && v2Set) {
					
					if(v1Type.equals("str")) {
						e1 = convertToDec(v1String);
					}else {
						e1 = v1Int;
					}
					
					if(v2Type.equals("str")) {
						e2 = convertToDec(v2String);
					}else {
						e2 = v2Int;
					}
					
				}else if(!v1Set && !v2Set) {
					
					System.out.println("First value: binary or decimal? B/D");
					String st3 = in.next();
					String store3 = st3.toUpperCase();
					
					if(store3.equals("B")) {
						v1Type = "str";
						System.out.println(store3);
					}else if(store3.equals("D")){
						v1Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the first value");
					String input2 = in.next();
					if(v1Type.equals("str")) {
						e1 = convertToDec(input2);
					}else {
						e1 = Integer.parseInt(input2);
					}
					
					System.out.println("Second value: binary or decimal? B/D");
					String st4 = in.next();
					String store4 = st4.toUpperCase();
					if(store4.equals("B")) {
						v2Type = "str";
					}else if(store4.equals("D")){
						v2Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the second value");
					String input3 = in.next();
					if(v2Type.equals("str")) {
						e2 = convertToDec(input3);
					}else {
						e2 = Integer.parseInt(input3);
					}
				}else if(v1Set && !v2Set) {
					if(v1Type.equals("str")) {
						e1 = convertToDec(v1String);
					}else {
						e1 = v1Int;
					}
					
					System.out.println("Second value: binary or decimal? B/D");
					String st5 = in.next();
					String store5 = st5.toUpperCase();
					if(store5.equals("B")) {
						v2Type = "str";
					}else if(store5.equals("D")){
						v2Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the second value:");
					String input4 = in.next();
					if(v2Type.equals("str")) {
						e2 = convertToDec(input4);
					}else {
						e2 = Integer.parseInt(input4);
					}
				}
				
				mult(e1, e2);
				play("S", in);
			break;
			
			case "F":
				int f1 = 0;
				int f2 = 0;
				
				if(v1Set && v2Set) {
					
					if(v1Type.equals("str")) {
						f1 = convertToDec(v1String);
					}else {
						f1 = v1Int;
					}
					
					if(v2Type.equals("str")) {
						f2 = convertToDec(v2String);
					}else {
						f2 = v2Int;
					}
					
				}else if(!v1Set && !v2Set) {
					
					System.out.println("First value: binary or decimal? B/D");
					String st3 = in.next();
					String store3 = st3.toUpperCase();
					
					if(store3.equals("B")) {
						v1Type = "str";
						System.out.println(store3);
					}else if(store3.equals("D")){
						v1Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the first value");
					String input2 = in.next();
					if(v1Type.equals("str")) {
						f1 = convertToDec(input2);
					}else {
						f1 = Integer.parseInt(input2);
					}
					
					System.out.println("Second value: binary or decimal? B/D");
					String st4 = in.next();
					String store4 = st4.toUpperCase();
					if(store4.equals("B")) {
						v2Type = "str";
					}else if(store4.equals("D")){
						v2Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the second value");
					String input3 = in.next();
					if(v2Type.equals("str")) {
						f2 = convertToDec(input3);
					}else {
						f2 = Integer.parseInt(input3);
					}
				}else if(v1Set && !v2Set) {
					if(v1Type.equals("str")) {
						f1 = convertToDec(v1String);
					}else {
						f1 = v1Int;
					}
					
					System.out.println("Second value: binary or decimal? B/D");
					String st5 = in.next();
					String store5 = st5.toUpperCase();
					if(store5.equals("B")) {
						v2Type = "str";
					}else if(store5.equals("D")){
						v2Type = "int";
					}else {
						System.out.println("Wrong type");
						play("S", in);
					}
					
					System.out.println("Type the second value:");
					String input4 = in.next();
					if(v2Type.equals("str")) {
						f2 = convertToDec(input4);
					}else {
						f2 = Integer.parseInt(input4);
					}
				}
				
				div(f1, f2);
				play("S", in);
			break;
			
			case "G":
				System.out.println("Bye, see you later!");
				System.exit(0);
			break;
			
			default:
				System.out.println("Invalid choice");
				play("S", in);
			break;
		}
	}
	
	public static String convertToBin(int interger) {
		
		int rem;
        int num =interger; 
        String str="";
        
        while(num>0)
        {
            rem = num%2;
            str = rem + str;
            num=num/2;
        }
        
        String result = String.valueOf(str);
        return result;
	}
	
	public static int convertToDec(String str) {
		
		double j=0;
		
	    for(int i=0;i<str.length();i++){
	        if(str.charAt(i)== '1'){
	         j=j+ Math.pow(2,str.length()-1-i);
	     }
	        
	    }
	    
	    return (int) j;
	}
	
	public static void add(int v1, int v2) {
		int result = v1+v2;
		System.out.println("Decimal value: "+result);
		String toBin = convertToBin(result);
		System.out.println("Binary value: "+toBin);
	}
	
	public static void sub(int v1, int v2) {
		int result = v1-v2;
		System.out.println("Decimal value: "+result);
		String toBin = convertToBin(result);
		System.out.println("Binary value: "+toBin);
	}
	
	public static void mult(int v1, int v2) {
		int result = v1*v2;
		System.out.println("Decimal value: "+result);
		String toBin = convertToBin(result);
		System.out.println("Binary value: "+toBin);
	}
	
	public static void div(int v1, int v2) {
		int result = v1/v2;
		System.out.println("Decimal value: "+result);
		String toBin = convertToBin(result);
		System.out.println("Binary value: "+toBin);
	}
}

