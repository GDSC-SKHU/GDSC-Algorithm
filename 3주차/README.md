## 문제

### 풀이
- Merge Two Binary Trees
```swift
import Foundation

public class TreeNode {
    public var val: Int
    public var left: TreeNode?
    public var right: TreeNode?
    public init() { self.val = 0; self.left = nil; self.right = nil; }
    public init(_ val: Int) { self.val = val; self.left = nil; self.right = nil; }
    public init(_ val: Int, _ left: TreeNode?, _ right: TreeNode?) {
        self.val = val
        self.left = left
        self.right = right
    }
}
class MergeTrees {
    func mergeTrees(_ root1: TreeNode?, _ root2: TreeNode?) -> TreeNode? {
        if root1 == nil && root2 == nil {
            return nil
        }
        let root = TreeNode((root1?.val ?? 0) + (root2?.val ?? 0))
       
        root.left = mergeTrees(root1?.left, root2?.left)
        root.right = mergeTrees(root1?.right, root2?.right)
        
        return root
    }
}
```

- All Paths From Source to Target
```swift
class AllPathsSourceTarget {
    func allPathsSourceTarget(_ graph: [[Int]]) -> [[Int]] {
        var result: [[Int]] = []
        func dfs(target: Int, path: [Int]) {
            if target + 1 == graph.count {
                result.append(path)
                return
            }
            var path = path
            
            for i in graph[target] {
                path.append(i)
                dfs(target: i, path: path)
                path.removeLast()
            }
        }
        
        dfs(target: 0, path: [0])
        return result
    }
}
```

- 타겟 넘버
```swift
class TargetNumber {
    var result = 0
    func targetNumber (_ numbers:[Int], _ target:Int) -> Int {
        dfs(arr: numbers, sum: 0, index: -1, target: target, path: "")
        return result
    }
    
    func dfs(arr: [Int], sum: Int, index: Int, target: Int, path: String) {
        if index == arr.count - 1 && target == sum{
            result += 1
            print(path)
            return
        }
        if index == arr.count - 1 {
            return
        }
        
        dfs(arr: arr, sum: sum + arr[index + 1], index: index + 1, target: target, path: path + " +" + String(arr[index + 1]))
        dfs(arr: arr, sum: sum - arr[index + 1], index: index + 1, target: target, path: path + " -" + String(arr[index + 1]))
    }
}
```
