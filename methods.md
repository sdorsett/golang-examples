# Methods
## methods.go
```
package main

import (
    "fmt"
    "time"
)

type Person struct {
    First string
    Last string
    Dob time.Time
}

func (p Person) SayHello() {
    fmt.Printf("Hello, %s\n", p.First)
}

func sayHello(name string) {
    fmt.Printf("Hello, %s\n", name)

}

func getHello(name string) string {
    return fmt.Sprintf("Hello, %s\n", name)
}

func NewPerson(first, last string, year, month, day int) *Person {
    return &Person{
        First: first,
        Last: last,
        Dob: time.Date(year, time.Month(month), day, 0, 0, 0, 0, time.Local),
    }
}

func (p Person) GetAge() int {
    d := time.Since(p.Dob)
    return int(d.Hours() / 24 / 365)
}

func main() {
    sayHello("John")
    e := getHello("Paul")
    fmt.Print(e)

    p1 := &Person{
        First: "Ringo",
        Last: "Star",
    }
    p1.SayHello()

    p2 := NewPerson("George", "Harrison", 1943, 2, 25)
    fmt.Printf("%s is %d years old\n", p2.First, p2.GetAge())
}
```
## Output:
```
63-158-0-142:methods standorsett$ go run methods.go
Hello, John
Hello, Paul
Hello, Ringo
George is 74 years old
63-158-0-142:methods standorsett$
```

