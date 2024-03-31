Counting the number of vowels in a string
In this article, we will learn how to write a C++ program to count the number of vowels in a string.

First, we will accept the string
Then we will iterate each character of the string through a for loop
If the character iterated is found to be a vowel (i.e. ‘A’, ‘E’, ‘I’, ‘O’, ‘U’)
Then we will increase the count of vowels by one.
We will have to check for both upper case and lower case at every iteration as C++ programming is case sensitive.
Program count the number of vowels in a string
Algorithm:
Accept the input.
Initialize the count vowel variable.
Initialize for loop and terminate it at the end of the string.
Check and count the number of vowels in a string.
Print total count of vowels.
C++ program to count the number of vowels in a string
Run
// Write a c++ program to read a string and find the number of vowels in it
#include <iostream>
#include <stdio.h>

using namespace std;

int main()
{
    char str[100] = "prepinsta";
    int vowels = 0;
    
    // can also do str[i] != '\0' in condition below both would work
    for(int i = 0; str[i]; i++)  
    {
        if(str[i]=='a'|| str[i]=='e'||str[i]=='i'||str[i]=='o'||str[i]=='u'
        ||str[i]=='A'||str[i]=='E'||str[i]=='I'||str[i]=='O' ||str[i]=='U')
        {
		    vowels++;
        }
    }
    
    cout << "Total Vowels : " << vowels;
    
    return 0;
}
Output
Total Vowels : 3
Note
The time complexity of above code in O(n) as in the code we are looping over the sting once. Also space complexity is O(1)
Method 2
The above method has separate conditions for lowercase and uppercase vowels. We can convert each lowercase char to upper case and test for only one condition. Since we need to only tell the count this won’t affect the implementation and output.
Run
#include <iostream>
#include <stdio.h>

using namespace std;

bool isVowel(char c){
    // converts char to upper case if it was lowercase
    c = toupper(c);
    
    // returns true if any of the condition matches
    return c=='A'||c=='E'||c=='I'||c=='O' ||c=='U';
}

int main()
{
    char str[100] = "prepinsta";
    int vowels = 0;
    
    // can also do str[i] != '\0' in condition below both would work
    for(int i = 0; str[i]; i++)  
    {
        if(isVowel(str[i]))
		    vowels++;
        
    }
    
    cout << "Total Vowels : " << vowels;
    
    return 0;
}
Output
Total Vowels : 3
Note
The time complexity of above code in O(n) as in the code we are looping over the sting once. Also space complexity is O(1)
Related Pages
Juggling algorithm for array rotation
 
Balanced Parenthesis Problem
 
Toggle each character in a string

Find the ASCII value of a character

Length of the string without using strlen() function

While loop in C
Method 3 (Using Recursion)
This method below uses recursion in C++

Run
#include <iostream>
using namespace std;

// Function to check the Vowel
// returns true of any character below is matched
bool isVowel(char ch) {
    ch = toupper(ch);
    
    return (ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U');
}

// to count total number of vowel from 0 to n
int countVovels(string str, int n) {
    if (n == 0) 
        return isVowel(0);
    
    return countVovels(str, n - 1) + isVowel(str[n]);
}

// main Function
int main() 
{
    // string object
    string str = "prepinsta";
    
    int len = str.length();
    
    // Total numbers of Vowel
    cout << "Vowels in " << str << ": ";
    
    // sending len - 1 as last character will be at that position
    cout << countVovels(str, len - 1);
    
    return 0;
}
Output
Vowels in prepinsta: 3
Note
The time complexity of above code in O(n) as in the code we are looping over the sting once.
The space complexity will be O(1). But the auxiliary space complexity will be O(N) due to function call stack.
Method 4
We can use a pointer-based function approach also to count the number of vowels, below is an implementation of this.
Run
#include <iostream> 
  
using namespace std;
  
int countVowels(char *chrPtr)
{
    // to count total number of vowels
    int count = 0;
  
    // Keep reading each character till string terminates
    // string will terminate when we read '\0'
    while ((*chrPtr) != '\0') 
    {
        // convert to uppercase
        (*chrPtr) = toupper((*chrPtr));
        
        // Check whether character pointer finds any vowels
        if (*chrPtr == 'A' || *chrPtr == 'E' || *chrPtr == 'I'
            || *chrPtr == 'O' || *chrPtr == 'U') {
  
            // if true then increment count
            count++;
        }
  
        // Move to next char of string by incrementing pointer val
        // pointer now points to next node
        chrPtr++;
    }
  
    return count;
}
  
// Driver Code
int main()
{
    // Initialize the string
    char str[] = "Prepinsta";
  
    // Display the count
    cout << "Vowel Count: " << countVowels(str);
  
    return 0;
}
Output
Vowel Count: 3
Prime Course Trailer

Related Banners
Get PrepInsta Prime & get Access to all 200+ courses offered by PrepInsta in One Subscription

Get Prime
Note
The time complexity of above code in O(n) as in the code we are looping over the sting once.
The space complexity will be O(1).
