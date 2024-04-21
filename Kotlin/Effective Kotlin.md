# 1장. 안정성(Safety)
코틀린은 **안정성**이 있는 언어입니다. 따라서 애플리케이션의 잠재적인 오류를 줄여줍니다.
코틀린이 제공하는 기능을 알아보고, 이를 올바르게 사용하는 방법 즉, **오류가 덜 발생하는 코드를 만드는 것** 을 알아봅니다.

## Item 1. 가변성을 제한하라
``` kotlin
class BankAccount {
  var balance = 0.0

  fun deposit(depositAmount: Double) {
    balance += depositAmount
  }

  @Throws(InsufficientFunds::class)
  fun withdraw(withdrawAmount: Double) {
    if(balance < withdrawAmount) {
      throw InsufficientFunds()
    }

    balance -= withdrawAmount
  }
}

class InsufficientFunds : Exception()
val account = BankAccount()
println(account.balance) // 0.0

```
