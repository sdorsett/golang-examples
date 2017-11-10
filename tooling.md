# golint - used to check go code against the style guide
```
Stans-MacBook-Pro:helloworld standorsett$ pwd
/Users/standorsett/go/src/github.com/sdorsett/helloworld

Stans-MacBook-Pro:helloworld standorsett$ go get -u github.com/golang/lint

Stans-MacBook-Pro:helloworld standorsett$ which golint
/Users/standorsett/go/bin/golint

Stans-MacBook-Pro:helloworld standorsett$ golint .
helloworld.go:3:1: exported function GetHelloWorld should have comment or be unexported

Stans-MacBook-Pro:helloworld standorsett$ vi helloworld.go
Stans-MacBook-Pro:helloworld standorsett$ cat helloworld.go
package helloworld

//GetHelloWorld will get the hello world string
func GetHelloWorld() string {
    return "Hello, World!"
}

Stans-MacBook-Pro:helloworld standorsett$ golint .

Stans-MacBook-Pro:helloworld standorsett$
```
# gofmt - used to ensure go code is properly formatted
```
Stans-MacBook-Pro:helloworld standorsett$ gofmt -l -d .
cmd/hello/main.go
diff cmd/hello/main.go gofmt/cmd/hello/main.go
--- /var/folders/zd/t14lgzhd511470drq7nssrx80000gn/T/gofmt217574365    2017-11-10 14:03:16.000000000 -0600
+++ /var/folders/zd/t14lgzhd511470drq7nssrx80000gn/T/gofmt254974360    2017-11-10 14:03:16.000000000 -0600
@@ -1,8 +1,8 @@
 package main

 import (
-  "fmt"
-  "github.com/sdorsett/helloworld"
+    "fmt"
+    "github.com/sdorsett/helloworld"
 )

 func main() {
helloworld.go
diff helloworld.go gofmt/helloworld.go
--- /var/folders/zd/t14lgzhd511470drq7nssrx80000gn/T/gofmt765196823    2017-11-10 14:03:16.000000000 -0600
+++ /var/folders/zd/t14lgzhd511470drq7nssrx80000gn/T/gofmt732744842    2017-11-10 14:03:16.000000000 -0600
@@ -2,6 +2,5 @@

 //GetHelloWorld will get the hello world string
 func GetHelloWorld() string {
-    return "Hello, World!"
+    return "Hello, World!"
 }
-

Stans-MacBook-Pro:helloworld standorsett$ go fmt
helloworld.go

Stans-MacBook-Pro:helloworld standorsett$ go fmt cmd/hello/main.go
cmd/hello/main.go

Stans-MacBook-Pro:helloworld standorsett$ gofmt -l -d .
Stans-MacBook-Pro:helloworld standorsett$
```
# godoc - user to print documentation from go code
```
Stans-MacBook-Pro:helloworld standorsett$ godoc github.com/sdorsett/helloworld
use 'godoc cmd/github.com/sdorsett/helloworld' for documentation on the github.com/sdorsett/helloworld command

PACKAGE DOCUMENTATION

package helloworld
    import "github.com/sdorsett/helloworld"


FUNCTIONS

func GetHelloWorld() string
    GetHelloWorld will get the hello world string

SUBDIRECTORIES

    cmd

Stans-MacBook-Pro:helloworld standorsett$
```
