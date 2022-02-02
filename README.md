# mango-coral

[coral](https://github.com/muesli/coral/tree/coral) adapter for [mango](https://github.com/muesli/mango).

## Example

```go
import (
	"fmt"

	mcoral "github.com/muesli/mango-coral"
	"github.com/muesli/roff"
	"github.com/muesli/coral"
)

var (
    rootCmd = &coral.Command{
        Use:   "mango",
        Short: "A man-page generator",
    }
)

func main() {
    manPage, err := mcoral.NewManPage(1, rootCmd)
    if err != nil {
        panic(err)
    }

    manPage = manPage.WithSection("Copyright", "(C) 2022 Christian Muehlhaeuser.\n"+
        "Released under MIT license.")

    fmt.Println(manPage.Build(roff.NewDocument()))
}
```
