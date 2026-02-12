# Practica-1

using System;
using System.Collections.Generic;

namespace RegistroPersonas
{
    class Program
    {
        static void Main(string[] args)
        {
            int numPersonas;

            // Validación de cantidad de personas
            while (true)
            {
                Console.Write("Ingrese el número de personas a registrar (mínimo 1): ");
                if (int.TryParse(Console.ReadLine(), out numPersonas) && numPersonas >= 1)
                    break;

                Console.WriteLine("Error: Debe ingresar un número válido mayor o igual a 1.\n");
            }

            List<(string Nombre, int Edad)> personas = new List<(string Nombre, int Edad)>();

            // Registro de personas
            for (int i = 0; i < numPersonas; i++)
            {
                Console.WriteLine($"\nPersona {i + 1}");

                string nombre;
                while (true)
                {
                    Console.Write("Nombre: ");
                    nombre = Console.ReadLine();

                    if (!string.IsNullOrWhiteSpace(nombre))
                        break;

                    Console.WriteLine("Error: El nombre no puede estar vacío.");
                }

                int edad;
                while (true)
                {
                    Console.Write("Edad: ");
                    if (int.TryParse(Console.ReadLine(), out edad) && edad >= 0)
                        break;

                    Console.WriteLine("Error: Edad inválida. Ingrese un número válido mayor o igual a 0.");
                }

                personas.Add((nombre, edad));
            }

            // Caso especial: una sola persona
            if (numPersonas == 1)
            {
                var persona = personas[0];

                Console.WriteLine("\nResultado:");
                if (persona.Edad >= 18)
                    Console.WriteLine($"{persona.Nombre} tiene {persona.Edad} años y es mayor de edad.");
                else
                    Console.WriteLine($"{persona.Nombre} tiene {persona.Edad} años y es menor de edad.");
            }
            else
            {
                // Lista general
                Console.WriteLine("\n===== LISTA GENERAL =====");
                foreach (var persona in personas)
                {
                    Console.WriteLine($"{persona.Nombre} - {persona.Edad} años");
                }

                // Clasificación
                List<(string Nombre, int Edad)> mayores = new List<(string Nombre, int Edad)>();
                List<(string Nombre, int Edad)> menores = new List<(string Nombre, int Edad)>();

                foreach (var persona in personas)
                {
                    if (persona.Edad >= 18)
                        mayores.Add(persona);
                    else
                        menores.Add(persona);
                }

                // Mostrar mayores
                if (mayores.Count > 0)
                {
                    Console.WriteLine("\n===== MAYORES DE EDAD =====");
                    foreach (var persona in mayores)
                    {
                        Console.WriteLine($"{persona.Nombre} - {persona.Edad} años");
                    }
                }

                // Mostrar menores
                if (menores.Count > 0)
                {
                    Console.WriteLine("\n===== MENORES DE EDAD =====");
                    foreach (var persona in menores)
                    {
                        Console.WriteLine($"{persona.Nombre} - {persona.Edad} años");
                    }
                }
            }

            Console.WriteLine("\nPrograma finalizado.");
            Console.ReadKey();
        }
    }
}

   
