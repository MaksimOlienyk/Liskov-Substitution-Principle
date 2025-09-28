# Liskov-Substitution-Principle
Цей приклад демонструє застосування LSP у C#.  

---

code:

```csharp
using System;

namespace Liskov_substitution_principle
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Enemy dragon = new Dragon();
            dragon.Attack();

            Enemy ogre = new Ogre();
            ogre.Attack();

            // FlyingEnemy ogre2 = new Ogre(); // не працює — і це правильно
        }
    }

    interface Enemy
    {
        void Attack();
    }

    interface FlyingEnemy : Enemy
    {
        void Fly();
    }

    class Dragon : FlyingEnemy
    {
        public void Attack() => Console.WriteLine("Дракон б'є хвостом");
        public void Fly() => Console.WriteLine("Дракон летить");
    }

    class Ogre : Enemy
    {
        public void Attack() => Console.WriteLine("Огр атакує");
    }
}
