# GOPATH and GOROOT need to be set for ‘go install’ to properly work
```
Stans-MacBook-Pro:helloworld standorsett$ echo $GOPATH
/Users/standorsett/go
Stans-MacBook-Pro:helloworld standorsett$ echo $GOROOT
/usr/local/go
```
# the typical path for packages to be installed is under $GOPATH/src
# create the directory structure
```
Stans-MacBook-Pro:helloworld standorsett$ mkdir -p $GOPATH/src/github.com/sdorsett/helloworld
Stans-MacBook-Pro:helloworld standorsett$ cd $GOPATH/src/github.com/sdorsett/helloworld
Stans-MacBook-Pro:helloworld standorsett$ pwd
/Users/standorsett/go/src/github.com/sdorsett/helloworld
```
# create a ‘helloworld’ package in the root of the helloworld directory
```
Stans-MacBook-Pro:helloworld standorsett$ cat helloworld.go
package helloworld

func GetHelloWorld() string {
    return "Hello, World!"
}
```
# create a directory under cmd for the main function:
```
Stans-MacBook-Pro:helloworld standorsett$ mkdir -p cmd/hello
Stans-MacBook-Pro:helloworld standorsett$ cd cmd/hello/
Stans-MacBook-Pro:helloworld standorsett$ cat cmd/hello/main.go
package main

import (
  "fmt"
  "github.com/sdorsett/helloworld"
)

func main() {
    fmt.Println(helloworld.GetHelloWorld())
}
```
# return to the root folder and perform a go install:
```
Stans-MacBook-Pro:helloworld standorsett$ cd $GOPATH/src/github.com/sdorsett/helloworld
Stans-MacBook-Pro:helloworld standorsett$ pwd
/Users/standorsett/go/src/github.com/sdorsett/helloworld
Stans-MacBook-Pro:helloworld standorsett$ tree
.
├── cmd
│   └── hello
│       └── main.go
└── helloworld.go

2 directories, 2 files

Stans-MacBook-Pro:helloworld standorsett$ go install ./...
Stans-MacBook-Pro:helloworld standorsett$ which hello
/Users/standorsett/go/bin/hello
Stans-MacBook-Pro:helloworld standorsett$ hello
Hello, World!
Stans-MacBook-Pro:helloworld standorsett$
```
