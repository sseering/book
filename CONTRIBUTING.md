# Contributing

If you want to contribute to nushell itself, see [nushell/nushell/CONTRIBUTING.md](https://github.com/nushell/nushell/blob/master/CONTRIBUTING.md) and the [contributor-book](https://github.com/nushell/contributor-book).

This book is based on Jekyll, which requires Ruby.

## Running locally with Docker

To avoid installing dependencies locally, run with Docker:
```
docker-compose up
```

Runing that command will first download the `jekyll/jekyll` Docker image. That will install dependencies, which can take a while. Once its done, open http://localhost:8080/

Changes in files will then show up after a reload and some delay (can be ~10 seconds).
