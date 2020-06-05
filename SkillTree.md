# [[프로그래머스]()] 스킬트리

- 문제 설명

  선행 스킬이란 어떤 스킬을 배우기 전에 먼저 배워야 하는 스킬을 뜻합니다.

  예를 들어 선행 스킬 순서가 `스파크 → 라이트닝 볼트 → 썬더`일때, 썬더를 배우려면 먼저 라이트닝 볼트를 배워야 하고, 라이트닝 볼트를 배우려면 먼저 스파크를 배워야 합니다.

  위 순서에 없는 다른 스킬(힐링 등)은 순서에 상관없이 배울 수 있습니다. 따라서 `스파크 → 힐링 → 라이트닝 볼트 → 썬더`와 같은 스킬트리는 가능하지만, `썬더 → 스파크`나 `라이트닝 볼트 → 스파크 → 힐링 → 썬더`와 같은 스킬트리는 불가능합니다.

  선행 스킬 순서 skill과 유저들이 만든 스킬트리[1](https://programmers.co.kr/learn/courses/30/lessons/49993#fn1)를 담은 배열 skill_trees가 매개변수로 주어질 때, 가능한 스킬트리 개수를 return 하는 solution 함수를 작성해주세요.

- 입출력 예

  | skill   | skill_trees                         | return |
  | ------- | ----------------------------------- | ------ |
  | `"CBD"` | `["BACDE", "CBADF", "AECB", "BDA"]` | 2      |

- 입출력 예 설명

  - "BACDE": B 스킬을 배우기 전에 C 스킬을 먼저 배워야 합니다. 불가능한 스킬트립니다.
  - "CBADF": 가능한 스킬트리입니다.
  - "AECB": 가능한 스킬트리입니다.
  - "BDA": B 스킬을 배우기 전에 C 스킬을 먼저 배워야 합니다. 불가능한 스킬트리입니다.



## 풀이

- 내 풀이

  ```swift
  func solution(_ skill:String, _ skill_trees:[String]) -> Int {
      
      var result = 0
      
      outer: for skillTree in skill_trees {
          
          var standard = skill
          var precedeSkill = standard.removeFirst()
          // 선행 되어야하는 스킬중 첫번째 스킬 삭제후 precedeSkill에 저장
          
          for currentSkill in skillTree {
              
              guard !standard.isEmpty else { break }
              // standard가 비어있으면 선행스킬들을 잘 찍은것이므로 더이상 반복문을 돌릴 필요가 없음
              
              if currentSkill == precedeSkill {
                  
                  precedeSkill = standard.removeFirst()
                  // 변수로 가지고있는 선행스킬과 일치하면 그 다음 선행스킬 삭제 후 precedeSkill에 저장
                  
              } else if standard.contains(currentSkill) {
                  
                  continue outer
                  // currentSkill이 standard에 가지고있는 문자라면 선행되어야하는 스킬보다 먼저 나온것이기때문에 실패한 스킬트리
                  
              }
              
          }
          
          result += 1
          // 반복문이 무사히 끝나면 성공한 스킬트리
          
      }
      
      return result
  }
  ```

  

