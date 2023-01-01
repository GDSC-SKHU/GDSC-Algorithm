# 문제
## Easy
https://leetcode.com/problems/longest-common-prefix/

## Medium
https://leetcode.com/problems/integer-to-roman/

# 풀이
### Easy
- 주동석
```swift
class LongestCommonPrefix {
    func longestCommonPrefix(_ strs: [String]) -> String {
        // 맨 처음 기준이 되는 prefix 저장
        var prefix: String = ""
        var answer: String = ""
        
        let sortedStrs = strs.sorted { a, b in
            a.count < b.count
        }
        
        for i in 0..<sortedStrs[0].count {
            let index = sortedStrs[0].index(sortedStrs[0].startIndex, offsetBy: i)
            let temp = sortedStrs[0]
            prefix += temp[index].description
            for j in strs {
                let endIndex = j.index(after: index)
                if j[..<endIndex] != prefix {
                    return answer
                }
            }
            answer = prefix
        }
        return answer
    }
}
```

### Medium
- 주동석
```swift
class IntegerToRoman {
    var map: [String: String] = [
        "1": "I",
        "4": "IV",
        "5": "V",
        "9": "IX",
        "10": "X",
        "40": "XL",
        "50": "L",
        "90": "XC",
        "100": "C",
        "400": "CD",
        "500": "D",
        "900": "CM",
        "1000": "M"
    ]
    
    func intToRoman(_ num: Int) -> String {
        var answer = ""
        var num = num
        let sortedMap = map.sorted { i, j in
            Int(i.key)! > Int(j.key)!
        }
        
        var count = 0
        while(num > 0) {
            let i = sortedMap[count]
                
            // 만약에 num에서 뺄 수 있으면
            if num - Int(i.key)! >= 0 {
                answer += i.value
                num -= Int(i.key)!
                count -= 1
            }
            count += 1
        }
        return answer
    }
}
```
