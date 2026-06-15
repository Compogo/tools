# tools

Набор утилитарных функций для Go с поддержкой дженериков (generics).

## Установка

```bash
go get github.com/Compogo/tools
```

## Пакет pointer

```go
import "github.com/Compogo/tools/pointer"
```

- `func Pointer[T any](value T) *T` - возвращает указатель на значение
- `func PointerOrNil[T any](value T) *T` - возвращает указатель, если значение не нулевое
- `func PointerValue[T any](value *T) T` - безопасно возвращает значение из указателя

## Пакет rand

```go
import "github.com/Compogo/tools/rand"
```

- `var LetterRunes = []rune("abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ")`
- `func RandString(length uint32) string` - случайная строка из букв
- `func RandStringFromRunes(length uint32, runes ...rune) string` - случайная строка из заданных символов

## Пакет type_name

```go
import "github.com/Compogo/tools/type_name"
```

- `func TypeName[T any]() string` - возвращает полное имя типа

## Примеры

```go
package main

import (
    "fmt"
    "math/rand"
    "time"
    "github.com/Compogo/tools/pointer"
    "github.com/Compogo/tools/rand"
    "github.com/Compogo/tools/type_name"
)

func main() {
    // pointer
    p := pointer.Pointer(42)
    fmt.Println(pointer.PointerValue(p)) // 42
    
    // rand
    rand.Seed(time.Now().UnixNano())
    fmt.Println(rand.RandString(5)) // случайная строка
    
    // type_name
    fmt.Println(type_name.TypeName[int]()) // "int"
}
```

## Требования

- Go 1.26 или выше