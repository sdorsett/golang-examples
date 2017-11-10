# slices ( think Ruby arrays )

## slices.go
```
package main

import "fmt"

func main() {
    s1 := []int{1, 2, 3, 4}
    s1 = append(s1, 5)
    fmt.Println(s1)

    s2 := make([]int, 10)
    s2[0] = 1
    fmt.Println(s2)
}
```
## Output
```
63-158-0-142:slices standorsett$ go run slices.go
[1 2 3 4 5]
[1 0 0 0 0 0 0 0 0 0]
63-158-0-142:slices standorsett$
```
