1
1
1
1
1
1
1
1
1

1
11

using System;
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
        string results = string.Empty;
        string alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        string[] rotors = new string[3];
        string result = "XPCXAUPHYQALKJMGKRWPGYHFTKRFFFNOUTZCABUAEHQLGXREZ";

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
            for (int i = 0; i < encrypt_1.Length; i++)
            {
                int index = alphabet.IndexOf(encrypt_1[i]);
                encrypt_2 += rotors[1][index];
            }
            Console.Error.WriteLine($"encrypted 2 message = {encrypt_2}");

            string encrypt_3 = "";
            for (int i = 0; i < encrypt_2.Length; i++)
            {
                int index = alphabet.IndexOf(encrypt_2[i]);
                encrypt_3 += rotors[2][index];
            }
            Console.Error.WriteLine($"encrypted 3 message = {encrypt_3}");
            result = encrypt_3;
        }
        else if (operation == "DECODE")
        {
            // Декодування rotors[2]
            string decrypted_3 = "";
            for (int i = 0; i < result.Length; i++)
            {
                int index = rotors[2].IndexOf(result[i]);
                decrypted_3 += alphabet[index];
            }

            // Декодування rotors[1]
            string decrypted_2 = "";
            for (int i = 0; i < decrypted_3.Length; i++)
            {
                int index = rotors[1].IndexOf(decrypted_3[i]);
                decrypted_2 += alphabet[index];
            }

            // Декодування rotors[0]
            string decrypted_1 = "";
            for (int i = 0; i < decrypted_2.Length; i++)
            {
                int index = rotors[0].IndexOf(decrypted_2[i]);
                decrypted_1 += alphabet[index];
            }

            // Декодування shift_message
            string original_message = "";
            for (int i = 0; i < decrypted_1.Length; i++)
            {
                int index = alphabet.IndexOf(decrypted_1[i]);
                int shift_index = (index - pseudoRandomNumber - i) % alphabet.Length;
                if (shift_index < 0)
                    shift_index += alphabet.Length;
                original_message += alphabet[shift_index];
            }

            result = original_message;
        }
        Console.WriteLine(result);
    }
}
