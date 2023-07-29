# DNG - Digital Negative

A basic DNG codec reader for Golang.
It extracts and returns the JPEG thumbnail from the metadata.

## Usage

```go
package main

import (
	"image"
	"image/png"
	"os"

	_ "github.com/eberle1080/dng"
)

var (
	input  = "/tmp/IMG_0020.dng"
	output = "/tmp/IMG_0020.png"
)

func main() {
	fi, err := os.Open(input)
	check(err)
	defer fi.Close()

	m, _, err := image.Decode(fi)
	check(err)

	fo, err := os.Create(output)
	check(err)

	png.Encode(fo, m)
}

func check(err error) {
	if err != nil {
		panic(err)
	}
}
```

## License

**BSD-style**

## Contributing

1. Fork it
2. Create your feature branch (git checkout -b my-new-feature)
3. Commit your changes (git commit -am 'Add some feature')
5. Push to the branch (git push origin my-new-feature)
6. Create new Pull Request
