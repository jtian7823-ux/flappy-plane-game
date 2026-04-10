# PropellerAds 投放連結規格

> 版本：2026-04-10
> aid=3899879 / tid=154469

---

## 落地頁網址

```
https://jtian7823-ux.github.io/flappy-plane-game/
```

---

## 投放連結格式（必帶參數）

```
https://jtian7823-ux.github.io/flappy-plane-game/?utm_prid={SUBID}
```

### 參數說明

| 參數 | 必填 | 說明 |
|------|------|------|
| `utm_prid` | ✅ 必填 | PropellerAds 的 Subid macro，系統自動替換為真實訪客 ID |

### PropellerAds 後台填法

在 PropellerAds 廣告設定的 **Landing Page URL** 欄位填入：

```
https://jtian7823-ux.github.io/flappy-plane-game/?utm_prid={SUBID}
```

> `{SUBID}` 是 PropellerAds 的動態 macro，系統投放時會自動替換成真實 subid，不需要手動修改。

---

## 追蹤流程說明

```
用戶點擊廣告
    ↓
進入落地頁（URL 帶 utm_prid=xxxxx）
    ↓
GTM 自動讀取 utm_prid 存入 Cookie（prop_visitor_id）
    ↓
用戶完成註冊 → GTM 觸發 Registration tag → 回傳轉換
    ↓
用戶完成首存 → GTM 觸發 Deposit tag (goal=2) → 回傳轉換
```

---

## 測試方法

手動在網址後面加上測試用 subid：

```
https://jtian7823-ux.github.io/flappy-plane-game/?utm_prid=test123
```

進入頁面後：
1. 打開 DevTools → Application → Cookies
2. 確認 `prop_visitor_id=test123` 存在 ✅

---

## 注意事項

- `utm_prid` 參數**不能省略**，沒有這個參數就無法追蹤轉換
- Cookie 有效期 30 天，用戶在 30 天內完成轉換都會被記錄
- 同一個 subid 重複進入頁面不影響，Cookie 會更新為最新值
