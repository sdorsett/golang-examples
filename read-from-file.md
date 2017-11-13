# reading from files
## maps.go
```
package main

import (
	"fmt"
	"os"
)

func main() {
	f, err := os.Open("output.txt")
	if err != nil {
		panic("unable ot create file")
	}
	defer f.Close()
	buf := make([]byte, 64)
	cnt, err := f.Read(buf)
	if err != nil {
		panic("unable to read file")
	}
	fmt.Printf("Read %d bytes\n", cnt)
	fmt.Println(string(buf[:cnt]))

}
```
## Output:
```
Stans-MacBook-Pro:files standorsett$ go run read.go
Read 13 bytes
Hello, World!
Stans-MacBook-Pro:files standorsett$
```
