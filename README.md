# 基礎駭客攻擊防禦
Same Origin Policy

- DOM 的同源政策
- ![image](https://user-images.githubusercontent.com/52542210/117407552-4c228d80-af41-11eb-8eba-dace488a6339.png)
- Cookie 的同源政策
- ![image](https://user-images.githubusercontent.com/52542210/117407580-55abf580-af41-11eb-9c31-b35473b89fb8.png)

HTTP Request

no-referrer(取消來源路徑參數)
避免傳遞敏感參數
用HTTP Header保護網站


X-Frame-Options [DENY:禁止嵌入這業網頁,SAMEORIGIN:同源允許許嵌入,ALLOW-FROM https://xxx.com/:白名單允許嵌入]
X-XSS-Protection [X-Xss-Protextion: 1; mode=block]
X-Context-Type-Options  [X-Context-Type-Option: nosniff] 避免瀏覽器探測檔案類型 可防止 MIME sniffing攻擊 

跨域存取設定

```
Access-Control-Allow-Origin：https://example.com
Access-Control-Allow-Credentials: true
Access-Control-Allow-Methods: GET
```

HTTPS Strict Transport Security

確保網站都在Https下進行操作
```
Strict-Transport-Security: max-age=31536000; includeSubDomains(包含子網域也要套用設定)
```
開啟HSTS讓瀏覽器強制跳轉HTTPS訪問

linux apach nginx設定
https://www.itread01.com/content/1545864130.html

保護Cookie的Header

HttpOnly:只能在伺服器端被存取 無法在客戶端被存取
避免cookie被修改
```
Set-Cookie: myCookie=parent; Path=/hello ; domain=game.com; HttpOnly
```
secure:cookie只有在https才能被傳輸
```
Set-Cookie: myCookie=secure; Path=/secure ; domain=game.com; secure
```

Content Security Policy

只有在下列規範允許的名單才能被載入到網頁上
```
Content-Security-Policy: <規範> <來源>;
Content-Security-Policy: <規範> <來源> <來源>;
```
對script來源進行規範
```
Content-Security-Policy: script-src http://*.example.com;
Content-Security-Policy: script-src http://*.example.com game.com;
```
最佳實踐

- 一定要設定 default-src 的規範
- 避免使用 'unsafe-inline'
- 避免使用 'unsafe-eval'
- 盡可能地清楚設定網域，例如不要只使用 *.com 
- 盡量少用通用字符 * 來設定來源
- 避免設定外部的來源，如果要設定，請確保有被技術人員審核過
- 盡量透過路徑 (Path) 來限制存取的資源，例如：game.com/scripts/
- 所有的來源都要使用 https

SQL Injection
- ![image](https://user-images.githubusercontent.com/52542210/117407637-68262f00-af41-11eb-9b29-6b976b322bb1.png)
- SQL 註解 -- 後面的語法都不執行
- ![image](https://user-images.githubusercontent.com/52542210/117408044-f6021a00-af41-11eb-8b61-31b99e03ce6d.png)

