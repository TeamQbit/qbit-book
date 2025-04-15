# პასუხები

## 2.1 ჩაიბარე ამანათი

ერთ-ერთი შესაძლო მარშრუტი:

```python
def main(): 
    # გასვლა
    move()
    move()
    turn_right()
    move()
    turn_left()
    move()
    
    # აღება და მობრუნება
    pick()
    turn_around()
    
    # დაბრუნება პოზიციაზე
    move()
    move()
    move()
    turn_right()
    move()
    turn_right()
    
def turn_right():
    turn_left()
    turn_left()
    turn_left()
    
def turn_around():
    turn_left()
    turn_left()
```


## 2.2 ააშენე სკოლები

```python
def main(): 
    # ჩაიაროს რუკა და შემხვედრ აგურზე დააშენოს 2x3 ზომის სკოლა
    while front_is_clear():
        if bricks_present():
            build_school()
        move()

# ალგორითმი სკოლის ასაშნებელად
def build_school():
    # მარცხენა ნაწილი
    turn_left()
    move()
    put()
    move()
    put()
    
    # მარჯვენა ნაწილი
    turn_right()
    move()
    put()
    turn_right()
    move()
    put()
    move()
    put()
    turn_left()
    
    
def turn_right():
    turn_left()
    turn_left()
    turn_left()
```

## 2.3 ხიდის შეკეთება

```python
def main():
    for i in range(3):
        fix_column()
        move_to_next_column()

    # Fence-post პრობლემა
    fix_column()    

def fix_column():
    turn_left()
    
    # აყვეს სვეტს ბოლომდე და დაალაგოს გამოტოვებული აგურები
    while front_is_clear():
        if no_bricks_present():
            put()
        move()
    # Fence-post პრობლემა
    if no_bricks_present():
        put()
    
    # მობრუნება და ქვემოთ დაბრუნება
    turn_around()
    while front_is_clear():
        move()
    turn_left()

def move_to_next_column():
    for i in range(4):
        move()

def turn_around():
    turn_left()
    turn_left()
```

## 2.4 არჩევნები

```python
def main(): 
    # ჩაიაროს დერეფანი და აკრიფოს მოპირდაპირე ყუთებიდან
    while front_is_clear():
        collect_sides()
        move()
    # Fence-post პრობლემა
    collect_sides()
    
    # დააწყოს შეგროვილი ბიულეტინები
    put_all()
    
    # დაბრუნდეს უკან
    return_back()
    
def return_back():
    turn_around()
    while front_is_clear():
        move()
    turn_around()
    
def put_all():
    while bricks_in_bag():
        put()
    
def collect_sides():
    # ზედა ყუთის აგროვება
    turn_left()
    move()
    collect_box()
    turn_around()
    move()
    
    # ქვედა ყუთის აგროვება
    move()
    collect_box()
    
    # დაბრუნება პოზიციაში
    turn_around()
    move()
    turn_right()
    
    
def collect_box():
    while bricks_present():
        pick()
        
def turn_around():
    turn_left()
    turn_left()
    
def turn_right():
    turn_left()
    turn_left()
    turn_left()
```

## 2.5 გააორმაგე აგურები

```python
def main():
    move()
    
    # თითო აგურზე დებს ორ აგურს მარჯვნივ, ასე თვლის გარეშე შევძლებთ გაორმაგებას
    while bricks_present():
        # აიღე ერთი
        pick()
        
        # წადი და დადე ორი ცალი თითო აღებულზე
        move()
        put()
        put()
        
        # დაბრუნდი უკან ციკლის დასატრიალებლად
        turn_around()
        move()
        turn_around()
    
    # საწყის პოზიციაზე დაბრუნება
    turn_around()
    move()
    turn_around()
        
def turn_around():
    turn_left()
    turn_left()
```