# Interfaces
## interfaces.go
```
package main

import "fmt"

type BasePerson struct {
    First string
    Last string
}

type Employee struct {
    BasePerson
    Salary int
    Boss *Manager
}

type Manager struct {
    Employee
}

type Person interface {
    GetName() string
}

func SayHello(p Person) {
    fmt.Printf("Hello, %s\n", p.GetName())
}

func (e Employee) GetName() string {
    return e.First
}

func (m Manager) GetName() string {
    return m.First
}

func main() {

    m := &Manager{
        Employee{
            BasePerson: BasePerson{
                First: "Big",
                Last: "Boss",
            },
            Salary: 4000,
            Boss: nil,
        },
    }
    e := &Employee{
        BasePerson: BasePerson{
            First: "Small",
            Last: "Employee",
        },
        Salary: 3000,
        Boss: m,
    }

    people := []Person{Person(m), Person(e)}
    for _, person := range people {
        SayHello(person)
    }

}
```
## Output:
```
63-158-0-142:interfaces standorsett$ go run interfaces.go
Hello, Big
Hello, Small
63-158-0-142:interfaces standorsett$
```
