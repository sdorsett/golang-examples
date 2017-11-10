# the flag package makes passing command line options easy:
## flags.go
```
Stans-MacBook-Pro:cliflags standorsett$ cat flags.go
package main

import (
    "flag"
    "fmt"
    "os"
    "time"
)

var debug bool
var name string
var wait time.Duration

func main() {
    if name == "" {
        fmt.Println("must add name to use this tool!")
        flag.Usage()
        os.Exit(1)
    }
    if debug {
        fmt.Printf("Going to wait for %v\n", wait)
    }

    time.Sleep(wait)
    fmt.Printf("Hello, %s\n", name)
}

func init() {
    flag.BoolVar(&debug, "debug", false, "Turn on debug output")
    flag.StringVar(&name, "name", "", "The name to say hello to")
    defaultWait, err := time.ParseDuration("5s")
    if err != nil {
        panic("could not parse default wait time")
    }
    flag.DurationVar(&wait, "wait-time", defaultWait, "Time to wait before print")
    flag.Parse()
}
```
## Output:
```
Stans-MacBook-Pro:cliflags standorsett$ go build .
Stans-MacBook-Pro:cliflags standorsett$ ./cliflags
must add name to use this tool!
Usage of ./cliflags:
  -debug
        Turn on debug output
  -name string
        The name to say hello to
  -wait-time duration
        Time to wait before print (default 5s)
Stans-MacBook-Pro:cliflags standorsett$ ./cliflags -name Stan
Hello, Stan
Stans-MacBook-Pro:cliflags standorsett$ ./cliflags -name Stan -debug
Going to wait for 5s
Hello, Stan
Stans-MacBook-Pro:cliflags standorsett$ ./cliflags -name Stan -debug -wait-time 1s
Going to wait for 1s
Hello, Stan
Stans-MacBook-Pro:cliflags standorsett$
```
