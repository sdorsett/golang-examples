## pointers.go
```
package main

import "fmt"

func main() {

    s := "My String"
    var sptr *string
    sptr = &s
    fmt.Println(sptr)
    fmt.Println(*sptr)
}
```

## Output
```
63-158-0-142:pointers standorsett$ go run pointers.go
0xc42000e260
My String
63-158-0-142:pointers standorsett$
```
