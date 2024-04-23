# OOP-practice1
# OOP
## Winform1
## 絕對值 客戶 
###  繼承 抽象 類別  建構函式 c#
### 介面  結構
```mermaid
classDiagram
Employee <|-- Contract :繼承
Employee <|-- Sales :繼承
Employee <|-- Fulltime :繼承
Contract <|-- Wai :繼承
class Employee {
<<Abstract>>
+string m_Name
}
class Contract {
+Employee
+int m_Hours
+int m_Rate
+GetPay()
}
class Wai {
+Contract
+GetPay()
+GetName()
}
class Sales {
+Employee
+int m_Bonus
+int m_Commi
+GetPay()
+Sales(int)
}
class Fulltime {
+Employee
+int m_Salary
+GetPay()
}
 ```

