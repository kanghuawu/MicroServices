
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

