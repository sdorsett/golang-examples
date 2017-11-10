# maps ( think Ruby hashes )
## maps.go
```
package main

import "fmt"

func main() {
    m1 := map[string]string{}
    m1["first"] = "John"
    m1["last"] = "Lenon"
    fmt.Println(m1)

    m2 := map[string]string{
        "first": "Paul",
        "last": "McCartney",
    }
    fmt.Println(m2)

    m3 := make(map[string]string)
    m3["first"] = "Ringo"
    m3["last"] = "Star"
    fmt.Println(m3["first"])

}
```
## Output:
```
63-158-0-142:maps standorsett$ go run maps.go
map[first:John last:Lenon]
map[first:Paul last:McCartney]
Ringo
63-158-0-142:maps standorsett$
```
