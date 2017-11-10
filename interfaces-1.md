# Interfaces
## interfaces.go
```
package main

import "fmt"

func main() {

    var x interface{}
    x = "Hello, World 1"
    fmt.Println(x)

    var y interface{}
    y = "Hello, World 2"
    str, ok := y.(int)
    if !ok {
        fmt.Printf("%v is not an int\n", y)
    }
    fmt.Println(str)

    var z interface{}
    z = 200
    switch z.(type) {
    case string:
        fmt.Printf("%s is a string\n", z)
    case int:
        fmt.Printf("%d is an int\n", z)
    }

    var zz interface{}
    zz = "learning go"
    switch zz.(type) {
    case string:
        fmt.Printf("%s is a string\n", zz)
    case int:
        fmt.Printf("%d is an int\n", zz)
    }

}
```
## Output:
```
63-158-0-142:interfaces standorsett$ go run interfaces.go
Hello, World 1
Hello, World 2 is not an int
0
200 is an int
learning go is a string
63-158-0-142:interfaces standorsett$
```
