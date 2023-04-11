---
order: 200
icon: file
---
# Super class

## Wat is een superclass en een subclass

In Java is het mogelijk om variabele en methoden van de ene klasse naar de andere te erven (Inheritance). We groeperen het "inheritance concept" in twee categorieën:

sub-klas (sub-class) - de klas die erft van een andere klasse

super-klas (super-class) - de klas waarvan wordt geërfd

Het gebruik van keyword `extends` zorgt ervoor om van een klasse te kunnen erven. De klas die `extends` gebruikt erft dan de properties/ methodes van de super klas. Hieronder zie je een voorbeeld van een super en sub klas. `Car` (sub-class) extends `Vehicle` (super-class) klas.

**Belangrijk:**

- **Default superclass**: uitgezonderd Object class (deze klas heeft geen superclass). Heeft elke andere class een directe superclass(Single inheritance). Bij afwezigheid van een directe super class is de default superclass de Object class.
- **Only one superclass**: Er kan altijd maar 1 superclass zijn. Dit is omdat Java niet toestaat om met meerdere klassen te uitbreiden. Er is een uitzondering, alleen met interface (Dit komt later in het boek terug) is het mogelijk om meerder interfaces te implementeren. Dit is genoemd multiple inheritances.
- **Inheriting constructor**: Een subclass kan geen constructor erven dit omdat een constructor niet tot de members van een class behoort. Een subclass kan wel de super constructor aanroepen.
- **Private member inheritance**: Een sub-class kan geen private member erven. Alhoewel als de superclass methodes heeft die public of protected zijn(Getters en Setters) heeft de subclass toegang via die methodes naar de private fields.

<div style='page-break-after: always;'></div>

## properties super class

Hieronder zie je een voorbeeld van inheritance, we hebben Car class en die `extents` Vehicle class. De Car class (sub-class) kan gebruik maken van de fields van vehicle class (super-class).

*Super class*

```java
package be.intecbrussel;

public class Vehicle {

    // Vehicle class field
    private String typeOfVehicle = "Car";


    public String getTypeOfVehicle() {
        return typeOfVehicle;
    }

    public void setTypeOfVehicle(String typeOfVehicle) {
        this.typeOfVehicle = typeOfVehicle;
    }

}
```

*Sub class*

```java
package be.intecbrussel;

public class Car extends Vehicle {

    // Car class field
    private String brandName = "Audi";

    public String getBrandName() {
        return brandName;
    }

    public void setBrandName(String brandName) {
        this.brandName = brandName;
    }
}
```

<div style='page-break-after: always;'></div>

*Main App*

```java
package be.intecbrussel;

public class MainApp {

    public static void main(String[] args) {

        // Creëert myCar object
        Car myCar = new Car();

        // Drukt de waarde af van type of vehicle van Vehicle class en brandname van Car class.
        System.out.println("This vehicle is an: " + myCar.getTypeOfVehicle() + "\nThe brand is: " + myCar.getBrandName());
    }
}
```

## super methode aanroepen

Zoals je hier beneden ziet hebben beide klassen de methode honk(). Door de `super` keyword te gebruiken kunnen we onderscheid maken welke methode we willen aanroepen.

*Super class*

```java
package be.intecbrussel;

public class Vehicle {

    // Vehicle class field
    private String typeOfVehicle = "Car";

    public String getTypeOfVehicle() {
        return typeOfVehicle;
    }

    public void setTypeOfVehicle(String typeOfVehicle) {
        this.typeOfVehicle = typeOfVehicle;
    }

    // Vehicle class methode
    public void honk() {
        System.out.println("Toet toet!");
    }

}
```

*Sub class*

```java
package be.intecbrussel;

public class Car extends Vehicle {

    // Car class field
    private String brandName = "Audi";

    public String getBrandName() {
        return brandName;
    }

    public void setBrandName(String brandName) {
        this.brandName = brandName;
    }

    // Vehicle class methode
    public void honk() {

        System.out.println("Tuut tuut!");

    }

    public void sound() {

        // Roept de honk() method van Vehicle
        super.honk();

    }

}
```

<div style='page-break-after: always;'></div>

*Main App*

```java
package be.intecbrussel;

public class MainApp {

    public static void main(String[] args) {

        // Creëert myCar object
        Car myCar = new Car();

        // Drukt de waarde af van type of vehicle van Vehicle class en brandname van Car class.
        System.out.println("This vehicle is an: " + myCar.getTypeOfVehicle() + "\nThe brand is: " + myCar.getBrandName());

        // Roept sound() methode op van car class. Dit roept de methode honk() van Vehicle class.
        myCar.sound();

        // Hier word honk() methode van Car class opgeroepen.
        myCar.honk();

    }

}
```

## super constructor aanroepen

Als we een super constructor willen aanroepen gebeurd dit met `super()` belangrijk is dat deze op de eerste lijn van de sub-class constructor moet komen te staan. Zie voorbeeld hieronder:

*Super class*

```java
package be.intecbrussel;

public class Vehicle {

    public Vehicle() {

        System.out.println("Vehicle class constructor");

    }

}
```

<div style='page-break-after: always;'></div>

*Sub class*

```java
package be.intecbrussel;

public class Car extends Vehicle {

    public Car() {
        // Roept de super constructor aan
        super();

        // Eigen implementatie van de Car constructor
        System.out.println("Car class constructor");

    }

}
```

*Main App*

```java
package be.intecbrussel;

public class MainApp {

    public static void main(String[] args) {

        // Creëert myCar object
        Car myCar = new Car();

    }

}
```

## Constructor chaining

Constructor chaining kunnen we doen door 2 manieren:

- In dezelfde klas met keyword [This]().
- Van een super class door de `super()`.

Waarom gebruiken we constructor chaining?

Dit proces wordt gebruikt wanneer we meerdere taken in een enkele constructor willen uitvoeren in plaats van een code voor elke taak in een enkele constructor te maken. We creëren een afzonderlijke constructor voor elke taak en maken hun keten waardoor het programma leesbaarder wordt.

<div style='page-break-after: always;'></div>

**Extra:**

- We kunnen niet `this()` en `super()` in een constructor samen gebruiken. Dit komt omdat beide op de eerste lijn moeten staan.
- Er moet minimaal een constructor zijn zonder `this()`.

*Super class*

```java
package be.intecbrussel;

public class Vehicle {

    private String typeOfVehicle;

    // This will be executed second
    public Vehicle() {

        this("Car");
        System.out.println("Vehicle class no-args constructor");

    }

    // This will be executed first
    public Vehicle(String typeOfVehicle) {

        //this();
        this.typeOfVehicle = typeOfVehicle;
        System.out.println("Constructor Vehicle met parameters");

    }

}
```

<div style='page-break-after: always;'></div>

*Sub class*

```java
package be.intecbrussel;

public class Car extends Vehicle {

    /*
    *Dit zal niet worden uitgevoerd. Als we de this() uit comment halen en de ander in comment zetten in de
    * Vehicle class kun je het veerschil zien. Vergeet niet dat er altijd 1 constructor zonder een this() moet zijn.
    */
    public Car() {

        System.out.println("No args constructor Car");

    }

    // This will be executed third
    Car(String typeOfVehicle) {

        super(typeOfVehicle);
        System.out.println("Car constructor");

    }

}
```

*Main App*

```java
package be.intecbrussel;

public class MainApp {

    public static void main(String[] args) {

        // Creëert myCar object
        Car myCar = new Car();

    }

}
```
