## `Project_rules.md`

### 🌱 專案風格總則

1. **以清晰為美，不為炫技而寫代碼。**
2. **優先考慮可讀性，其次是效能。**
3. **遵循 ASP.NET Core 官方最佳實踐與架構慣例。**

---

### 📁 專案架構規範

* 使用 **Clean Architecture**：

  * `Domain`: 業務核心與實體
  * `Application`: 用例與介面
  * `Infrastructure`: 實作細節，如 EF Core、第三方 API
  * `Web`: ASP.NET Core 專案本體（Controllers、ViewModels、Filters 等）

* 各層透過介面（Interface）解耦，禁止跨層直接相依。

---

### 🧩 命名規則

* **類別命名**：採 PascalCase，須具語意。

  * ✅ `UserService`, `OrderController`, `ILoginRepository`
* **方法命名**：採 PascalCase，使用動詞開頭，清楚描述行為。

  * ✅ `GetUserById`, `CalculateTotalPrice`
* **變數命名**：採 camelCase，避免過短或過長。

  * ✅ `userId`, `orderTotal`
* **介面命名**：以 `I` 為前綴。

  * ✅ `IUserRepository`, `ILogger`

---

### 🧼 程式風格

* **縮排**：使用 4 個空白格，禁止使用 Tab。
* **括號**：大括號獨立一行。

  ```csharp
  if (condition)
  {
      // do something
  }
  ```
* **Null 檢查優雅處理**：使用 C# 8+ 的 Null 合併運算子或 pattern matching。

  ```csharp
  var result = input ?? throw new ArgumentNullException(nameof(input));
  ```

---

### 📚 文件與註解

* 所有 **Public 方法與類別** 必須撰寫 XML Doc 註解。
* 禁用無意義註解，例如 `// TODO: Implement this later`（請寫下明確意圖）。

---

### 🔁 測試與 CI/CD

* 所有核心邏輯需有對應單元測試。
* 使用 xUnit 搭配 FluentAssertions。
* 將測試專案獨立於 `tests/` 資料夾。

---

### ⛔ 禁止事項

* 禁止在 Controller 中寫商業邏輯。
* 禁止靜態全域變數（除非經過評估與明確理由）。
* 禁止使用 `dynamic`，除非與 JSON/ExpandoObject 有關。

---

### 🧠 額外建議（選填）

* 可導入 [StyleCop Analyzers](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) 自動檢查風格。
* 建議使用 `.editorconfig` 維持 IDE 一致性。
* 推薦安裝 Resharper / Rider 或 Visual Studio + Roslyn 分析器。

---

這份規則是初稿，當然可依你的專案特性進行微調。

---

請問你是否需要：

1. 加入 **Git commit 規則（如 Conventional Commits）**？
2. 加入 **API 命名與 RESTful 準則**？
3. 加入 **CQRS/DDD 更細部的實作細節建議**？

或者，你希望我幫你產出 `.editorconfig`、StyleCop 設定檔，甚至是專案範本？
