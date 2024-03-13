import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class RegExp {
    
    public static void main(String[] args) {
        
        String str1 = args[1];
        String str2 = args[2];
        int s2Count = Integer.parseInt(args[3]);

        //For your testing of input correctness
        //System.out.println("The input file:"+args[0]);
        //System.out.println("str1="+str1);
        //System.out.println("str2="+str2);
        //System.out.println("num of repeated requests of str2 = "+s2Count);

        try {
            BufferedReader reader = new BufferedReader(new FileReader(args[0]));
            String line;
            while ((line = reader.readLine()) != null) {
                //You main code should be invoked here
                //condition 1
                String sc1 = line.toLowerCase();
                char[] testString = sc1.toCharArray();
                
            
                boolean testp = true;
                for(int i = 0; i < testString.length / 2 ; i++){
                    int j = testString.length - (1 + i );
                    if(testString[i] != testString[j]){
                        testp = false;
                        break;
                    }
                }
                System.out.print((testp ? "Y," : "N,"));
                
                //condition 2
                boolean testStr1 = false;
                if(sc1.contains(args[1].toLowerCase())){
                    testStr1 = true;
                }
                System.out.print((testStr1 ? "Y," : "N,"));

                //condition 3
                int count = 0;
                int index = sc1.indexOf(args[2].toLowerCase());
                boolean testStr2N = true;
                while(index != -1){
                    count++;
                    index = sc1.indexOf(args[2].toLowerCase() , index + 1 );
                }
                if(count < s2Count){
                    testStr2N = false;
                }


                System.out.print(( testStr2N ? "Y," : "N,"));

                //condition 4
                boolean testContinue = false;
                int index1 = sc1.indexOf("a");
                
                for(int i = index1 + 1 ; i < sc1.length() -1 ; i++){
                    if(sc1.charAt(i) == sc1.charAt(i + 1) && sc1.charAt(i) == 'b'){
                        testContinue = true;
                        break;
                    }
                }
                if(index1 == -1){
                    testContinue = false;
                }
                System.out.println((  testContinue ? "Y" : "N"));
            }
            reader.close();

        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
