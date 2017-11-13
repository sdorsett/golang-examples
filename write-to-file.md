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

## write2.go
```
package main

import (
	"fmt"
	"io/ioutil"
)

func main() {
	err := ioutil.WriteFile("output.txt", []byte("Hello, World!"), 0644)
	if err != nil {
		panic("unable to write file")
	} else {
		fmt.Println("file has been written")
	}
	buf, err := ioutil.ReadFile("output.txt")
	if err != nil {
		panic("unable to read file")
	}
	fmt.Println(string(buf))
}
```
## Output:
```
Stans-MacBook-Pro:files standorsett$ go run write2.go
file has been written
Hello, World!
Stans-MacBook-Pro:files standorsett$
```
