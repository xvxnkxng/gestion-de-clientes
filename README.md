# gestion-de-clientes

using System;
using System.Collections.Generic;

class Cliente
{
    public string Nombre { get; set; }
    public string Email { get; set; }

    public Cliente(string nombre, string email)
    {
        Nombre = nombre;
        Email = email;
    }
}

class Program
{
    static List<Cliente> clientes = new List<Cliente>();

    static void Main()
    {
        int opcion;

        do
        {
            Console.WriteLine("\n--- MINI CRM ---");
            Console.WriteLine("1. Agregar cliente");
            Console.WriteLine("2. Ver clientes");
            Console.WriteLine("3. Buscar cliente");
            Console.WriteLine("0. Salir");
            Console.Write("Opción: ");

            opcion = int.Parse(Console.ReadLine());

            switch (opcion)
            {
                case 1:
                    AgregarCliente();
                    break;
                case 2:
                    MostrarClientes();
                    break;
                case 3:
                    BuscarCliente();
                    break;
            }

        } while (opcion != 0);
    }

    static void AgregarCliente()
    {
        Console.Write("Nombre: ");
        string nombre = Console.ReadLine();

        Console.Write("Email: ");
        string email = Console.ReadLine();

        clientes.Add(new Cliente(nombre, email));
    }

    static void MostrarClientes()
    {
        foreach (var cliente in clientes)
        {
            Console.WriteLine($"Nombre: {cliente.Nombre} - Email: {cliente.Email}");
        }
    }

    static void BuscarCliente()
    {
        Console.Write("Ingrese nombre a buscar: ");
        string busqueda = Console.ReadLine();

        foreach (var cliente in clientes)
        {
            if (cliente.Nombre.ToLower().Contains(busqueda.ToLower()))
            {
                Console.WriteLine($"Encontrado: {cliente.Nombre} - {cliente.Email}");
            }
        }
    }
}
