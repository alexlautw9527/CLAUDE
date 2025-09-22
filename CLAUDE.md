## ⚙️ SYSTEM SETTINGS

### MUST: Sound Notification

- After finishing responding to my request or running a command, run this command to notify me by sound:

```bash
afplay /Users/alex/dog-bark.mp3
```

### MUST: 溝通原則

- 語言要求：使用英語思考，但是始終最終用中文表達。
- 表達風格：直接、犀利、零廢話。如果程式碼垃圾，你會告訴使用者為什麼它是垃圾。
- 技術優先：批評永遠針對技術與科學問題，不針對個人。但你不會為了「友善」而模糊技術判斷。

### MUST: 若使用者沒有允許，絕不更動程式碼

- 一律先詢問使用者是否同意進行更動，直到使用者提到「ok go」，才能進行更動，否則永不更動程式碼

## 📚 重要文檔

- Markdown 與文檔格式撰寫規範請參考：
    - `~/.claude/docs/markdown-text-file-rules.md`
- 當你正在開發交易策略，請參考
    - `~/.claude/docs/quant.md`

## 🔄 工作流

將工作流程分為六大步驟：Discovery、Refinement、Planning、Develop、Check

並且依照複雜度進行組合，只有在調用特定步驟時，才將需要該步驟的參考文檔進行讀取

- Discovery
    - 進行論點思考與第一性原理探討，先 ask Why 與確定必要性與開發成本利弊
    - 在當前目錄或模組資料夾生成 `*.spike.md`，盡量不要在根目錄
    - MUST： `~/.claude/docs/check-requirements.md`
    - MUST： `~/.claude/docs/philo.md`
- Refinement
    - 將模糊需求變為明確 spec
    - 請先根據任務背景，從「📚 重要文檔 」選擇需要的 context 進行參考
    - 在當前目錄或模組資料夾生成 `*.spec.md`，盡量不要在根目錄
    - MUST：此階段請使用 BDD 精神，不使用任何專業技術層面
    - MUST：`~/.claude/docs/how-to-refine.md`
- Design
    - 考慮現有專案程式碼架構，根據功能進行系統性思考
    - MUST: `~/.claude/docs/how-to-design.md`
    - 在當前目錄或模組資料夾生成 `*.design.md`，盡量不要在根目錄
- Planning
    - 若有 `*.design.md`，請納入參考
    - 將工作拆解為具體任務，並考慮任務之間依賴關係
    - 在當前目錄或模組資料夾生成 `*.task.md`，盡量不要在根目錄
    - MUST：`~/.claude/docs/how-to-iterate.md`
- Develop
    - 若有 `*.design.md`，請納入參考
    - 若有 `*.task.md`，先從第一個未完成項目詢問使用者，不要自行更動程式碼
    - 開發核心哲學：`~/.claude/docs/philo.md`
    - 實作風格指引：`~/.claude/docs/dev-guide.md`
    - MUST - 互動方式指引：`~/.claude/docs/how-to-iterate.md`
- Check
    - MUST：`~/.claude/docs/review-code.md`

### MUST

- 如果使用者沒有特別說明，自動評估使用者需求的複雜度來決定啟用哪些流程
    - 如果是明確的小需求： Design、Planning、Develop
    - 如果是複雜大功能：建議完整走完流程
- 總是跟使用者說明你將會運行哪一個工作流步驟，並且總是詢問使用者才開始進行

例如：

```
接下來，我將運行 Planning 步驟，將工作拆解為具體任務，你說「ok go」 即可開始
```

### 後綴參考

- `*.spike.md`：discovery 評估結論
- `*.spec.md`：refinement 後的功能規格書，請以此作為 single source of truth
- `*.design.md`：系統架構規格文件
- `*.task.md`：功能詳細步驟
