# Practica-1

using System;
using System.Collections.Generic;

namespace ControlPersonas
{
    class Program
    {
        static void Main(string[] args)
        {
            int cantidad;

            // Validar cantidad
            while (true)
            {
                Console.Write("Ingrese la cantidad de personas: ");
                if (int.TryParse(Console.ReadLine(), out cantidad) && cantidad >= 1)
                    break;

                Console.WriteLine("Cantidad inválida. Intente de nuevo.\n");
            }

            List<string> nombres = new List<string>();
            List<int> edades = new List<int>();

            // Registro
            for (int i = 0; i < cantidad; i++)
            {
                Console.WriteLine($"\nPersona {i + 1}");

                Console.Write("Nombre: ");
                string nombre = Console.ReadLine();

                int edad;
                while (!int.TryParse(Console.ReadLine(), out edad) || edad < 0)
                {
                    Console.Write("Edad inválida. Ingrese nuevamente: ");
                }

                nombres.Add(nombre);
                edades.Add(edad);
            }

            if (cantidad == 1)
            {
                Console.WriteLine("\nResultado:");
                Console.WriteLine(edades[0] >= 18
                    ? $"{nombres[0]} es mayor de edad."
                    : $"{nombres[0]} es menor de edad.");
            }
            else
            {
                Console.WriteLine("\n--- Lista General ---");
                for (int i = 0; i < cantidad; i++)
                    Console.WriteLine($"{nombres[i]} - {edades[i]} años");

                Console.WriteLine();

                bool hayMayores = false, hayMenores = false;

                for (int i = 0; i < cantidad; i++)
                {
                    if (edades[i] >= 18 && !hayMayores)
                    {
                        Console.WriteLine("Mayores de edad:");
                        hayMayores = true;
                    }

                    if (edades[i] < 18 && !hayMenores)
                    {
                        Console.WriteLine("Menores de edad:");
                        hayMenores = true;
                    }
                }

                for (int i = 0; i < cantidad; i++)
                {
                    if (edades[i] >= 18)
                        Console.WriteLine($"{nombres[i]} - {edades[i]} años");
                }

                for (int i = 0; i < cantidad; i++)
                {
                    if (edades[i] < 18)
                        Console.WriteLine($"{nombres[i]} - {edades[i]} años");
                }
            }

            Console.ReadKey();
        }
    }
}

   
