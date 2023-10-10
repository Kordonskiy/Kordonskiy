- 👋 Hi, I’m @Kordonskiy
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Kordonskiy/Kordonskiy is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->using System;
using System.Linq;
using System.IO;
using System.Text;
using System.Collections;
using System.Collections.Generic;

/**
 * Auto-generated code below aims at helping you parse
 * the standard input according to the problem statement.
 **/
class Solution
{
    static void Main(string[] args)
    {
        string alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        string[] rotors = new string[3];
        
        string operation = Console.ReadLine();
        Console.Error.WriteLine($"operation = {operation}");

        int pseudoRandomNumber = int.Parse(Console.ReadLine());
        Console.Error.WriteLine($"pseudoRandomNumber = {pseudoRandomNumber}");

        for (int i = 0; i < 3; i++)
        {
            string rotor = Console.ReadLine();
            Console.Error.WriteLine($"rotor[{i}] = {rotor}");
            rotors[i] = rotor;
        }
        string message = Console.ReadLine();
        Console.Error.WriteLine($"message = {message}");
        
        if (operation == "ENCODE")
        {
            string shift_message = "";
            for (int i = 0; i < message.Length; i++)
            {
                int index = alphabet.IndexOf(message[i]);
                int shift_index = (index + pseudoRandomNumber + i) % alphabet.Length;
                shift_message += alphabet[shift_index];
            }
            Console.Error.WriteLine($"shifted message = {shift_message}");

            string encrypt_1 = "";
            for (int i = 0; i < shift_message.Length; i++)
            {
                int index = alphabet.IndexOf(shift_message[i]);
                encrypt_1 += rotors[0][index];
            }
            Console.Error.WriteLine($"encrypted 1 message = {encrypt_1}");

            string encrypt_2 = "";
            for (int i = 0; i < encrypt_1.Length; i++);
            {
                int index = alphabet.IndexOf(encrypt_1[i]);
                encrypt_2 += rotors[1][index];
            }
            Console.Error.WriteLine($"encrypted 2 message = {encrypt_2}");

            string encrypt_3 = "";
            for (int i = 0; i < encrypt_2.Length; i++);
            {
                int index = alphabet.IndexOf(encrypt_2[i]);
                encrypt_3 += rotors[2][index];
            }
            Console.Error.WriteLine($"encrypted 2 message = {encrypt_3}");
            result = encrypt_3;

            
        }
        else if (operation == "DECODE")
        {

        }


        Console.WriteLine("result"); 
    }
}
