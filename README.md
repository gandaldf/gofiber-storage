
<p align="center">
  <!-- <a href="https://gofiber.io">
    <img alt="Fiber" height="125" src="https://raw.githubusercontent.com/gofiber/docs/master/static/fiber_v2_logo.svg">
   </a>
  <br>   -->

  # 📦 Storage

</p>

Premade storage drivers that implement the [`Storage`](https://github.com/gofiber/storage/blob/main/storage.go) interface, designed to be used with various [Fiber middlewares](https://github.com/gofiber/fiber/tree/master/middleware).

```go
// Storage interface for communicating with different database/key-value
// providers. Visit https://github.com/gofiber/storage for more info.
type Storage interface {
	// Get gets the value for the given key.
	// `nil, nil` is returned when the key does not exist
	Get(key string) ([]byte, error)

	// Set stores the given value for the given key along
	// with an expiration value, 0 means no expiration.
	// Empty key or value will be ignored without an error.
	Set(key string, val []byte, exp time.Duration) error

	// Delete deletes the value for the given key.
	// It returns no error if the storage does not contain the key,
	Delete(key string) error

	// Reset resets the storage and delete all keys.
	Reset() error

	// Close closes the storage and will stop any running garbage
	// collectors and open connections.
	Close() error
}
```