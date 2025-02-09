---
timezone: Asia/Taipei
---

# Nooma42

1. 自我介绍：大家好，我是 Nooma。之前一直沒有好好學習過協議層，希望能夠更瞭解以太坊的底層架構。
2. 你認為你會完成這次的殘酷學習嗎？Yes

<!-- Content_START -->
## Notes

### 2025.02.06

今天把 wiki 內容簡單看一下，之前有些基本了解的應該會先跳過，例如 BLS, ECDSA, SSZ, RLP serialization 等等。會著重看開發相關/JSONRPC/Transaction細節以及 consensus layer

#### 2025.02.09

JSON-RPC API 提供一個介面讓我們去跟節點互動，可以直接使用 curl 來去呼叫這個函數來獲取一些資訊，例如下面的範例

```bash
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_chainId","params":[],"id":1}' -H "Content-Type: application/json" https://eth1.lava.build

/// 得到
{"jsonrpc":"2.0","id":1,"result":"0x1"}% 
```

文件裡面有提到有不同的 namespace，之前沒注意過，像是上面使用的 `eth_chainId` 就是其中一個 namespace

每個節點提供的方法不同，有時候可以透過 rpc_methods 來查看所有的方法，但我常遇到不行的
```
curl -X POST \
  -H "Content-Type: application/json" \
  --data '{"jsonrpc":"2.0","method":"rpc_methods","params":[],"id":1}' \
 https://virginia.rpc.blxrbdn.com
{"jsonrpc":"2.0","id":1,"error":{"code":-32601,"message":"the method rpc_methods does not exist/is not available"}}
```

<!-- Content_END -->