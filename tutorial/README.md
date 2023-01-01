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
- 
