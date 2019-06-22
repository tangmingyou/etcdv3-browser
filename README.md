# etcdv3-browser

A simple etcd (v3) web-based browser.

## Building and running

The application is designed to be run in Docker.

Assuming `etcd` is running at `etcd:2379` in `my_net`:

```
docker build . -t etcdv3-browser
docker run -d --name etcdv3-browser -p 8081:8081 --net my_net -e ETCD=etcd:2379 etcdv3-browser
```

Open http://localhost:8081

### Configuration

Environment variables:

| variable  | description     | default                   |
|-----------|-----------------|---------------------------|
| `HTTP_PORT` | listen port     | `8081`                  |
| `ETCD`      | etcd endpoint   | `etcd:2379`             |
| `CORS`      | allowed origins | `http://localhost:8080,http://localhost:8081` |

## Development environment

Initial setup: install Go, Node.js, `npm install -g yarn`

### Backend

```
cd backend
go build
./etcdv3-browser
```

### Frontend

```
cd frontend
yarn serve
```

### Running unit tests

```
go test ./...
npm run test:unit
```

### Lints and fixes files

```
npm run lint
```