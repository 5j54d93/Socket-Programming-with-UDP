# Simple UDP

Using Python to write a simple UDP program that server side change a string into lower case and send back to client side.

## Socket programming with UDP

功能說明：在 Client 端傳送全大寫字串，從 Server 端回傳全小寫字串，並顯示在 Client 端的螢幕上。

以下說明連線、傳送、關閉流程：

### Client

```python
# 為 Server 創建一個 UDP 封包
clientSocket = socket(AF_INET,SOCK_DGRAM)

# 從使用者的鍵盤讀輸入
message = input('Input uppercase sentence:')

# 將 Server 的名字、port 加進封包，然後傳出去給 Server
clientSocket.sendto(str2Bytes,(serverName, serverPort))
```

### Server

```python
# 創建一個 UDP 封包
clientSocket = socket(AF_INET,SOCK_DGRAM)

# 將封包捆在 local port 12000
serverSocket.bind(('', serverPort))

# Server 印出「已經準備好接收」
print("The server is ready to receive")
```

以下重複接收與回傳：

#### Server

```python
# 讀進 UDP 封包，並獲得 Client 的 IP 和 port
message, clientAddress = serverSocket.recvfrom(2048)

# 將全大寫字串轉換成全小寫字串
modifiedMessage = message.lower()

# 回傳轉換好的字串給 Client
serverSocket.sendto(modifiedMessage, clientAddress)
```

#### Client

```python
# 從回傳封包讀字串
modifiedBytes, serverAddress = clientSocket.recvfrom(2048)

# 在螢幕上印出 Server 回傳的字串（全小寫）
print(modifiedMessage)

# 如果不再傳送了就關閉
clientSocket.close()
```

## License：MIT

This package is [MIT licensed](https://github.com/5j54d93/Simple-UDP/blob/main/LICENSE).
