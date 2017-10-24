
### Resource

```
An Introduction to Programming in Go
https://www.golang-book.com/books/intro

The Go Programming Language
https://www.amazon.com/Programming-Language-Addison-Wesley-Professional-Computing/dp/0134190440

Go by Example
https://gobyexample.com

A Tour of Go
https://tour.golang.org/welcome/1

How to Write Go Code
https://golang.org/doc/code.html

Effective Go
https://golang.org/doc/effective_go.html

Go Web Programming
http://proquest.safaribooksonline.com.libaccess.sjlibrary.org/book/programming/go/9781617292569
```


### Command

```
go get <package>

go run <file-one.go> <file-two.go>

go build

go install

go install vs go build
https://www.quora.com/What-is-the-difference-between-build-and-install-in-Go
https://pocketgophers.com/go-install-vs-go-build/
Go build just compile the executable file and move it to destination. 
Go install do a little more. It move the executable file to $GOPATH/bin and cache all non-main packages which imported to $GOPATH/pkg. the cache will be use in the next compile if it not changed yet. 
```


### GOPATH

```
VScode
https://github.com/Microsoft/vscode-go/wiki/GOPATH-in-the-VS-Code-Go-extension

.bash_profile
#GOPATH
export GOPATH=$HOME/go

#GOPATH bin
export PATH=$PATH:$GOPATH/bin
alias gohome='export GOPATH=$HOME/go;export PATH=$PATH:$GOPATH/bin'
# add gohere alias for changing folder
alias gohere='export GOPATH=$(pwd);export PATH=$PATH:$GOPATH/bin'
```

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

#### Equivalent Binary Trees

```{go}
package main

import (
    "fmt"
    "golang.org/x/tour/tree"
)

// Walk walks the tree t sending all values
// from the tree to the channel ch.
func Walk(t *tree.Tree, ch chan int) {
    defer close(ch)
    WalkHelper(t, ch)
}
func WalkHelper(t *tree.Tree, ch chan int) {
    if t == nil {
        return
    }
    
    WalkHelper(t.Left, ch)
    ch <- t.Value
    WalkHelper(t.Right, ch)
}

// Same determines whether the trees
// t1 and t2 contain the same values.
func Same(t1, t2 *tree.Tree) bool {
    
    ch1 := make(chan int)
    ch2 := make(chan int)
    go Walk(t1, ch1)
    go Walk(t2, ch2)
    
    for num1 := range ch1 {
        if num1 == <- ch2 {
            continue
        } else {
            return false
        }
    }
    _, ok := <- ch2
    return ok == false
}

func main() {
    fmt.Println(Same(tree.New(1), tree.New(1)))
    fmt.Println(Same(tree.New(1), tree.New(2)))
}
```

#### Web Crawler

```{go}
package main

import (
    "fmt"
    "sync"
    "time"
)

type Fetcher interface {
    // Fetch returns the body of URL and
    // a slice of URLs found on that page.
    Fetch(url string) (body string, urls []string, err error)
}

type SafeCounter struct {
    v   map[string]bool
    mux sync.Mutex
}

func (s *SafeCounter) findOrAdd(url string) bool {
    //s.mux.Lock()
    //defer s.mux.Unlock()
    if s.v[url] { 
        return true
    }
    s.v[url] = true
    return false
}

// Crawl uses fetcher to recursively crawl
// pages starting with url, to a maximum of depth.
func Crawl(url string, depth int, fetcher Fetcher, safe SafeCounter) {
    // TODO: Fetch URLs in parallel.
    // TODO: Don't fetch the same URL twice.
    // This implementation doesn't do either:
    if depth <= 0 {
        return
    }
    body, urls, err := fetcher.Fetch(url)
    if err != nil {
        fmt.Println(err)
        return
    }
    if safe.findOrAdd(url) {
        return
    }
    fmt.Printf("found: %s %q\n", url, body)
    for _, u := range urls {
        go Crawl(u, depth-1, fetcher, safe) 
    }
    return
}

func main() {
    safe := SafeCounter{v: make(map[string]bool)}
    Crawl("http://golang.org/", 4, fetcher, safe)
    time.Sleep(2 * time.Second)
}

// fakeFetcher is Fetcher that returns canned results.
type fakeFetcher map[string]*fakeResult

type fakeResult struct {
    body string
    urls []string
}

func (f fakeFetcher) Fetch(url string) (string, []string, error) {
    if res, ok := f[url]; ok {
        return res.body, res.urls, nil
    }
    return "", nil, fmt.Errorf("not found: %s", url)
}

// fetcher is a populated fakeFetcher.
var fetcher = fakeFetcher{
    "http://golang.org/": &fakeResult{
        "The Go Programming Language",
        []string{
            "http://golang.org/pkg/",
            "http://golang.org/cmd/",
        },
    },
    "http://golang.org/pkg/": &fakeResult{
        "Packages",
        []string{
            "http://golang.org/",
            "http://golang.org/cmd/",
            "http://golang.org/pkg/fmt/",
            "http://golang.org/pkg/os/",
        },
    },
    "http://golang.org/pkg/fmt/": &fakeResult{
        "Package fmt",
        []string{
            "http://golang.org/",
            "http://golang.org/pkg/",
        },
    },
    "http://golang.org/pkg/os/": &fakeResult{
        "Package os",
        []string{
            "http://golang.org/",
            "http://golang.org/pkg/",
        },
    },
}

```