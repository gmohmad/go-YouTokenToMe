# go-YouTokenToMe

go-YouTokenToMe is a Go port of [YoutTokenToMe](https://github.com/VKCOM/YouTokenToMe) - a computationally efficient implementation of Byte Pair Encoding [[Sennrich et al.](https://www.aclweb.org/anthology/P16-1162/)]. Only inference is supported, no training.

## Usage example
```go
file, err := os.Open("data/yttm.model")
if err != nil {
    fmt.Println(err)
    return
}
defer file.Close()

r := io.Reader(file)

m, err := bpe.ReadModel(r)
if err != nil {
    panic(err)
}
config := bpe.NewConfig(false, false, false)
fmt.Println(m.EncodeSentence("мама мыла раму", *config))
```