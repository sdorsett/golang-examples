# working with writing to files
## write.go
```
package main

import (
	"fmt"
	"os"
)

func main() {
	f, err := os.Create("output.txt")
	if err != nil {
		panic("unable ot create file")
	}
	defer f.Close()
	cnt, err := f.WriteString("Hello, World!")
	if err != nil {
		panic("unable to write file")
	}
	fmt.Printf("Wrote %d bytes\n", cnt)

	
}
```
## Output:
```
Stans-MacBook-Pro:files standorsett$ go run write.go
Wrote 13 bytes
Stans-MacBook-Pro:files standorsett$ cat output.txt
Hello, World!Stans-MacBook-Pro:files standorsett$
```

