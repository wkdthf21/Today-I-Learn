# IntellliJ Debugging
---
## 조건으로 Break
---
- Break Point 우클릭
- [이미지] 장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_11-27-50.png

<br>



## 디버깅 버튼
---
- [이미지] 장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_14-36-11.png

### resume
- 다음 break point로 이동

<br>

### step over
- 현재 break 된 파일에서 다음 라인으로 이동

<br>

### step into
- 현재 break된 라인에서 실행하고 있는 라인으로 이동

- 예시
- [이미지] 장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_12-50-27.png
- [이미지] 장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_12-55-32.png

<br>

### force step into
- 다음 실행되는 라인으로 이동
- step into와 달리 Stepping을 무시하고 진행
- 예시

- [이미지] 장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_12-59-34.png

    - Settings > Stepping에서 Skip simple getters 체크

- [이미지] 장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_13-0-17.png
    - 이후 getter 함수 호출하는 라인에서 step into와 force step into 비교
    - force step into는 Stepping 설정과 무관하게 getter 메소드까지 이동한다

- 확인이 불필요한 getter / 생성자 등에 skip 옵션을 설정한 뒤, **skip하고 싶을 땐 step into, 전부 확인이 필요할 때는 force step into를 통해 디버깅하자**

<br>

### step out
- 해당 라인을 호출한 곳으로 이동
- 보통 step into로 파고 들어간 라인을 다시 빠져나오려고 할 때 사용함

<br>

### Drop frame
- call stack을 거슬러 올라감
- step out은 해당 라인을 실행한 후 돌아가는데, drop frame은 해당 라인을 실행하지 않고 돌아간다

<br>

### Run to Cursor
- 커서가 올라가 있는 라인으로 이동
- break point로 지정하지 않고 일회성으로 break 걸고 싶을 때 사용
장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_14-2-9.png

<br>

## Evaluate / Watch / Call Stack
---
### Evaluate
- break된 상태에서 코드를 실행
- 현재 라인에서 사용 가능한 코드만 사용할 수 있다 
- [이미지] 장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_14-22-28.png
- [이미지] 장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_14-21-39.png

<br>

### Watch
- 현재 라인에서 사용 가능한 코드만 사용할 수 있다
- [이미지] 장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_14-27-4.png

<br>

### Evaluate vs Watch
- 기능은 동일
- **Evaluate**는 코드를 계속 **수동 실행**
- **Watch**는 break 를 건 라인이 실행될 때마다 **자동 실행**
- 여러 개의 디버깅 코드를 동시에 볼 수 있다는 것과 반복적으로 코드를 작성할 필요가 없다는 점이 장점
값 변경하는 코드를 watch에 등록할 경우, 값이 변경되어서 다른 로직에 영향을 줄 수 있으므로 주의

<br>

### Call Stack
- 해당 break 라인에 오기까지의 call stack이 출력됨
- call stack에서 찾고자 하는 라인을 클릭하면 해당 라인으로 이동
- [이미지] 장예솔/yesol21.jang > [IntelliJ Community] Debugging > image2021-6-15_14-33-50.png








