
### Resource

```
https://www.golang-book.com/books/intro

https://www.amazon.com/Programming-Language-Addison-Wesley-Professional-Computing/dp/0134190440

https://gobyexample.com

https://tour.golang.org/welcome/1
```


###

### A Tour of Go

```
go get golang.org/x/tour/gotour

gotour
```

#### Loops and Functions

```{go}
package main

import (
    "fmt"
    "math"
)

func Sqrt(x float64) (z float64) {
    z = 1.0
    for i := 0; i < 10; i++ {
        z -= (z*z - x) / (2*z)
    }
    return
}

func main() {
    fmt.Println(Sqrt(2))
    fmt.Println(math.Sqrt(2))
}
```

#### Slices

```{go}
package main

import "golang.org/x/tour/pic"

func Pic(dx, dy int) [][]uint8 {
    y := make([][]uint8, dy)
    for i := 0; i < dy; i++ {
        y[i] = make([]uint8, dx)
        for j := 0; j < dx; j++ {
            y[i][j] = uint8(i^j)
        }
    }
    return y
}

func main() {
    pic.Show(Pic)
}
```

#### Maps

```{go}
package main

import (
    "strings"
    "golang.org/x/tour/wc"
)

func WordCount(s string) map[string]int {
    m := make(map[string]int)
    for _, v := range strings.Fields(s) {
        m[v]++
    }
    return m
}

func main() {
    wc.Test(WordCount)
}
```

#### Fibonacci closure

```{go}
package main

import "fmt"

// fibonacci is a function that returns
// a function that returns an int.
func fibonacci() func() int {
    a := 0
    b := 1
    return func() int {
        temp := a
        a = b
        b = temp + b
        return temp
    }
}

func main() {
    f := fibonacci()
    for i := 0; i < 10; i++ {
        fmt.Println(f())
    }
}
```

#### Stringers

```{go}
package main

import "fmt"

type IPAddr [4]byte

// TODO: Add a "String() string" method to IPAddr.
func (i IPAddr) String() string {
    return fmt.Sprintf("%v.%v.%v.%v", i[0], i[1], i[2], i[3])
}

func main() {
    hosts := map[string]IPAddr{
        "loopback":  {127, 0, 0, 1},
        "googleDNS": {8, 8, 8, 8},
    }
    for name, ip := range hosts {
        fmt.Printf("%v: %v\n", name, ip)
    }
}
```

#### Readers

```{go}
package main

import "golang.org/x/tour/reader"

type MyReader struct{}

// TODO: Add a Read([]byte) (int, error) method to MyReader.
func (m MyReader) Read(b []byte) (int, error) {
    for i, _ := range b{
        b[i] = 'A'
    }
    return len(b), nil
}

func main() {
    reader.Validate(MyReader{})
}
```

#### rot13Reader

```{go}
package main

import (
    "io"
    "os"
    "strings"
)

type rot13Reader struct {
    r io.Reader
}

func (rot *rot13Reader) Read(p []byte) (n int, err error) {
    n, err = rot.r.Read(p)
    for i := 0; i < len(p); i++ {
        if (p[i] <= 'M' && p[i] >= 'A') || (p[i] <= 'm' && p[i] >= 'a') {
            p[i] += 13
        } else if (p[i] <= 'Z' && p[i] >= 'N') || (p[i] <= 'z' && p[i] >= 'n') {
            p[i] -= 13
        }
    }
    return
}

func main() {
    s := strings.NewReader("Lbh penpxrq gur pbqr!")
    r := rot13Reader{s}
    io.Copy(os.Stdout, &r)
}
```

#### Images

```{go}
package main

import (
    "golang.org/x/tour/pic"
    "image"
    "image/color"
)

type Image struct{}

func (i Image) ColorModel() color.Model {
    return color.GrayModel
}

func (i Image) Bounds() image.Rectangle {
    return image.Rect(0, 0, 255, 255)
}

func (i Image) At(x, y int) color.Color {
    return color.Gray{uint8(x ^ y)}
}

func main() {
    m := Image{}
    pic.ShowImage(m)
}
```