#### How to perform multiplication using bitwise operator?  
As introduced in [stackoverflow](https://stackoverflow.com/questions/3722004/how-to-perform-multiplication-using-bitwise-operators). 
1. iteratively add the number. 
2.the bitwise operation works like this:  
e.g 8*5:  
5 = 2^2 + 1. 
8*5 = 8*2^2 + 8 = 8<<2 + 8  
    public int bitwise_multiplication(int a, int b) {
    	if (a==0 || b == 0) return 0;
    	boolean neg = false;
    	if (a>0 && b<0) {
    		neg = true;
    		b = -b;
    	}
    	if (a<0 && b>0) {
    		neg = true;
    		a = -a;
    	}
    	int res = 0;
    	while (b>0) {
    		if (b&1)  // Bitwise & of the value of b with 01, only add if it is odd, this can be concluded with some examples
    			res+=a;
    		b >>= 1;
    		a <<= 1;
    		
    	}
    					
    }

#### How to convert a string into integer without using Integer.parseInt. 
[explanation](http://javahungry.blogspot.com/2014/02/how-to-convert-string-to-int-in-java-without-using-integer-parseint-method-code-with-example.html). 
