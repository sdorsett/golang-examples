# using viper
## with-viper.go
```
package main

import (
	"flag"
	"fmt"
	"log"

	"github.com/spf13/viper"
)

var username, password string

func useCredentials() {
	fmt.Printf("Your username is %s\n", viper.GetString("credentials.username"))
	fmt.Printf("Your password is %s\n", viper.GetString("credentials.password"))
}

func main() {
	flag.StringVar(&username, "user", "", "username to user")
	flag.StringVar(&password, "pass", "", "password to user")
	flag.Parse()
	viper.AddConfigPath(".")
	viper.SetConfigName("creds")
	viper.ReadInConfig()
	if err := viper.ReadInConfig(); err != nil {
		log.Fatalln("unable to read config")
	}
	if username != "" {
		viper.Set("credentials.username", username)
	}
	if password != "" {
		viper.Set("credentials.username", password)
	}
	if !viper.IsSet("credentials.username") || !viper.IsSet("credentials.password") {
		log.Fatalln("no credentials")
	}

	useCredentials()
}

```
## Output:
```
Stans-MacBook-Pro:viper standorsett$ go run with-viper.go
ringoYour username is ringo
Your password is passw0rd
Stans-MacBook-Pro:viper standorsett$ go run with-viper.go -user john -pass di@mond
Your username is di@mond
Your password is passw0rd
Stans-MacBook-Pro:viper standorsett$ cat creds.yaml
---
credentials:
  username: ringo
  password: passw0rd
Stans-MacBook-Pro:viper standorsett$
```
