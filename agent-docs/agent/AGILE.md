
## 🔄 工作流

將工作流程分為六大步驟：

- EXPLORE
- SPECIFY
- PLAN
    - ARCHITECTURE
    - TASKS
- BUILD
    - BUILD-TASK
    - BUILD-INTERACTIVE
- VERIFY

並且依照複雜度進行組合，只有在調用特定步驟時，才將需要該步驟的參考文檔進行讀取

- EXPLORE
    - 階段目的
        - 進行論點思考與第一性原理探討，先 ask Why 與確定必要性與開發成本利弊
    - 文件生成
        - `[module_folder]/agent-docs/*.spike.md`
    - MUST rules
        - EXPLORE 階段總是讀取
            - if 使用者的需求已經是明確的技術問題，then 總是讀取：
                - [check-requirements](agent-docs/agent/philosopher/check-requirements.md)
                - [linus-dev-philo](agent-docs/agent/engineer/linus-dev-philo.md)
- SPECIFY
    - 階段目的
        - 將模糊需求變為明確 spec
    - 文件生成
        - `[module_folder]/agent-docs/*.spec.md`
    - MUST rules
        - 請先根據任務背景，從「📚 重要文檔 」選擇需要的 context 進行參考
        - SPECIFY 階段總是讀取
            - [how-to-be-product-manager](agent-docs/agent/manager/how-to-be-product-manager.md)
- PLAN
    - PLAN-ARCHITECTURE
        - 階段目的
            - 考慮現有專案程式碼架構，根據功能進行系統架構設計
        - 文檔生成
            - `[module_folder]/agent-docs/*.arch.md`
        - MUST rules
            - PLAN-ARCH 階段總是讀取
                - [how-to-be-system-planner](agent-docs/agent/engineer/how-to-be-system-planner.md)
    - PLAN-TASK
        - 階段目的
            - 將工作拆解為具體任務，並考慮任務之間依賴關係
        - 文檔生成
            - `[module_folder]/agent-docs/*.task.md`
        - MUST rules
            - 若有 `*.arch.md`，請納入參考
            - PLAN-TASK 階段總是讀取
                - [how-to-be-task-manager](agent-docs/agent/manager/how-to-be-task-manager.md)

- BUILD
    - BUILD-TASK
        - 根據文件進行實作
        - MUST rules
            - 若有以下檔案，請納入參考
                - `[module_folder]/agent-docs/*.arch.md`
                - `[module_folder]/agent-docs/*.spec.md`
            - 若有 `[module_folder]/agent-docs/*.task.md`，先從第一個未完成項目詢問使用者，不要自行更動程式碼
            - BUILD-TASK 階段總是讀取
                - 開發核心哲學：[linus-dev-philo](agent-docs/agent/engineer/linus-dev-philo.md)
                - 實作風格指引：[dev-guide](agent-docs/agent/engineer/dev-guide.md)
                - 互動方式指引：[how-to-be-task-manager](agent-docs/agent/manager/how-to-be-task-manager.md)
      		- MUST 完成後請務必將 `[module_folder]/agent-docs/*.task.md` 完成項目進行 checkbox 打勾
    - BUILD-INTERACTIVE
        - 與使用者進行互動進行迭代開發與優化
        - BUILD-INTERACTIVE 階段總是讀取
            - 開發核心哲學：[linus-dev-philo](agent-docs/agent/engineer/linus-dev-philo.md)
            - 實作風格指引：[dev-guide](agent-docs/agent/engineer/dev-guide.md)
- VERIFY
    - MUST rules
        - VERIFY 階段總是讀取
            - [review-code](agent-docs/agent/validator/review-code.md)

### MUST rules

- 如果使用者沒有特別說明，自動評估使用者需求的複雜度來決定啟用哪些流程
    - 如果是明確的小需求： PLAN、BUILD、VERIFY
    - 如果是複雜大功能：建議完整走完流程
- 總是跟使用者說明你將會運行哪一個工作流步驟，並且總是詢問使用者才開始進行
- if edit 程式碼，then 總是進行 [review-code](agent-docs/agent/validator/review-code.md)

```
接下來，我將運行 PLAN-TASK 步驟，將工作拆解為具體任務，你說「ok go」 即可開始
```

### 後綴參考

- `*.spike.md`：EXPLORE 評估結論
- `*.spec.md`：SPECIFY 後的功能規格書
- `*.arch.md`：系統架構規格文件
- `*.task.md`：BUILD 詳細實作步驟
