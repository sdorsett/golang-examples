# logging with golang
## logging.go
```
package main

import "log"
import "flag"
import "os"
import "fmt"

var name string

func main() {
	prefix := fmt.Sprintf("%s: ", os.Args[0])
	info, err := os.Create("info.log")
	if err != nil {
		log.Fatalln("Failed to create log file")
	}
	infoLog := log.New(info, prefix, log.LstdFlags)
	errorLog := log.New(os.Stderr, prefix, log.LstdFlags)
	if name == "" {
		errorLog.Println("No name supplied!")
		flag.Usage()
		os.Exit(1)
	}
	infoLog.Println("Program started!")
	infoLog.Printf("Hello, %s\n", name)
	infoLog.Println("Program finished!")

}

func init() {
	flag.StringVar(&name, "name", "", "The name to say hello to")
	flag.Parse()
}
```
## Output:
```
Stans-MacBook-Pro:logging standorsett$ go build logging.go
Stans-MacBook-Pro:logging standorsett$ ./logging -name Stan
Stans-MacBook-Pro:logging standorsett$ cat info.log
./logging: 2017/11/13 14:42:23 Program started!
./logging: 2017/11/13 14:42:23 Hello, Stan
./logging: 2017/11/13 14:42:23 Program finished!
Stans-MacBook-Pro:logging standorsett$ ./logging
./logging: 2017/11/13 14:42:37 No name supplied!
Usage of ./logging:
  -name string
        The name to say hello to
Stans-MacBook-Pro:logging standorsett$
```
