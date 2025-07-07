# ლექცია 

### ჩვენი პროგრამირების ენა “ქუბიტი”

<iframe width="560" height="315" src="https://youtu.be/5MtauKEgRiI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


### გამარჯობა, ლექციის მიმოხილვა

გამარჯობა მეგობრებო, ეს უკვე **მე-ექვსე** (6‼) ლექციაა. იმედი გვაქვს, წინა ხუთი უკვე ნახეთ.  
დღეს ძალიან საინტერესო გზას გავივლით — *შევქმნით ჩვენს საკუთარ პროგრამირების ენას!*


### რა არის საერთოდ „ენა“?

> **ფორმალური ენა** — სიმბოლოების სტრიქონების (სიტყვების) სიმრავლე,  
> რომლის ყველა სიმბოლო აღებულია ამ ენის **ანბანიდან**.

მაგალითი ანბანებისა:

```text
{a, b}          // ორი სიმბოლო
{0, 1}          // ბიტური
{x, =, +, ;}    // პროგრამული
```

ამ სიმბოლოებით ვაწყობთ სტრიქონებს (`aab`, `abba`, …),  
მაგრამ **გრამატიკის** გარეშე ისინი ჯერ კიდევ *უბრალო კომბინაციებია* — არა ენის „სიტყვები“.

### Context‑Free Grammar (CFG)

CFG პროგრამირების ენებისთვის საკმარისია. იგი მოიცავს:

1. **საწყის სიმბოლოს** (Start)  
2. **არა‑საბოლოო სიმბოლოებს** (Non‑terminal)  
3. **საბოლოო სიმბოლოებს** (Terminal)  
4. **წარმოების წესებს** (Productions)


### რომელი ფერი რომელ კომპონენტს შეესაბამება?

```{image} ./assets/HotDogRunsTree.png
:alt: demo
:width: 80%
:align: center
```

ჯერ შენით დაფიქრდი და შემდეგ ვიდეოში გადაამოწმე თუ სწორად გამოიცანი!

### „ქუბიტი“ — ენის შესაძლებლობები

1. არითმეტიკა: `5 + 3 * 2`  
2. ცვლადები: `sum = 5 + 2`  
3. ბეჭდვა: `print(sum)` ან `print(10)`

---

### გრამატიკა (სრული ვერსია)

```ebnf
<Program>        ::= <StatementList>
<StatementList>  ::= <Statement> | <StatementList> <Statement>

<Statement>      ::= <AssignStmt> | <PrintStmt>
<AssignStmt>     ::= <Identifier> "=" <Expression> ";"
<PrintStmt>      ::= "print" "(" <Expression> ")" ";"

<Expression>     ::= <Term>
                   | <Expression> "+" <Term>
                   | <Expression> "-" <Term>

<Term>           ::= <Factor>
                   | <Term> "*" <Factor>
                   | <Term> "/" <Factor>

<Factor>         ::= <Number>
                   | <Identifier>
                   | "(" <Expression> ")"

<Identifier>     ::= [A-Za-z][A-Za-z0-9]*
<Number>         ::= [0-9]+
```

და ქართულად გამოდის:

```{image} ./assets/QbitCFGGeorgian.png
:alt: demo
:width: 80%
:align: center
```

### **პრიორიტეტი**  
> ჯერ `*` / `/`, შემდეგ `+` / `-`.


#### მაგალითი — `2 + 3 * 4`


```{image} ./assets/MathOperationsPrioTree.png
:alt: demo
:width: 80%
:align: center
```

ფაზები (ქვემოდან ზემოთ):

1. 3 * 4 = 12  
2. 2 + 12 = **14**

---

### Compile‑time vs Run‑time

*სინტაქსი* — ენას სწორი სტრუქტურა;  
*სემანტიკაში* — რას ნიშნავს ეს სტრიქონი.

```qbit
a = 5 / 0;   // სინტაქსურად სწორია, მაგრამ 0‑ზე გაყოფა run‑time‑ზე აფეთქდება
```



### პატარა კომპილატორი და გამოგონილი პროცესორი

* 32 რეგისტრი — `R1 … R32`
* ბრძანებები: `LOAD`, `ADD`, `SUB`, `MUL`, `DIV`, `STORE`, `PRINT`, `HALT`

```qbit
subscribers = 775 + 225;
print(subscribers);
```

თარგმნა 👇

```cpu
LOAD R1 775
LOAD R2 225
ADD  R3 R1 R2
STORE subscribers R3
PRINT subscribers
HALT
```

### რეგისტრების ოპტიმიზაცია — `(2 + 3) * (4 + 5)`

**გულუბრყვილო (Naive)** — 7 რეგისტრი  
**ჭკვიანური** — 3 რეგისტრი

```cpu
; ოპტიმიზებული
LOAD R1 2
LOAD R2 3
ADD  R1 R1 R2        ; R1 = 5

LOAD R2 4
LOAD R3 5
ADD  R2 R2 R3        ; R2 = 9

MUL  R1 R1 R2        ; R1 = 45
```

---

### შეჯამება

ამ ლექციაში:

* ავაწყეთ ჩვენი **პროგრამირების ენა**
* გავაფორმეთ მისი **CFG**
* ვნახეთ, როგორ აკეთებს **კომპილატორი** წარმოების ხეს
* და როგორ ითარგმნება კოდი პროცესორის ინსტრუქციებად

**მადლობა ყურადღებისთვის!**  
მოიწონეთ, გამოიწერეთ და ნუ გამოტოვებთ შემდეგ ლექციას.  
დროებით! 🚀

გაითვალისწინეთ, ეს მხოლოდ მოკლე შეჯამებაა, სრული ვერსია ნახეთ ვიდეოში <3
