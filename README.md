
using System;
using System.Collections.Generic;
class Student
{
    public int id;
    public string name;
    public int age;
    
}
class givenprog
{
    
     static List <Student> students = new List<Student>();
     static void AddStudent(int id,string name,int age)
     {
          for (int i=0;i<students.Count;i++)
          {
              if(students[i].id == id)
              {
                  Console.WriteLine("Student with same Id Already exists.");
                  return;
              }
          }
          Student s = new Student();
          s.id = id;
          s.name = name;
          s.age = age;
          students.Add(s);
     }
     static void allstu()
     {
         for(int i=0;i<students.Count;i++)
         {
             Console.WriteLine(students[i].id+" "+students[i].name+" "+students[i].age);
         }
         static void morethan20()
         {
             for(int i=0;i<students.Count;i++)
             {
                 if(students[i].age>20)
                 {
                     Console.WriteLine(students[i].name+" "+students[i].age);
                 }
             }
         }
         static void upstu(int id, string update,int newage)
         {
             bool newid = false;
             for( int i=0;i<students.Count;i++)
             {
                 if(students[i].id == id)
                 {
                     students[i].name = update;
                     students[i].age = newage;
                     newid= true;
                     break;
                 }
             }
             if(newid == false)
             {
                 Console.WriteLine("Student Id not Found.");
             }
         }
         static void delete(int id)
         {
             int ind = -1;
             for (int i=0; i<students.Count;i++)
             {
                 if(students[i].id == id)
                 {
                     ind = i;
                     break;
                 }
             }
             if(ind != -1)
             {
                 students.RemoveAt(ind);
             }
             else
                 Console.WriteLine("Student not Present");
         }
         static void youngandold()
         {
             if ( students.Count == 00)
                 return;
             Student y = students[0];
             Student o = students[0];
             for ( int i= 1;i<students.Count;i++)
             {
                 if (students[i].age<y.age)
                     y= students[i];
                if (students[i].age > o.age)
                     o= students[i];
             }
             Console.WriteLine("Youndest One :"+ y.name+" "+y.age);
             Console.WriteLine("Oldest One :"+ o.name+" "+o.age);
         }
         static void acc()
         {
             students.sort((a,b) => a.name.CompareTo(b.name));
             Console.WriteLine("Aphlabetical order ");
             allstu();
         }
         static void byage()
         {
             students.Sort((a,b) => b.age.CompareTo(a.age));
             Console.WriteLine("By Age in Descending Order :");
             allstu();
         }
         static void let(char l)
         {
             Console.WriteLine("Names with Letter "+l);
             for(int i=0;i<students.Count;i++)
             {
                 if(students[i].name.StartsWith(l.ToString(),StringComparison.OrdinalIgnoreCase))
                     Console.WriteLine(students[i].name);
             }
         }
         static void group()
         {
             Dictionary<int,int> ac =new Dictionary<int,int>();
             for(int i=0;i<students.Count;i++)
             {
                 int a = students[i].age;
                 if(ac.ContainsKey(a))
                 ac[a]++;
                 else
                 ac[a] = 1;
             }
             Console.WriteLine("Age Group :");
             foreach(var pair in ac)
             {
                 Console.WriteLine("age" + pair.Key+" "+pair.Value+"students(s)");
             }
         }
         static void main()
         {
             AddStudent(1,"john",19);
             AddStudent(2,"vijay",20);
             AddStudent(3,"arun",18);
             AddStudent(4,"mickey",21);
             AddStudent(5,"zoya",26);
             Console.WriteLine(" all students");
             allstu();
             Console.WriteLine("Students Older than 20");
             morethan20();
             Console.WriteLine("Update Student ");
             upstu(5,"Ajay",22);
             delete(3);
             allstu();
             Console.WriteLine("Youngest an Oldest ");
             youngandold();
             Console.WriteLine("By Name");
             acc();
             Console.WriteLine("By Age");
             byage();
             Console.WriteLine("by Letter");
             let(l);
             Console.WriteLine(" by age group ");
             group();
         }
     }
}









