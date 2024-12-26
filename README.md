# Survey Decryptor API

## 簡介
Survey Decryptor API 是一個使用 Node.js 實現的伺服器端應用程式，旨在從外部服務（SurveyCake）中安全地解密調查資料。該程式碼可以在 AWS Lambda 或任何支持 Node.js 的伺服器上運行，並提供了一個簡單的介面來存取解密的調查資料。

## 功能
- 根據提供的哈希值和 SVID，從 SurveyCake 透過 Webhook 取得加密的資料。
- 使用對稱解密演算法（AES-128-CBC）對資料進行解密。
- 從配置文件中動態獲取密鑰和初始化向量（IV）。
- 返回解密後的調查資料作為 JSON 格式的響應。

## 安裝與使用方式
1. **克隆專案**
   ```bash
   git clone https://github.com/你的帳號/SurveyDecryptorAPI.git
   cd SurveyDecryptorAPI
   ```

2. **安裝依賴**
   確保已安裝 Node.js，然後運行以下命令安裝依賴模組：
   ```bash
   npm install
   ```

3. **配置**
   在專案根目錄下創建一個 `config.json` 文件，並根據需要填入 SurveyCake 的相關配置，包括 `hashKey` 和 `ivKey`。示例配置格式：
   ```json
   {
       "yourdomain.com": {
           "your_svid": {
               "hashKey": "your_hash_key",
               "ivKey": "your_iv_key"
           }
       }
   }
   ```

4. **運行應用**
   資源可以部署到支持 Node.js 的環境中，如 AWS Lambda。根據需要設置觸發器以供外部系統訪問該 API。

5. **API 調用**
   透過 HTTP GET 請求調用 API，示例請求方式：
   ```
   GET /?svid=your_svid&hash=your_hash&domain=yourdomain.com
   ```

## 必要的依賴模組清單
- `axios`: 用於發送 HTTP 請求。
- `crypto`: Node.js內建模組，處理加密和解密操作。
- `fs`: Node.js內建模組，用於文件系統操作。

## 授權條款
本專案採用 MIT 授權條款。詳細資訊請參閱 LICENSE 文件。