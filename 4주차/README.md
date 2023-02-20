## 풀이
### 소수만들기
```swift
import Foundation

func solution(_ nums:[Int]) -> Int {
    var answer = 0
    
    var result = combination(nums: nums, length: 3)
    
    for i in result {
        let sum = i.reduce(0, +)
        if isPrime(num: sum) {
            answer += 1
        }
    }
    return answer
}

func combination(nums: [Int], length: Int) -> [[Int]] {
    var result: [[Int]] = []
    
    func combi(index: Int, cur: [Int]) {
        if cur.count == length {
            result.append(cur)
            return
        }
        for i in index..<nums.count {
            combi(index: i + 1, cur: cur + [nums[i]])
        }
    }
    
    combi(index: 0, cur: [])
    
    return result
}

func isPrime(num: Int) -> Bool {
    let rootNum = Int(sqrt(Double(num))) + 1
    
    if rootNum < 3 || num < 3 {
        return true
    }
    
    for i in 2..<rootNum {
        if num % i == 0 {
            return false
        }
    }
    
    return true
}
```

### 예산
```swift
import Foundation

func solution(_ d:[Int], _ budget:Int) -> Int {
    let sortedD = d.sorted(by: <)
    var currentBudget = budget
    var result = 0
    
    for i in sortedD {
        if currentBudget - i >= 0 {
            result += 1
            currentBudget -= i
        }
    }
    return result
}
```

### 점프와 순간이동
```swift
import Foundation

func solution(_ n:Int) -> Int 
{
    var answer = 0
    var target = n
    while (target > 0) {
        if target % 2 != 0 {
            answer += 1
        }
        target /= 2
    }

    return answer
}
```
