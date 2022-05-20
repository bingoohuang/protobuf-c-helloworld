# Protobuf-c Hello World

[Original repo](https://github.com/ox/protobuf-c-hello-world)

This is the smallest useful demonstration of [protobuf-c](https://github.com/protobuf-c/protobuf-c)'s RPC capabilities. I made this project because the _only_ [example use of RPC](https://github.com/protobuf-c/protobuf-c/wiki/Examples) was incredibly convoluted (复杂难懂的) and managed to hide the core logic that was needed to actually _use_ the RPC capabilities. Hopefully this little example will manage to show off some of the incredible RPC capabilities that protobuf-c offers.

## Prereqs

1. For OS X users with [homebrew](http://mxcl.github.io/homebrew/), just run: `brew install protobuf-c`
1. `brew install autoconf automake libtool`
1. `git clone https://github.com/protobuf-c/protobuf-c-rpc`, `./autogen.sh && ./configure && make && make install`

## Building and Running

1. To build `make`
2. To run the server: `make run_server`
3. To run the client: `make run_client`

The server is a long-running process and will stay up until you kill it.

Make output:

```sh
$ make
protoc-c --c_out . ping.proto
gcc -c -g -pedantic -Wall -I/usr/local/include/protobuf-c-rpc -o server.o -c server.c
gcc -c -g -pedantic -Wall -I/usr/local/include/protobuf-c-rpc -o ping.pb-c.o -c ping.pb-c.c
gcc -o server server.o ping.pb-c.o -lprotobuf-c-rpc -lprotobuf-c
gcc -c -g -pedantic -Wall -I/usr/local/include/protobuf-c-rpc -o client.o -c client.c
gcc -o client client.o ping.pb-c.o -lprotobuf-c-rpc -lprotobuf-c
```

Server output:

```sh
$ make run_server
./server --port=8080
input->message: HELLO WORLD
input->message: HELLO WORLD
input->message: HELLO WORLD
```

Client output:

```sh
$ make run_client
./client --tcp=localhost:8080
Connecting... done.
sending ping... ping reply: hi
$ make run_client
./client --tcp=localhost:8080
Connecting... done.
sending ping... ping reply: hi
$ make run_client
./client --tcp=localhost:8080
Connecting... done.
sending ping... ping reply: hi
```

## License

fuck it
