```mermaid
classDiagram
  class Class 類別 {
    + Fields // 欄位
    + Constructors // 建構函式
    + Properties // 屬性
    + Methods // 方法
    + Events // 事件
  }

  class Interface 介面 {
    + Properties // 屬性
    + Methods // 方法
    + Events // 事件
  }

  Class 類別 <|-- Interface介面
  Class 類別 : supports inheritance // 支援繼承

  class Property 屬性 {
    + Accessors // 存取子
    + Logic and validation // 邏輯和驗證
  }

  class Delegate 委派{
    + Type-safe callable entity // 類型安全的可呼叫實體
    + Represents method signature // 表示方法簽名
    + Used for event-driven programming // 用於事件驅動程式設計
  }
  ```