# creating and assigning values to a struct 'on the fly'
```
package main

import "fmt"
import "github.com/davecgh/go-spew/spew"

func main() {

    pt := struct {
        X int
        Y int
    }{
        X: 10,
        Y: 20,
    }
    fmt.Println(pt)
    spew.Dump(pt)
}
```
# output
```
63-158-0-142:go-learning standorsett$ go run structs.go
{10 20}
(struct { X int; Y int }) {
 X: (int) 10,
 Y: (int) 20
}
63-158-0-142:go-learning standorsett$
```
