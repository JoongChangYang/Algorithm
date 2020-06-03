# 트리(Tree)

## 개념

- 트리(Tree)
  - Cycle이 없는 **연결그래프**
  - DAG(Directed Acyclic Graph), 방향성이 있는 비순환 그래프의 한 종류  
  - 트리는 하나의 루트 노드를 갖는다
  - 루트 노드는 0개 이상의 자식 노드를 갖고 있다.
  - 그 자식노드 또한 0개 이상의 자식노드를 갖고 있고, 이는 반복적으로 정의됨
  - 비선형 가료구조로 계층적 관계를 표현한다. (디렉터리 구조, 조직도 등)
  - 정점의 개수 V, 간선의 개수 V - 1
  - 트리의 성일뿐, 위를 만족한다고해서 트리는 아니다. **연결되어 있어야함**

## 용어

- 루트 노드(Root node): 부모가 없는 노드, 트리는 하나의 루트 노드만을 가진다.
- 단말 노드(Leaf node): 자식이 없는 노드 '말단 노드' 또는 '잎 노드' 라고도 부른다.
- 내부 노드(Internal node): 단말 노드가 아닌 노드
- 부모 노드(Parent node): 간선으로 연결되어있고 자기자신보다 레벨이 작은(위에 있는) 노드
- 자식 노드(Child node): : 간선으로 연결되어있고 자기자신보다 레벨이 큰(아래에 있는)노드
- 형제 노드(Sibling node): 같은 부모를 가지는 노드
- 선조 노드(Ancestor node): 특정 노드에서 루트 노드까지의 모든 부모 노드
- 후손 노드(Descendant node): 특정 노드의 아래에 있는 모든 노드
- 레벨(Level): 루트 노드부터의 거리 (시작을 0 또는 1로)
- 깊이(Depth): 루트에서 부터의 거리
- 높이(Height): 깊이의 최댓값
- 차수(Degree): 자식 노드의 개수
- 노드의 크기(Size): 자신을 포함한 모든 자손 노드의 개수



## 종류





## 트리의 순회

### 이진 탐색 트리

- 트리의 모든 노드를 방문하는 순서.

- 트리는 그래프이기 때문에 DFS, BFS 모두 가능

- DFS 순회 방법: 노드를 언제 처리할 것인지의 차이

  - 전위 순회(Pre-Order)

    - 부모의 값을 이용해서 자식의 값을 구해야 할 때 사용할 수 있다.

    - 현재 노드 -> 왼쪽가지 -> 오른쪽 가지

      ```swift
      func preOrder(_ node: Node?) {
        guard let node = node else { return }
        visit(node) // 자기 자신 처리
        preOrder(node.left) // 왼쪽 가지 프리오더
        preOrder(node.right) // 오른쪽 가지 프리오더
      }
      ```

      

  - 중위 순회(In-Order)

    - BST(Binary Search Tree)에서 삭제를 구현할 때 인오더 successor를 이용할때 사용할 수 있다.

    - 왼쪽가지 -> 현재 노드 -> 오른쪽 가지

      ```swift
      func inOrder(_ node: Node?) {
        guard let node = node else { return }
        in)rder(node.left) // 왼쪽 가지 인오더
        visit(node) // 자기자신 처리
        inOrder(node.right) // 오른쪽 가지 인오더
      }
      ```

  - 후위 순회(Post-Order)

    - Dynamic Programming, Segment Tree등 트리를 사용하는 대부분의 알고리즘에서 사용됨

    - 왼쪽가지 -> 오른쪽 가지 -> 현재 노드

      ```swift
      func postOrder(_ node: Node?) {
        guard let node = node else { return }
        postOrder(node.left) // 왼쪽 가지 포스트오더
        posetOrder(node.right) // 오른쪽 가지 포스트오더
        visit(node) // 자기자신 처리
      }
      ```

      

  