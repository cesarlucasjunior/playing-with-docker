FROM golang:1.21 as builder
WORKDIR /usr/src/app
COPY ./hello.go .
RUN go build hello.go

FROM scratch
WORKDIR /
COPY --from=builder /usr/src/app .
CMD [ "./hello" ]