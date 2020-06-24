# [[프로그래머스](https://programmers.co.kr/learn/courses/30/lessons/12948)]핸드폰 번호 가리기

- 문제 설명

  프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.
  전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 `*`으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.

- 제한 조건

  - s는 길이 4 이상, 20이하인 문자열입니다.

- 입출력 예

  | phone_number | return        |
  | ------------ | ------------- |
  | 01033334444  | `*******4444` |
  | 027778888    | `*****888`    |



## 풀이

- 내 풀이

  ```swift
  func solution(_ phone_number:String) -> String {
    return phone_number
      .enumerated()
      .reduce("", { $0 + ($1.offset > phone_number.count - 5 ? String($1.element): "*") })
  }
  ```

- 다른 풀이

  ```swift
  func solution(_ phone_number:String) -> String {
    guard phone_number.count > 4 else { return phone_number }
    return String(repeating: "*", count: phone_number.count - 4) + phone_number.suffix(4)
  }
  ```

  