# Practica-1
using System;
using System.Collections.Generic;

namespace ProgramacionEstructurada22
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // Obtener cantidad válida de personas
            int cantidadPersonas = ObtenerCantidadPersonas();

            // Registrar personas
            List<string> nombres = new List<string>();
            List<int> edades = new List<int>();

            for (int i = 1; i <= cantidadPersonas; i++)
            {
                Console.Write($"Ingresa el nombre de la persona {i}: ");
                string nombre = Console.ReadLine();

                int edad = ObtenerEdadValida($"Ingresa la edad de {nombre}: ");

                nombres.Add(nombre);
                edades.Add(edad);
            }

            // Mostrar resultados según la cantidad de personas
            if (cantidadPersonas == 1)
            {
                // Caso especial: una sola persona
                MostrarPersonaUnica(nombres[0], edades[0]);
            }
            else
            {
                // Caso general: dos o más personas
                MostrarResultadosGenerales(nombres, edades);
            }

            Console.WriteLine("\nPrograma finalizado.");
            Console.ReadKey();
        }

        /// <summary>
        /// Solicita y valida la cantidad de personas a registrar
        /// </summary>
        static int ObtenerCantidadPersonas()
        {
            while (true)
            {
                Console.Write("Ingresa la cantidad de personas a clasificar: ");
                if (int.TryParse(Console.ReadLine(), out int cantidad) && cantidad >= 1)
                {
                    return cantidad;
                }
                Console.WriteLine("⚠ Error: Debes ingresar un número válido mayor o igual a 1.\n");
            }
        }

        /// <summary>
        /// Solicita y valida la edad de una persona
        /// </summary>
        static int ObtenerEdadValida(string mensaje)
        {
            while (true)
            {
                Console.Write(mensaje);
                if (int.TryParse(Console.ReadLine(), out int edad) && edad >= 0 && edad <= 120)
                {
                    return edad;
                }
                Console.WriteLine("⚠ Error: Debes ingresar una edad válida (número entre 0 y 120).\n");
            }
        }

        /// <summary>
        /// Muestra información de una única persona
        /// </summary>
        static void MostrarPersonaUnica(string nombre, int edad)
        {
            Console.WriteLine();
            if (edad >= 18)
            {
                Console.WriteLine($"{nombre} es mayor de edad.");
            }
            else
            {
                Console.WriteLine($"{nombre} es menor de edad.");
            }
        }

        /// <summary>
        /// Muestra resultados para dos o más personas
        /// </summary>
        static void MostrarResultadosGenerales(List<string> nombres, List<int> edades)
        {
            // Separar en mayores y menores
            List<string> nombresMayores = new List<string>();
            List<int> edadesMayores = new List<int>();

            List<string> nombresMenores = new List<string>();
            List<int> edadesMenores = new List<int>();

            for (int i = 0; i < nombres.Count; i++)
            {
                if (edades[i] >= 18)
                {
                    nombresMayores.Add(nombres[i]);
                    edadesMayores.Add(edades[i]);
                }
                else
                {
                    nombresMenores.Add(nombres[i]);
                    edadesMenores.Add(edades[i]);
                }
            }

            // Mostrar lista general
            MostrarListaGeneral(nombres, edades);

            // Mostrar mayores de edad (si existen)
            if (nombresMayores.Count > 0)
            {
                MostrarListaMayores(nombresMayores, edadesMayores);
            }

            // Mostrar menores de edad (si existen)
            if (nombresMenores.Count > 0)
            {
                MostrarListaMenores(nombresMenores, edadesMenores);
            }
        }

        /// <summary>
        /// Muestra la lista general de personas
        /// </summary>
        static void MostrarListaGeneral(List<string> nombres, List<int> edades)
        {
            Console.WriteLine("\n========== LISTA GENERAL ==========");
            for (int i = 0; i < nombres.Count; i++)
            {
                Console.WriteLine($"{nombres[i]} - {edades[i]} años");
            }
        }

        /// <summary>
        /// Muestra la lista de personas mayores de edad
        /// </summary>
        static void MostrarListaMayores(List<string> nombres, List<int> edades)
        {
            Console.WriteLine("\n===== PERSONAS MAYORES DE EDAD =====");
            for (int i = 0; i < nombres.Count; i++)
            {
                Console.WriteLine($"{nombres[i]} - {edades[i]} años");
            }
        }

        /// <summary>
        /// Muestra la lista de personas menores de edad
        /// </summary>
        static void MostrarListaMenores(List<string> nombres, List<int> edades)
        {
            Console.WriteLine("\n===== PERSONAS MENORES DE EDAD =====");
            for (int i = 0; i < nombres.Count; i++)
            {
                Console.WriteLine($"{nombres[i]} - {edades[i]} años");
            }
        }
    }
}
