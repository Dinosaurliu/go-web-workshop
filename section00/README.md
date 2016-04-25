<!--
Copygright 2016 Google Inc. All rights reserved.
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at
http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to writing, software distributed
under the License is distributed on a "AS IS" BASIS, WITHOUT WARRANTIES OR
CONDITIONS OF ANY KIND, either express or implied.

See the License for the specific language governing permissions and
limitations under the License.
-->

# 0: Hello world

Before we start writing web servers let's analyze a simple Go program.

```go
package main

import "fmt"

func   main() {
    fmt.Println(  "hello, world!"  );
    }
```

You should be able to understand every line of this program.
If you do not it's probably time to check out the [Go tour][1].

## Running your code

At this point you can paste the code above into a file named `main.go`.
This file should be anywhere in your `$GOPATH`.
I will assume it is inside of a folder with path `$GOPATH/hello/main.go`.

You can now run the code in a couple of ways. From the directory containing `main.go` run:

- `go run main.go` compiles and runs only `main.go`.

- `go build` compiles the code in the current directory and generates a binary named `hello` in the current directory.

- `go install` compiles the code in the current directory and generates a binary named `hello` in `$GOPATH/bin`.

## Formatting your code: gofmt

If you're used to seeing some Go code you might have noticed that this code is not formatted in a standard way.

Try running `gofmt main.go` and you'll see what the output should look like.
You can run `gofmt -d main.go` to see how the file differs from the formatted version.
And finally you can run `gofmt -w main.go` to simply rewrite the file with its formatted version.

## Managing import statements: goimports

The import statements at the beginning of the program are needed for the compiler to know what packages you use.
But this doesn't mean you need to write them yourself!

Try deleting the line `import "fmt"` from `main.go` and run it, you should see an error:

```
    $ go run main.go
    # command-line-arguments
    ./main.go:5: undefined: fmt in fmt.Println
```

You can fix this error by manually adding the missing import statements or using `goimports`.

If you don't have `goimports` installed in your machine you can easily install it by running:

```
    $ go get golang.org/x/tools/cmd/goimports
```

This will install the `goimports` binary in `$GOAPTH/bin`.
It is basically the equivalent to fetching the code from GitHub and then running `go install`.

You can now run `goimports` as a replacement of `gofmt`.
`goimports` formats your code *and* fixes your imported package list adding missing ones and removing those unused.

Similarly to `gofmt` you can run:

- `goimports main.go` to see what the fixed file would look like.
- `goimports -d main.go` to see the difference between the current and fixed versions.
- `goimports -w main.go` to rewrite the file with its fixed version.

## Making your life easier

`gofmt` and `goimports` are just two of the tools that you might use to make your life easier.
To have those and more invoked everytime you save your file you should consider adding a plugin to your favorite editor.
I personally love [vim][2] with [vim-go][3] and I'm also using [VS Code][4] with its Go plugin.
But there's many more editors with Go support, you can find them [here][5].

# Congratulations!

You're done with section ... zero. Well, we need to start somewhere!
But hey, at least now you're ready to tackle [section 1][6].

[1]: https://tour.golang.org
[2]: http://www.vim.org/
[3]: https://github.com/fatih/vim-go
[4]: https://www.visualstudio.com/en-us/products/code-vs.aspx
[5]: https://github.com/golang/go/wiki/IDEsAndTextEditorPlugins
[6]: ../section01/README.md
