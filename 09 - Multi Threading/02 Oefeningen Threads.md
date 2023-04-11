## Inleiding

Hier onder vind je afbeeldingen van demo's over verschillende onderwerpen van multi-threading. Dit is om het gevoel te krijgen voor de syntax en gebruiken.

Onder de demo's hebben we ook een een aantal oefening voor jullie.

## Demo 1

Dit gaat over de Thread class.

```java
public class MyThread extends Thread {
	private char c;
	private int count;

	public MyThread(char c, int count){
		this.c = c;
		this.count = count;
	}
	
	public void run() {
		for (int i = 0; i < count; i++) {
			System.out.println(c);
		}
	}
}
```

![](demo1Example.png)

<div style='page-break-after: always;'></div>

## Demo 2

Nu gaan we de interface Runnable implementeren.

![](demo2Example.png)

<div style='page-break-after: always;'></div>

## Demo 3

We gaan onze Threads omzetten naar lambda’s. Verander de code, en probeer eens te achterhalen wat ‘yield’ doet.

![](demo3Example.png)

## Demo 4

Daemon Threads, verander het volgende in je code, en kijk wat er gebeurt:

![](demo4Example.png)

Maak nu van beide Daemon Threads. Wat gebeurt er?

<div style='page-break-after: always;'></div>

## Demo 5

De slaaptoestand is soms ingewikkeld, probeer volgende code eens en kijk wat voor resultaat dat je krijgt:

![](demo5Example.png)

<div style='page-break-after: always;'></div>

## Oefening 1

Maak een applicatie die 10 seconden aftelt. Gebruik hiervoor Thread.sleep() en toon ook de huidige tijd aan met LocalDateTime.

## Oefening 2

Maak een klasse TimeBomb die je gaat gebruiken in onderstaande toepassing:

```java
public class VillainSpot {

    public static void main(String[] args) {

        Random random = new Random();
        TimeBomb timeBomb = new TimeBomb(10); // Bomb has 10 seconds!
        timeBomb.activate();

        try {
            Thread.sleep(random.nextInt(30000)); // It will take us between 0-30 secs to disarm the bomb.
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        timeBomb.disarm();

    }

}
```

Als je niet genoeg tijd hebt om de bom te ontmantelen, dan ontploft de bom. Anders, heb je die disarmed.

## Samenvatting

