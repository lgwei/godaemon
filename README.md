godaemon
========

Run golang app as background program, 以后台形式运行golang

## 安装：

```
go get github.com/icattlecoder/godaemon
```

## 示例:

```go
package main

import (
	_ "github.com/icattlecoder/godaemon"
	"log"
	"net/http"
)

func main() {
	mux := http.NewServeMux()
	mux.HandleFunc("/index", func(rw http.ResponseWriter, req *http.Request) {
		rw.Write([]byte("hello, golang!\n"))
	})
	log.Fatalln(http.ListenAndServe(":7070", mux))
}
```

## 运行

```
./example -d=true
~$ curl http://127.0.0.1:7070/index
hello, golang!
```
## 注
1. 这个fork支持参数以 "-d"的形式提供，等价于"-d=true"
