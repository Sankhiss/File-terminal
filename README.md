using System;
using System.IO;

namespace Terminal_files
{
    public static class Program
    {
        public static void Main()
        {
            Console.WriteLine("enter the number of files/введите число файлов цыфрой");

            string filesD = Console.ReadLine();
            int files = Convert.ToInt32(filesD);
            string[] file = new string[files];

            for (int a = 0; a < files; a++)
            {
                Console.WriteLine($"Enter the name for file {a + 1}:");
                string d = Console.ReadLine();
                file[a] = d;
                File.WriteAllText($"{d}.txt", d);
            }

            while (true)
            {
                Console.WriteLine("change file value/измените значение (type 'redact file' to edit, 'clear' to delete all files, or 'exit' to quit):");
                string bd = Console.ReadLine();
                if (bd == "redact file")
                {
                    Console.WriteLine("Enter the name of the file to change:");
                    string gg = Console.ReadLine();
                    Console.WriteLine("Enter the new value:");
                    string bb = Console.ReadLine();
                    int index = Array.IndexOf(file, gg);
                    if (index != -1)
                    {
                        file[index] = bb;
                        File.WriteAllText($"{gg}.txt", bb);
                        Console.WriteLine("Element updated successfully.");
                    }
                    else
                    {
                        Console.WriteLine("No such element found.");
                    }

                    Console.WriteLine("Updated file list:");
                    foreach (var f in file)
                    {
                        Console.WriteLine(f);
                    }
                }
                else if (bd == "clear")
                {
                    foreach (var f in file)
                    {
                        if (File.Exists($"{f}.txt"))
                        {
                            File.Delete($"{f}.txt");
                        }
                    }
                    Console.WriteLine("All files deleted.");
                }
                else if (bd == "exit")
                {
                    break;
                }
            }
        }
    }
}

