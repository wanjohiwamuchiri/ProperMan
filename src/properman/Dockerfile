FROM golang:1.21.0 as builder
WORKDIR /properman
RUN go mod init github.com/wanjohiwamuchiri/properman
COPY *.go ./
RUN CGO_ENABLED=0 GOOS=linux go build -o /hello-app

FROM gcr.io/distroless/base-debian11
WORKDIR /
COPY --from=builder /properman /properman
ENV PORT 8080
USER nonroot:nonroot
CMD ["/properman"]