# Calculadora-De-Media

#Descrição

O projeto tem como ideia principal facilitar a vida de um estudante comum que esteja precisando calcular sua média final e não sabe muito bem o que fazer.
Para desenvolvermos o código utilizamos 2 classes (Boletim e Aluno) Cujo o aluno recebe um nome e um boletim como atributos e o boletim recebe as notas do aluno.
A classe Boletim possui os métodos ColetarNotas() e CalcularMedia()


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


Dia 04/11 

O que foi feito? 

Já fizemos basicamente o código completo, criamos as duas classes, instânciamos
em program e também já implementamos para criar um arquivo txt e ler o mesmo no final no projeto.
No momento estamos trabalhando em algumas possíveis otimizações pois ainda temos tempo.

Segue a baixo o que já temos pronto: 

using System;
using System.IO;
using System.Collections.Generic;

namespace Objetos
{

    class Boletim
    {
        public double Geo, Mat, His, Por, Fis, Qui, Bio, Média;
        public double[] notas = new double[] { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 };
        public void ColetarNotas()
        {
            Console.WriteLine("Informe suas notas do semestre... ");
            Console.WriteLine("");
            
            Console.WriteLine("Informe sua nota em Geografia:");
            notas[0] = Convert.ToDouble(Console.ReadLine());
            Geo = notas[0];

            while (Geo > 10 || Geo < 0)
            {
                Console.WriteLine("Houve algum erro na digitação da nota. Informe um número de 0 a 10. Ex: 1.0, 2, 9.3");
                notas[0] = Convert.ToDouble(Console.ReadLine());
                Geo = notas[0];
            }

            Console.WriteLine("Informe sua nota em Matemática:");
            notas[1] = Convert.ToDouble(Console.ReadLine());
            Mat = notas[1];

            while (Mat > 10 || Mat < 0)
            {
                Console.WriteLine("Houve algum erro nadigitação da nota. Informe um número de 0 a 10. Ex: 1.0, 2, 9.3");
                notas[1] = Convert.ToDouble(Console.ReadLine());
                Mat = notas[1];
            }

            Console.WriteLine("Informe sua nota em História:");
            notas[2] = Convert.ToDouble(Console.ReadLine());
            His = notas[2];

            while (His > 10 || His < 0)
            {
                Console.WriteLine("Houve algum erro nadigitação da nota. Informe um número de 0 a 10. Ex: 1.0, 2, 9.3");
                notas[2] = Convert.ToDouble(Console.ReadLine());
                His = notas[2];
            }

            Console.WriteLine("Informe sua nota em Português:");
            notas[3] = Convert.ToDouble(Console.ReadLine());
            Por = notas[3];
            
            while (Por > 10 || Por < 0)
            {
                Console.WriteLine("Houve algum erro nadigitação da nota. Informe um número de 0 a 10. Ex: 1.0, 2, 9.3");
                notas[3] = Convert.ToDouble(Console.ReadLine());
                Por = notas[3];
            }

            Console.WriteLine("Informe sua nota em Física:");
            notas[4] = Convert.ToDouble(Console.ReadLine());
            Fis = notas[4];

            while (Fis > 10 || Fis < 0)
            {
                Console.WriteLine("Houve algum erro nadigitação da nota. Informe um número de 0 a 10. Ex: 1.0, 2, 9.3");
                notas[4] = Convert.ToDouble(Console.ReadLine());
                Fis = notas[4];
            }

            Console.WriteLine("Informe sua nota em Química:");
            notas[5] = Convert.ToDouble(Console.ReadLine());            
            Qui = notas[5];

            while (Qui > 10 || Qui < 0)
            {
                Console.WriteLine("Houve algum erro nadigitação da nota. Informe um número de 0 a 10. Ex: 1.0, 2, 9.3");
                notas[5] = Convert.ToDouble(Console.ReadLine());
                Qui = notas[5];
            }

            Console.WriteLine("Informe sua nota em Biologia:");
            notas[6] = Convert.ToDouble(Console.ReadLine());
            Bio = notas[6];

            while (Bio > 10 || Bio < 0)
            {
                Console.WriteLine("Houve algum erro nadigitação da nota. Informe um número de 0 a 10. Ex: 1.0, 2, 9.3");
                notas[6] = Convert.ToDouble(Console.ReadLine());
                Bio = notas[6];
            }
        }

        public void CalcularMedia()
        {
            Média = (notas[0] + notas[1] + notas[2] + notas[3] + notas[4] + notas[5] + notas[6])/ 7;
        }
    }




    class Aluno
    {

        public string nome;
        public Boletim boletim;


        public Aluno(string n)
        {
            nome = n;
        }
    }


    class Program
    {
        public static void Main(string[] args)
        {
            string nome1;
            Console.WriteLine("De um nome ao aluno(a):");
            nome1 = Console.ReadLine();
            Aluno aluno1 = new Aluno(nome1);
            Boletim boletim1 = new Boletim();
            boletim1.ColetarNotas();
            boletim1.CalcularMedia();
            aluno1.boletim = boletim1;

            StreamWriter escritor = new StreamWriter("Resultado.txt");
            if (aluno1.boletim.Média > 6)
            {
                escritor.WriteLine("Parabéns, " + aluno1.nome + " ,você está aprovado, sua média foi " + aluno1.boletim.Média);
            }
            else if (aluno1.boletim.Média < 6)
            {
                escritor.WriteLine("Poxa vida, " + aluno1.nome + " ,infelizmente você foi reprovado, sua média foi " + aluno1.boletim.Média);
            }
            escritor.Close();

            StreamReader Leitor = new StreamReader("Resultado.txt");
            string lido = Leitor.ReadLine();
            Console.WriteLine("");
            Console.WriteLine("A seguir, o resultado do seu teste, extraído de 'Resultado.txt'");
            Console.WriteLine(lido);
        }
    }
} 


Link da apresentação https://youtu.be/OnEi8GDfy7k
