# 문제
## Easy
https://leetcode.com/problems/minimum-number-of-operations-to-convert-time/

https://leetcode.com/problems/largest-odd-number-in-string/

https://leetcode.com/problems/assign-cookies/

# 풀이
- minimum-number-of-operations-to-convert-time
```swift
class Solution {
    func convertTime(_ current: String, _ correct: String) -> Int {
        let currentTime = timeToNum(time: current)
        var correctTime = timeToNum(time: correct)
        
        var result = 0
        
        while(currentTime != correctTime) {
            if currentTime == correctTime {
                return result
            }
            else if currentTime + 60 <= correctTime {
                result += 1
                correctTime -= 60
            }
            else if currentTime + 15 <= correctTime {
                result += 1
                correctTime -= 15
            }
            else if currentTime + 5 <= correctTime {
                result += 1
                correctTime -= 5
            }
            else if currentTime + 1 <= correctTime {
                result += 1
                correctTime -= 1
            }
        }
        
        return result
    }
    
    func timeToNum(time: String) -> Int {
        let arr = time.split(separator: ":")
        return Int(arr[0])! * 60 + Int(arr[1])!
    }
}
```
- assign-cookies
```swift
class Solution {
    func findContentChildren(_ g: [Int], _ s: [Int]) -> Int {
        var sortedG = g.sorted()
        let sortedS = s.sorted()
        var result = 0
        
        for i in sortedS {
            if let j = sortedG.first {
                if i >= j {
                    result += 1
                    sortedG.remove(at: 0)
                }
            }
        }

        return result
    }
}
```

- largest-odd-number-in-string
```swift
class Solution {
    func largestOddNumber(_ num: String) -> String {
        var numArr = num.map { c in c.description }
        while (!numArr.isEmpty) {
            if Int(numArr.last!)! % 2 == 0 {
                _ = numArr.popLast()
            }
            else {
                return numArr.joined()
            }
        }
        return ""
    }
}
```
