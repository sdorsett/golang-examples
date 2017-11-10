# golang tests alway end in _test.go:
```
Stans-MacBook-Pro:helloworld standorsett$ cat helloworld_test.go
package helloworld

import "testing"


func TestGetHelloWorld(t *testing.T) {
  retval := GetHelloWorld()
  if retval != "Hello, World!"{
    t.Fail()
  }
}
```
# golang test are run with the ‘go test’ command:
```
Stans-MacBook-Pro:helloworld standorsett$ go test
PASS
ok      github.com/sdorsett/helloworld    0.006s
```
# test coverage can be displayed by running 'go test -cover'
```
Stans-MacBook-Pro:helloworld standorsett$ go test -cover
PASS
coverage: 50.0% of statements
ok      github.com/sdorsett/helloworld    0.005s
```
# add more tests:
```
Stans-MacBook-Pro:helloworld standorsett$ cat helloworld_test.go
package helloworld

import (
  "testing"
  "golang.org/x/sys/unix"
)

func TestGetHelloWorld(t *testing.T) {
  retval := GetHelloWorld()
  if retval != "Hello, World!"{
    t.Fail()
  }
}

func TestGetUserID(t *testing.T) {
  retval := GetUserID()
  actual := unix.Getuid()
  if retval != actual {
    t.Fail()
  }
}

Stans-MacBook-Pro:helloworld standorsett$
```
# ...and test again:
```
Stans-MacBook-Pro:helloworld standorsett$ go test
PASS
ok      github.com/sdorsett/helloworld    0.005s

Stans-MacBook-Pro:helloworld standorsett$ go test -cover
PASS
coverage: 100.0% of statements
ok      github.com/sdorsett/helloworld    0.006s

Stans-MacBook-Pro:helloworld standorsett$
```
# intensive tests can be set to be skipped when running with the ‘-short’ flag:
```
Stans-MacBook-Pro:helloworld standorsett$ go test -short
PASS
ok      github.com/sdorsett/helloworld    0.006s
Stans-MacBook-Pro:helloworld standorsett$ go test -short -cover
PASS
coverage: 40.0% of statements
ok      github.com/sdorsett/helloworld    0.005s
Stans-MacBook-Pro:helloworld standorsett$

Stans-MacBook-Pro:helloworld standorsett$ cat helloworld.go
package helloworld

import "golang.org/x/sys/unix"

//GetHelloWorld will get the hello world string
func GetHelloWorld() string {
    return "Hello, World!"
}

//GetUserID get the ID for the current user
func GetUserID() int {
    return unix.Getuid()
}

func GetAbsValue(i int) int{
  if i > 0 {
    return i
  }
  return -1 * i
}

Stans-MacBook-Pro:helloworld standorsett$ cat helloworld_test.go
package helloworld

import (
  "testing"
  "golang.org/x/sys/unix"
)

func TestGetHelloWorld(t *testing.T) {
  retval := GetHelloWorld()
  if retval != "Hello, World!"{
    t.Fail()
  }
}

func TestGetUserID(t *testing.T) {
  retval := GetUserID()
  actual := unix.Getuid()
  if retval != actual {
    t.Fail()
  }
}

func TestGetAbsValue(t *testing.T) {
  if testing.Short() {
    t.Skip()
  }
  retval := GetAbsValue(-5)
  if retval != 5 {
    t.Fail()
  }
  retval = GetAbsValue(10)
  if retval != 10 {
    t.Fail()
  }
}
```
