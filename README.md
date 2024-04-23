# OOP-practice1
# OOP
## Winform1
## 絕對值 客戶 
###  繼承 抽象 類別  建構函式 c#
### 介面  結構
```mermaid
classDiagram
    Contract <-- Wai : 繼承
    Contract <-- Sales : 繼承
    Employee <|-- Sales : 繼承
    Employee <|-- Fulltime : 繼承
    class Contract {
        <<abstract>>
    }
    class Employee {
        <<abstract>>
    }
    class Fulltime {
        <<abstract>>
    }
    class Sales {
        -contractDuration : int
        -salesBonus() : decimal
    }
    class Wai {
        <<abstract>>
    }