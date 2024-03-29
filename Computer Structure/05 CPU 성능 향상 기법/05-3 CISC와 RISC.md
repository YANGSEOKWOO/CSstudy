
### 명령어 집합
> 모든 CPU가 똑같이 생긴 명령어를 실행하지 않는다.

CPU각 이해할 수 있는 명령어들의 모음 : **명령어 집합**, **명령어 집합구조** (Instruction Set Architecture)가 다를 수 있다.
=> CPU마다 ISA가 다를 수 있다는 것

ISA가 다르다 => CPU가 이해할 수 있는 명령어, 어셈블리어도 달라진다.
![[Pasted image 20240218144224.png]]
이렇듯, ISA가 다르면 컴파일내용 자체가 달라진다.
+컴파일러에 따라서도 어셈블리어가 달라질 수 있다.
- 제어장치가 명령어를 해석하는 방식
- 사용되는 레지스터의 종류와 개수
- 메모리 관리 방법
- CPU 하드웨어 설계
![[Pasted image 20240218144406.png]]


## CISC
Complex Instruction Set Computer
- 복잡한 명령어 집합을 활용하는 컴퓨터
ex) x86, x86-64

명령어의 형태와 크기가 다양한 **가변 길이 명령어** 사용
![[Pasted image 20240218144521.png]]

다양하고 강력한 명령어 => 상대적으로 적은 수의 명령어로도 프로그램 실행이 가능
=> 메모리를 아끼며 개발해야 했던 시절에 인기가 높았다.
=> 적은 수의 명령어 => 프로그램동작가능? => 메모리 공간 절약 가능

#### 단점
명령어가 다양하고 복잡 => 명령어의 크기, 실행시간이 일정하지 않다.
명령어 하나를 실행하는 데에 여러 클럭 주기를 필요로 한다.

![[Pasted image 20240218144709.png]]
이따구로 되버린다는 거임!
=> 파이프라인의 규격이 매우 떨어짐

그리고 기능은 많은데, 그 기능을 아주 어쩌다 사용하는거지 그렇게 자주 쓰지는 않는다는 거임, 20%정도의 명령어가 전체 명령어의 80%를 사용한다는 것!!!(충격)

#### 결론
 장점 : 너가 생각하는 거 ? 다있어, 나는 메모리 덜써
 단점 : 제가 생각하는건 그렇게 많지 않은데요;;, 파이프라이닝이 어렵다.

#### 한계
- 빠른 처리를 하려면 **파이프라인**을 써야한다. => '명령어 길이, 수행시간'이 규격화 되어야 한다.
- '자주 쓰이는 기본적인 명령어를 작고 빠르게 만들어야 한다.'
## RISC
Reduced Instruction Set Computer
위의 한계를 극복한 특징!!

#### 특)
1. CISC보다 명령어 종류 적음
2. 규격화되고 짧은 명령어 (되도록 1클럭 내외로 실행되는 명령어) : **고정길이 명령어**
3. 규격화 => 파이프라이닝에 최적화
4. 메모리에 직접접근하는 명령어 제한(2개!, load, store) => 메모리 접근 단순화, 최소화

메모리접근을 단순화, 최소화하면 그에 따른 단점이 있을텐데?
=> 레지스터를 적극적으로 활용한다는거여
그래서 범용레지스터도 많고 명령어가 많다!

그리고 메모리에 접근을 최소화한다? => 레지스터내에서 작동하기 때문에 더 빠르다.
![[Pasted image 20240218145346.png]]
