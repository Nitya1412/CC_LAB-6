FROM ubuntu:22.04
RUN apt-get update && apt-get install -y g++ netcat-openbsd
WORKDIR /app
COPY app.cpp .
RUN g++ app.cpp -o app
EXPOSE 8080
CMD while true; do \
    echo -e "HTTP/1.1 200 OK\r\nContent-Type: text/plain\r\n\r\nServed by backend: $HOSTNAME" \
    | nc -l -p 8080 -q 1; \
done
