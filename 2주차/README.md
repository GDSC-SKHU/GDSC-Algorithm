# 문제

## Medium

## 풀이
- minimum-add-to-make-parentheses-valid
```swift
import Foundation

class MinAddToMakeValid {
    func minAddToMakeValid(_ s: String) -> Int {
        let list = s.map { c in c.description }
        var result = 0
        var stack: [String] = []
        
        for i in list {
            if i == "(" {
                stack.append("(")
            }
            else {
                if stack.isEmpty {
                    result += 1
                }
                _ = stack.popLast()
            }
        }
        
        return result + stack.count
    }
}
```

- minimum-domino-rotations-for-equal-row
```swift
import Foundation

class MinDominoRotations {
    func minDominoRotations(_ tops: [Int], _ bottoms: [Int]) -> Int {
			var numCount: [Int: Int] = [:]
        for i in 0..<tops.count {
            if numCount[tops[i]] == nil {
                numCount[tops[i]] = 1
            }
            else {
                numCount[tops[i]]! += 1
            }
            if numCount[bottoms[i]] == nil {
                numCount[bottoms[i]] = 1
            }
            else {
                numCount[bottoms[i]]! += 1
            }
        }
        
        let filterData = numCount.filter { it in
            it.value >= tops.count
        }
        
        if filterData.isEmpty {
            return -1
        }
        
        let selectData = filterData.first!.key
        var result = 0

        for i in 0..<tops.count {
            if tops[i] != selectData && bottoms[i] != selectData {
                return -1
            }
        }
        
        result = tops.filter({ i in i == selectData }).count > bottoms.filter({ i in i == selectData }).count ? tops.filter({ i in i == selectData }).count : bottoms.filter({ i in i == selectData }).count
        
        return tops.count - result
    }
}
```

- integer-break
```swift
import Foundation

class IntegerBreak {
    func integerBreak(_ n: Int) -> Int {
        if n == 2 {
            return 1
        }
        if n == 3 {
            return 2
        }
        var powNum = n / 3
        var remain = n % 3
        
        if remain == 1{
            powNum -= 1
            remain = 4
        }
        
        return Int((pow(3, powNum) * pow(2, remain / 2)).description)!
    }
}
```
