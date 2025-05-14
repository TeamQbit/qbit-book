# გამოყენებული კოდი

### კლასი
```java
void main(){
	House myHouse = new House("qbit 1", 3, true);
	House myFriendsHouse = new House("qbit 23", 2, false);
	myHouse.openGarage();
	myFriendsHouse.openGarage();
}

class House {
	String address;
	int numOfRooms;
	boolean hasGarage;

	House(String address, int numOfRooms, boolean hasGarage){
		this.address = address;
		this.numOfRooms = numOfRooms;
		this.hasGarage = hasGarage;
	}

	void openGarage() {
		if(hasGarage){
			System.out.println("opening garage!")
		}else {
			System.out.println("no garage door to open!")
		}
	}

	void closeGarage() {
		if(hasGarage){
			System.out.println("closed garage door!")
		}else {
			System.out.println("no garage door to close!")
		}
	}
}
```

### String ტიპის ცვლადები
```java
void main(){
	String name1 = "Java";
	String name2 = "Java";

	String name3 = new String("Java");
}
```

### String კლასის მეთოდები
```java
void main(){
	String message = "Qbit";
	System.out.println(message.length());
	System.out.println(message.toUpperCase());
	System.out.println(message.toLowerCase());
	System.out.println(message.charAt(0));
	System.out.println(message.substring(1, 3));
}
```

## OOP
### მემკვიდრეობითობა
```java
public class Main {
	public static void main(String[] args){
		House myHouse = new House();
		School mySchool = new School();
		myHouse.numOfFloors = 12;
		myHouse.address = "qbit 1";
		myHouse.hasGarden = true;
		
		mySchool.numOfFloors = 9;
		mySchool.address = "school 1";
		mySchool.numOfStudents = 300;
		
		System.out.println(myHouse.numOfFloors);
		System.out.println(myHouse.address);
		System.out.println(myHouse.hasGarden);
		
		System.out.println(mySchool.numOfFloors);
		System.out.println(mySchool.address);
		System.out.println(mySchool.numOfStudents);
	}

}

class Building {
	int numOfFloors;
	String address;
}

class House extends Building{
	boolean hasGarden;

	void ringDoorBell() {
		System.out.println("ding ding it's a house!");
	}
}

class School extends Building{
	int numOfStudents;
	
	void startSchool() {
		System.out.println("school has started!");
	}

}
```

### ენკაფსულაცია
```java
public class Main {
	public static void main(String[] args){
		House myHouse = new House();
		School mySchool = new School();
		myHouse.setFloorCount(12);
		myHouse.setFloorCount(-1);
		myHouse.address = "qbit 1";
		myHouse.hasGarden = true;

		System.out.println(myHouse.getNumOfFloors());
		mySchool.setFloorCount(9);
		mySchool.address = "school 1";
		mySchool.numOfStudents = 300;
		
		System.out.println(myHouse.getNumOfFloors());
		System.out.println(myHouse.address);
		System.out.println(myHouse.hasGarden);
		
		System.out.println(mySchool.getNumOfFloors());
		System.out.println(mySchool.address);
		System.out.println(mySchool.numOfStudents);
	}

}

class Building {
	private int numOfFloors;
	String address;

	void setFloorCount(int numOfFloors){
		if(numOfFloors <= 0){
			System.out.println("House needs to have at least one floor!");
		}else {
			this.numOfFloors = numOfFloors;
		}
	}

	int getNumOfFloors(){
		return numOfFloors;
	}
}

class House extends Building{
	boolean hasGarden;

	void ringDoorBell() {
		System.out.println("ding ding it's a house!");
	}
}

class School extends Building{
	int numOfStudents;
	
	void startSchool() {
		System.out.println("school has started!");
	}
}
```

### პოლიმორფიზმი
#### მეთოდის გადაფარვა Override
```java
public class Main {
	public static void main(String[] args){
		House myHouse = new House();
		School mySchool = new School();
		myHouse.warningAlarm();
		mySchool.warningAlarm();
	}

}

class Building {
	private int numOfFloors;
	String address;

	void setFloorCount(int numOfFloors){
		if(numOfFloors <= 0){
			System.out.println("House needs to have at least one floor!");
		}else {
			this.numOfFloors = numOfFloors;
		}
	}

	int getNumOfFloors(){
		return numOfFloors;
	}

	void warningAlarm(){
		System.out.println("WARNING!");
	}
}

class House extends Building{
	boolean hasGarden;

	void ringDoorBell() {
		System.out.println("ding ding it's a house!");
	}

	@Override
	void warningAlarm(){
		System.out.println("please don't use elevator!");
	}
}

class School extends Building{
	int numOfStudents;
	
	void startSchool() {
		System.out.println("school has started!");
	}

	@Override
	void warningAlarm(){
		System.out.println("students please stay seated!");
	}
}
```

#### მეთოდის გადატვირთვა Overload
```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

### აბსტრაქცია
#### აბსტრაქტული კლასები, მეთოდები
```java
public class Main {
	public static void main(String[] args){
		
	}
}

abstract class CoffeeMachine{
	abstract void makeEsspresso();
	abstract void makeLatte();
}

class FancyCoffeeMachine extends CoffeeMachine{

	@Override
	void makeEsspresso(){
		System.out.println("brewing water");
		System.out.println("making esspresso");
	}

	@Override
	void makeLatte(){
		System.out.println("brewing milk");
		System.out.println("latte done!");
	}
	
}
```

#### interface
```java
public class Main {
	public static void main(String[] args){
		
	}
}

interface Printable {
	void print();
}

interface Drawable {
    void draw();
}

class Document implements Printable, Drawable {
    @Override
    public void draw() {
        System.out.println("Drawing document");
    }

    @Override
    public void print() {
        System.out.println("Printing document");
    }
}
```

### static საკვანძო სიტყვა
```java
public class Main {
	public static void main(String[] args){
		MyClass.sayHello();
	}
}

class MyClass {
	static void sayHello(){
		System.out.println("Hello from MyClass");
	}
}
```
