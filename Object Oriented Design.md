### Object Oriented Design:

### 1. Explain the concept of encapsulation in object-oriented programming.

**Answer:** Encapsulation is one of the fundamental principles in object-oriented programming (OOP) that involves bundling data (attributes) and methods (functions) that operate on the data into a single unit called a class. Encapsulation restricts access to some of an object's components and prevents the accidental modification of data. It promotes information hiding and allows the object to control its internal state. Access to the data is typically achieved through getter and setter methods, providing a way to interact with the object's state in a controlled manner.

### 2. Discuss the advantages of inheritance and composition in object-oriented design.

**Answer:** Inheritance and composition are two key concepts in object-oriented design that offer different approaches to building relationships between classes.

- **Inheritance:**
  - **Advantages:**
    - Code Reusability: Inherited classes can reuse the code of their parent class.
    - Polymorphism: Enables the creation of a common interface for different subclasses.
    - Logical Organization: Models an "is-a" relationship, expressing a natural hierarchy.

- **Composition:**
  - **Advantages:**
    - Flexibility: Allows for dynamic behavior changes at runtime by changing the composition of objects.
    - Better Code Structure: Emphasizes "has-a" relationships, leading to more modular and maintainable code.
    - Avoids the Diamond Problem: Unlike multiple inheritance, composition avoids ambiguities and complexities.

### 3. Implement a simple class hierarchy for a zoo simulation.

**Answer:**

```python
class Animal:
    def __init__(self, name, species):
        self.name = name
        self.species = species

    def make_sound(self):
        pass

class Lion(Animal):
    def make_sound(self):
        return "Roar!"

class Elephant(Animal):
    def make_sound(self):
        return "Trumpet!"

# Usage:
lion = Lion("Simba", "African Lion")
elephant = Elephant("Dumbo", "African Elephant")

print(lion.make_sound())      # Output: Roar!
print(elephant.make_sound())  # Output: Trumpet!
```

### 4. How would you design a system for handling different shapes and their areas?

**Answer:**

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def calculate_area(self):
        pass

class Rectangle(Shape):
    def __init__(self, length, width):
        self.length = length
        self.width = width

    def calculate_area(self):
        return self.length * self.width

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def calculate_area(self):
        return 3.14 * self.radius * self.radius

# Usage:
rectangle = Rectangle(5, 10)
circle = Circle(7)

print(rectangle.calculate_area())  # Output: 50
print(circle.calculate_area())      # Output: 153.86
```

### 5. Discuss the importance of interfaces in Java or C#.

**Answer:** Interfaces in Java or C# define a contract that classes must adhere to, specifying a set of methods that they must implement. This promotes code consistency, modularity, and multiple inheritances of behavior. Key points:

- **Enforcing Contracts:** Interfaces define a clear set of methods that implementing classes must provide, ensuring consistency across various classes.
  
- **Multiple Inheritance:** Unlike classes, which cannot inherit from multiple classes in Java or C#, a class can implement multiple interfaces, facilitating a form of multiple inheritance.

- **Polymorphism:** Interfaces support polymorphism, allowing objects of different classes to be treated interchangeably if they implement the same interface.

### 6. Design a parking lot system using object-oriented principles.

**Answer:**

```python
class ParkingLot:
    def __init__(self, capacity):
        self.capacity = capacity
        self.available_spots = capacity
        self.parking_spots = {}

    def park_vehicle(self, vehicle):
        if self.available_spots > 0:
            spot_id = self._find_available_spot()
            self.parking_spots[spot_id] = vehicle
            self.available_spots -= 1
            return spot_id
        else:
            return None

    def remove_vehicle(self, spot_id):
        if spot_id in self.parking_spots:
            del self.parking_spots[spot_id]
            self.available_spots += 1
            return True
        else:
            return False

    def _find_available_spot(self):
        for spot_id in range(1, self.capacity + 1):
            if spot_id not in self.parking_spots:
                return spot_id

class Vehicle:
    def __init__(self, license_plate, vehicle_type):
        self.license_plate = license_plate
        self.vehicle_type = vehicle_type

# Usage:
parking_lot = ParkingLot(10)
car = Vehicle("ABC123", "Car")
spot_id = parking_lot.park_vehicle(car)

if spot_id:
    print(f"Vehicle parked at spot {spot_id}")
else:
    print("Parking lot full")

# Remove vehicle
removed = parking_lot.remove_vehicle(spot_id)
print(f"Vehicle removed: {removed}")
```

### 7. Explain the concept of abstract classes and when to use them.

**Answer:** Abstract classes in Java or C# are classes that cannot be instantiated and may contain abstract methods (methods without a body) that must be implemented by concrete (non-abstract) subclasses. Use abstract classes when:

- **Partial Implementation:** You want to provide a base class with some common functionality but leave certain methods to be implemented by subclasses.

- **Code Reusability:** You want to share code among related classes while enforcing a certain structure.

- **Enforcing Rules:** You want to define a contract that subclasses must adhere to by providing implementations for certain methods.

Example:

```java
abstract class Shape {
    int x, y;

    abstract void draw(); // Abstract method

    void moveTo(int newX, int newY) {
        this.x = newX;
        this.y = newY;
    }
}

class Circle extends Shape {
    int radius;

    Circle(int x, int y, int radius) {
        this.x = x;
        this.y = y;
        this.radius = radius;
    }

    void draw() {
        // Implementation for drawing a circle
        System.out.println("Drawing a circle");
    }
}
```

### 8. Implement a simple observer pattern in Java or C#.

**Answer:**

```java
import java.util.ArrayList;
import java.util.List;

// Subject (Observable)
class Subject {
    private List<Observer> observers = new ArrayList<>();

    void addObserver(Observer observer) {
        observers.add(observer);
    }

    void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    void notifyObservers(String message) {
        for (Observer observer : observers) {
            observer.update(message);
        }
    }
}

// Observer
interface Observer {
    void update(String message);
}

// Concrete Observer
class ConcreteObserver implements Observer {
    private String name;

    ConcreteObserver(String name) {
        this.name = name;
    }

    public void update(String message) {
        System.out.println(name + " received message: " + message);
   

 }
}

// Usage:
public class ObserverPatternExample {
    public static void main(String[] args) {
        Subject subject = new Subject();

        ConcreteObserver observer1 = new ConcreteObserver("Observer 1");
        ConcreteObserver observer2 = new ConcreteObserver("Observer 2");

        subject.addObserver(observer1);
        subject.addObserver(observer2);

        subject.notifyObservers("Hello Observers!");
    }
}
```

### 9. Design a class to represent a deck of playing cards.

**Answer:**

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

enum Suit {
    HEARTS,
    DIAMONDS,
    CLUBS,
    SPADES
}

enum Rank {
    ACE, TWO, THREE, FOUR, FIVE, SIX, SEVEN, EIGHT, NINE, TEN, JACK, QUEEN, KING
}

class Card {
    private final Suit suit;
    private final Rank rank;

    Card(Suit suit, Rank rank) {
        this.suit = suit;
        this.rank = rank;
    }

    @Override
    public String toString() {
        return rank + " of " + suit;
    }
}

class Deck {
    private List<Card> cards = new ArrayList<>();

    Deck() {
        initializeDeck();
        shuffle();
    }

    private void initializeDeck() {
        for (Suit suit : Suit.values()) {
            for (Rank rank : Rank.values()) {
                cards.add(new Card(suit, rank));
            }
        }
    }

    void shuffle() {
        Collections.shuffle(cards);
    }

    Card drawCard() {
        if (!cards.isEmpty()) {
            return cards.remove(0);
        } else {
            System.out.println("Deck is empty.");
            return null;
        }
    }
}

// Usage:
public class DeckOfCardsExample {
    public static void main(String[] args) {
        Deck deck = new Deck();

        // Draw and print the first five cards
        for (int i = 0; i < 5; i++) {
            Card card = deck.drawCard();
            if (card != null) {
                System.out.println(card);
            }
        }
    }
}
```

### 10. Discuss the principles of loose coupling and high cohesion in object-oriented design.

**Answer:**

- **Loose Coupling:**
  - **Definition:** Loose coupling refers to the degree of independence between components or modules in a system. It is a measure of how much one module knows about the internal workings or implementation details of another module.
  - **Advantages:**
    - Easy Maintenance: Changes in one module don't affect other modules significantly.
    - Reusability: Components can be reused in different contexts without modification.
    - Testability: Modules can be tested independently, leading to better unit testing.

- **High Cohesion:**
  - **Definition:** High cohesion means that the elements within a module or class are strongly related to each other and have a shared responsibility. It emphasizes that a class should have a single, well-defined purpose.
  - **Advantages:**
    - Improved Readability: Code is easier to understand and reason about.
    - Easier Maintenance: Changes are localized to specific modules, reducing unintended consequences.
    - Encapsulation: Encourages encapsulation of related functionality within classes.

**Example:**
```java
// Loose Coupling Example
class Logger {
    void log(String message) {
        System.out.println("Logging: " + message);
    }
}

class UserManager {
    private Logger logger;

    UserManager(Logger logger) {
        this.logger = logger;
    }

    void createUser(String username) {
        // User creation logic
        logger.log("User created: " + username);
    }
}
```

In the example, `UserManager` is loosely coupled with the `Logger` class because it depends on an abstraction (`Logger`), and different logger implementations can be easily swapped without affecting the `UserManager` class.