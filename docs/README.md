# 다리 건너기 게임

## 기능 목록
- UI 기능
  - 입력 기능
    - 다리의 길이를 입력받는다.
    - 플레이어가 이동할 칸을 입력받는다. 'U'(위) 또는 'D'(아래)
    - 플레이어의 재시작 여부를 입력받는다. 'R'(재시작) 또는 'Q'(종료)
  - 출력 기능
    - 게임 시작 문구를 출력한다.
    - 다리의 길이 입력 요청 메시지를 출력한다.
    - 이동할 칸 입력 요청 메시지를 출력한다.
    - 플레이어의 재시작 여부 요청 메시지를 출력한다.
    - 게임 종료 문구를 출력한다.
    - 에러 문구를 출력한다.
- 핵심 기능
  - 다리 생성 기능
    - 입력 받은 다리의 길이로 생성한다.
    - 위 칸과 아래 칸 중 건널 수 잇는 칸은 0과 1 중 무작위 값을 이용해서 정한다.
    - 무작위 값이 0인 경우 아래 칸, 1인 경우 위 칸이 건널 수 있는 칸이 된다.
    - 위 칸을 건널 수 있는 경우 U, 아래 칸을 건널 수 있는 경우 D 값으로 나타낸다.
  - 다리 이동 기능
    - 플레이어가 입력한 이동한 칸이 건널 수 있다면 O로 표시한다. 건널 수 없다면 X로 표시한다.
  - 게임 재시작 기능
    - 생성된 다리를 재사용한다.
    - 게임 시도 횟수를 증가시킨다.

## 기능 요구 사항
위아래 둘 중 하나의 칸만 건널 수 있는 다리를 끝까지 건너가는 게임이다.
- 위아래 두 칸으로 이루어진 다리를 건너야 한다.
    - 다리는 왼쪽에서 오른쪽으로 건너야 한다.
    - 위아래 둘 중 하나의 칸만 건널 수 있다.
- 다리의 길이를 숫자로 입력받고 생성한다.
    - 다리를 생성할 때 위 칸과 아래 칸 중 건널 수 있는 칸은 0과 1 중 무작위 값을 이용해서 정한다.
    - 위 칸을 건널 수 있는 경우 U, 아래 칸을 건널 수 있는 경우 D값으로 나타낸다.
    - 무작위 값이 0인 경우 아래 칸, 1인 경우 위 칸이 건널 수 있는 칸이 된다.
- 다리가 생성되면 플레이어가 이동할 칸을 선택한다.
    - 이동할 때 위 칸은 대문자 U, 아래 칸은 대문자 D를 입력한다.
    - 이동한 칸을 건널 수 있다면 O로 표시한다. 건널 수 없다면 X로 표시한다.
- 다리를 끝까지 건너면 게임이 종료된다.
- 다리를 건너다 실패하면 게임을 재시작하거나 종료할 수 있다.
    - 재시작해도 처음에 만든 다리로 재사용한다.
    - 게임 결과의 총 시도한 횟수는 첫 시도를 포함해 게임을 종료할 때까지 시도한 횟수를 나타낸다.
- 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException`를 발생시키고, "[ERROR]"로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.
    - `Exception`이 아닌 `IllegalArgumentException`, `IllegalStateException` 등과 같은 명확한 유형을 처리한다.

### 입출력 요구 사항

#### 입력
- 자동으로 생성할 다리 길이를 입력 받는다. 3 이상 20 이하의 숫자를 입력할 수 있으며 올바른 값이 아니면 예외 처리한다.
```
3
```
- 라운드마다 플레이어가 이동할 칸을 입력 받는다. U(위 칸)와 D(아래 칸) 중 하나의 문자를 입력할 수 있으며 올바른 값이 아니면 예외 처리한다.
```
U
```
- 게임 재시작/종료 여부를 입력 받는다. R(재시작)과 Q(종료) 중 하나의 문자를 입력할 수 있으며 올바른 값이 아니면 예외 처리한다.
```
R
```

#### 출력
- 게임 시작 문구
- 게임 종료 문구
- 사용자가 이동할 때마다 다리 건너기 결과의 출력 형식은 실행 결과 예시를 참고한다.
    - 이동할 수 있는 칸을 선택한 경우 O 표시
    - 이동할 수 없는 칸을 선택한 경우 X 표시
    - 선택하지 않은 칸은 공백 한 칸으로 표시
    - 다리의 시작은 `[`, 다리의 끝은 `]`으로 표시
    - 다리 칸의 구분은 ` | `(앞뒤 공백 포함) 문자열로 구분
    - 현재까지 건넌 다리를 모두 출력
- 예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다.