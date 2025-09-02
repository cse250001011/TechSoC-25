# PS1: The Secret Message - Caesar Cipher Challenge

## Overview
You've intercepted a secret message, but it's encoded using an ancient encryption technique called the **Caesar Cipher**. Your goal is to build a program that can both encode and decode messages.

## What is a Caesar Cipher?
The Caesar Cipher is one of the oldest and simplest encryption techniques, named after Julius Caesar who used it to protect his military communications. It works by shifting each letter in the alphabet by a fixed number of positions.

### How it Works:
- Choose a **shift value** (e.g., 3)
- Move each letter forward in the alphabet by that many positions
- When you reach the end of the alphabet, wrap around to the beginning

### Example with shift = 3:
```
Original:  A B C D E F G ... X Y Z
Shifted:   D E F G H I J ... A B C

'A' → 'D'
'B' → 'E'  
'C' → 'F'
...
'X' → 'A' (wraps around)
'Y' → 'B' (wraps around)
'Z' → 'C' (wraps around)
```

**Example Message:**
- Original: `HELLO WORLD`
- Encoded (shift +3): `KHOOR ZRUOG`
- To decode: shift back by -3

## Your Tasks

### Level 1: Basic Caesar Cipher
Implement functions to:
1. **Encode** a message with a given shift value
2. **Decode** a message with a known shift value
3. Handle both uppercase and lowercase letters
4. Keep non-alphabetic characters (spaces, punctuation) unchanged

## Learning Objectives
By completing this challenge, you will:
- Understand basic programming concepts
- Practice string manipulation and ASCII operations
- Implement loops and conditional logic
- Handle edge cases and input validation
- Debug and test your code systematically
- Think about algorithm efficiency and security
- #include <iostream>
using namespace std;

int main()
{
    string s;
    cout << "Enter shift value: ";
    int shift;
    cin >> shift;

    cin.ignore(); // <-- important, clear newline from buffer

    cout << "Enter message to be encoded: ";
    getline(cin, s);

    int i;
    char ch;
    int n = s.length();
    string enc = "";
    shift = shift % 26;

   
    for(i=0;i<n;i++)
    {
        ch=s[i];
        if(ch>=65 && ch<=90)
        {
            ch+=shift;
            if(ch>90)
            {
                ch=ch-26;
            }
        }
        else if(ch>=97 && ch<=122)
        {
            ch-=(26-shift);
            if(ch<97)
            {
                ch=ch+26;
            }
        }
        enc+=ch;
    }
    string dec="";
    cout<<"Encoded message: "<<enc<<endl;
    for(i=0;i<n;i++)
    {
        ch=enc[i];
        if(ch>=65 && ch<=90)
        {
            ch-=shift;
            if(ch<65)
            {
                ch=ch+26;
            }
        }
        else if(ch>=97 && ch<=122)
        {
            ch-=shift;
            if(ch<97)
            {
                ch=ch+26;
            }
        }
        dec+=ch;
    }
    cout<<"Decoded message: "<<dec<<endl;
    return 0;
}
