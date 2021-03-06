[![Build Status](https://travis-ci.org/shahob/config.svg?branch=master)](https://travis-ci.org/shahob/config)
[![Go Report Card](https://goreportcard.com/badge/github.com/shahob/config)](https://goreportcard.com/report/github.com/shahob/config)
[![Maintainability](https://api.codeclimate.com/v1/badges/c2032986cc5a5ba53755/maintainability)](https://codeclimate.com/github/shahob/config/maintainability)

# Yet another JSON configuration file reader

Is a lightweight Golang package :beer:

## Installation

```bash
go get github.com/shahob/config
```

## Usage

JSON configuration file example

```json
{
  "database": {
    "host": "localhost",
    "port": 5432,
    "password": "password",
    "user": "user",
    "database": "database"
  }
}
```

Create `Config` struct type from JSON format

```golang
type Database struct {
	Host     string `json:"host"`
	Port     int    `json:"port"`
	Password string `json:"password"`
	User     string `json:"user"`
	Base     string `json:"database"`
}

type Config struct {
	Database `json:"database"`
}
```

```golang
import (
	"fmt"

	"github.com/shahob/config"
)

configuration := Config{}

// get configuration file
err := config.Load(*configPath, &configuration)

if err != nil {
	fmt.Println(err.Error())
}

fmt.Println(configuration.Database.Host)
```



## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE) file for details
