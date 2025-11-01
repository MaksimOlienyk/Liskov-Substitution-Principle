# Enemy System — Приклад SOLID (Liskov Substitution Principle)

Цей приклад демонструє **принцип підстановки Барбари Лісков (LSP)** із SOLID у мові C#.

## Суть принципу LSP

> **Об'єкти підкласів повинні бути взаємозамінними з об'єктами базового класу, не порушуючи логіку програми.**

- Якщо ми використовуємо тип `Enemy`,
- То будь-який його нащадок (`Dragon`, `Ogre`, тощо) повинен **поводитись узгоджено**.
- Програма не повинна «ламатися» при заміні одного нащадка іншим.

---

## Структура

| Тип | Опис |
|----|------|
| `Enemy` | Базовий інтерфейс ворога, має метод `Attack()` |
| `FlyingEnemy` | Розширює `Enemy`, додає можливість `Fly()` |
| `Dragon` | Літаючий ворог (може `Attack()` і `Fly()`) |
| `Ogre` | Наземний ворог (може лише `Attack()`) |

---

## Код:

```csharp
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

## Приклад використання:
Enemy dragon = new Dragon();
dragon.Attack();

Enemy ogre = new Ogre();
ogre.Attack();
